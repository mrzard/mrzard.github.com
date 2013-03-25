---
layout: post
title: "MySQL Query to Export Prestashop Data to a Shopify CSV"
date: 2013/02/13 09:19:00 -0800
comments: true
external-url:
categories: [MySQL, Prestashop, Programming, PHP, Shopify]
---


If you find yourself migrating your shop from Prestashop to Shopify, you can 
use this query. It was written for an old version of Prestashop, but you probably 
won't have much trouble adapting it to newer versions.

Also, take in consideration this query only outputs basic data, no variants, 
colors, etc. Also check which values do you need for 'variant requires shipping', 
ID_LANG, etc.

  

	SELECT pl.link_rewrite as `Handle`, pl.name as `Title`, 
	pl.description as `Body (HTML)`, 'VENDORNAME' as `Vendor`, pcl.`name` as `Type`, 
	t.`name` as Tags, '' as `Option1 Name`, '' as `Option1 Value`, '' as `Option2 Name`, 
	'' as `Option2 Value`, '' as `Option3 Name`, '' as `Option3 Value`, '' as `Variant SKU`, 
	p.weight * 1000 as `Variant Grams`, '' as `Variant Inventory Tracker`, p.`quantity` 
	as `Variant Inventory Qty`, 'deny' as `Variant Inventory Policy`, 'manual' 
	as `Variant Fulfillment Service`, p.price as `Variant Price`, p.price_before 
	as `Variant Compare At Price`, 'true' as `Variant Requires Shipping`, 'true' 
	as `Variant Taxable`, '' as `Image Src` 
	FROM 
		`ps_product` p 
		INNER JOIN `ps_product_lang` pl ON pl.`id_product` = p.`id_product` 
		LEFT JOIN `ps_product_tag` pt ON pt.`id_product` = p.`id_product` 
		LEFT JOIN `ps_tag` t ON t.`id_tag` = pt.`id_tag` 
		INNER JOIN `ps_image` pi ON pi.`id_product` = p.`id_product` 
		INNER JOIN `ps_category_lang` pcl ON pcl.`id_category` = p.`id_category_default` 
	WHERE 
		pl.`id_lang` = ID_LANG 
		AND pcl.`id_lang` = ID_LANG 
		AND p.`id_category_default` IN (
			SELECT `id_category` 
			FROM `ps_category` WHERE `active` = 1
		) 
		AND p.`active` = 1 GROUP BY p.`id_product`; 
	



