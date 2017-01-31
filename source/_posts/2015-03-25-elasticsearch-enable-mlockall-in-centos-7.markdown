---
layout: post
title: "ElasticSearch: Enable Mlockall in CentOS 7"
date: 2015-03-25 10:52
comments: true
categories: ["CentOS 7", Elastic, ElasticSearch, linux, mlockall, systems]
---

I have recently been wrestling with ElasticSearch/Elastic and how to finally enable mlockall under CentOS 7\. You usually will get the “Unable to lock JVM memory (ENOMEM). This can result in part of the JVM being swapped out. Increase RLIMIT_MEMLOCK (ulimit)`.”

These are all the places I made changes to get it to work. Now, I don’t know if some of these steps are skippable (my guess is some of them are), but I got it working i nthe end, and my nodes are now happily showing `mlockall: true“

*   Make sure `bootstrap.mlockall: true` is uncommented in `/etc/elasticsearch/elasticsearch.yml` or the appropiate config file for your configuration.

*   Edit `/etc/security/limits.conf` and add these lines (or edit them if applicable). You usually will want to add them at the very end of the file.
```
    elasticsearch - nofile 65535
    elasticsearch - memlock unlimited
    root - memlock unlimited

```

*   Edit `/etc/sysconfig/elasticsearch`. You will find these values commented, and possibly without values. Change them to these:

```
    # ES_HEAP_SIZE; 30g for my nodes - look up a good value for yours
    ES_HEAP_SIZE=30g

    MAX_OPEN_FILES=65535
    MAX_LOCKED_MEMORY=unlimited
    ...
    # WORK_DIR: Make sure /tmp is not mounted as
    # noexec OR put a regular directory here
    WORK_DIR=/tmp/elasticsearch
```

*   Edit `/usr/lib/systemd/system/elasticsearch.service` and make sure `LimitMEMLOCK` is uncommented and set to infinity


``
    # See MAX_LOCKED_MEMORY in sysconfig, use "infinity"
    # when MAX_LOCKED_MEMORY=unlimited
    # and using bootstrap.mlockall: true
    LimitMEMLOCK=infinity
``

*   Edit `/etc/init.d/elasticsearch` and add `su $ES_USER --shell /bin/bash -c "ulimit -l unlimited"` before the actual start of ES, this is more or less how it looks in mine:

```
    echo -n $"Starting $prog: "
    # if not running, start it up here, usually something like "daemon $exec"
    su $ES_USER --shell /bin/bash -c "ulimit -l unlimited"
    daemon --user $ES_USER --pidfile $pidfile $exec -p $pidfile -d -Des.default.path.home=$ES_HOME -Des.default.path.logs=$LOG_DIR -Des.default.path.data=$DATA_DIR -Des.default.path.work=$WORK_DIR -Des.default.path.conf=$CONF_DIR
```

After I had everything in place, I restared my nodes and now they all show `mlockall: true` when checked with `curl http://localhost:9200/_nodes/process?pretty`

Hope this helps someone!
