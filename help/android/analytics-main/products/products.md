---
description: De productvariabele kan niet worden ingesteld door verwerkingsregels te gebruiken. In Mobiele SDK, moet u een speciale syntaxis in de parameter van contextgegevens gebruiken om producten op de servervraag te plaatsen.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud,Analytics
title: Productvariabele
topic-fix: Developer and implementation
uuid: f4484022-cb8b-4dea-9209-5a110ba607df
exl-id: 1d850ce1-6fd4-463e-8949-8b8cf40d8467
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 1%

---

# Variabele voor producten {#products-variable}

De productvariabele kan niet worden ingesteld door verwerkingsregels te gebruiken. In Mobiele SDK, moet u een speciale syntaxis in de parameter van contextgegevens gebruiken om producten op de servervraag te plaatsen.

Als u de variabele *products* wilt instellen, stelt u een contextgegevenssleutel in op `"&&products"` en stelt u de waarde in met de syntaxis die is gedefinieerd voor de variabele *products*:

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

De *products* variabele wordt geplaatst op het beeldverzoek, en de andere variabelen worden geplaatst als contextgegevens. Alle variabelen van contextgegevens moeten door verwerkingsregels worden in kaart gebracht:

![](assets/map-products.png)

U hoeft de *products* variabele niet in kaart te brengen door verwerkingsregels te gebruiken omdat deze variabele rechtstreeks op de afbeeldingsaanvraag door de SDK wordt ingesteld.
