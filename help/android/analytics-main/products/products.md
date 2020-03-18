---
description: De productvariabele kan niet worden ingesteld door verwerkingsregels te gebruiken. In Mobiele SDK, moet u een speciale syntaxis in de parameter van contextgegevens gebruiken om producten op de servervraag te plaatsen.
keywords: android;library;mobile;sdk
seo-description: De productvariabele kan niet worden ingesteld door verwerkingsregels te gebruiken. In Mobiele SDK, moet u een speciale syntaxis in de parameter van contextgegevens gebruiken om producten op de servervraag te plaatsen.
seo-title: Variabele voor producten
solution: Marketing Cloud,Analytics
title: Variabele voor producten
topic: Developer and implementation
uuid: f4484022-cb8b-4dea-9209-5a110ba607df
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Variabele voor producten {#products-variable}

De productvariabele kan niet worden ingesteld door verwerkingsregels te gebruiken. In Mobiele SDK, moet u een speciale syntaxis in de parameter van contextgegevens gebruiken om producten op de servervraag te plaatsen.

Als u de variabele *products* wilt instellen, stelt u een contextgegevenssleutel in `"&&products"`en stelt u de waarde in met de syntaxis die voor de variabele *products* is gedefinieerd:

```java
cdata.put("&&products", "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]");
```

Bijvoorbeeld:

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata.put("&&products", ";Running Shoes;1;69.95,;Running Socks;10;29.99"); 
cdata.put("myapp.purchase", "1"); 
cdata.put("myapp.purchaseid", "1234567890"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("purchase", cdata); 
// trackState example: 
Analytics.trackState("Order Confirmation", cdata);
```

De variabele *products* wordt ingesteld op de afbeeldingsaanvraag en de andere variabelen worden ingesteld als contextgegevens. Alle variabelen van contextgegevens moeten door verwerkingsregels worden in kaart gebracht:

![](assets/map-products.png)

U hoeft de variabele *products* niet aan de hand van verwerkingsregels toe te wijzen, omdat deze variabele rechtstreeks is ingesteld op de afbeeldingsaanvraag van de SDK.
