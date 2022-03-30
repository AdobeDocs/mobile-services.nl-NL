---
description: De productvariabele kan niet worden ingesteld door verwerkingsregels te gebruiken. In iOS 4.x SDK, moet u een speciale syntaxis in de parameter van contextgegevens gebruiken om producten op de servervraag direct te plaatsen.
solution: Experience Cloud Services,Analytics
title: Productvariabele
topic-fix: Developer and implementation
uuid: 6ece4d27-ef86-435c-a6f7-bd76be1c95ca
exl-id: c945add4-5358-44f6-b445-554b0df056c1
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 1%

---

# Variabele voor producten {#products-variable}

De productvariabele kan niet worden ingesteld door verwerkingsregels te gebruiken. In iOS 4.x SDK, moet u een speciale syntaxis in de parameter van contextgegevens gebruiken om producten op de servervraag direct te plaatsen.

Als u de *`products`* variabele, een sneltoets voor contextgegevens instellen op `"&&products"`en stel de waarde in met de syntaxis die is gedefinieerd voor de *`products`* variabele:

```objective-c
[contextData setObject:@"Category;Product;Quantity;Price[,Category;Product;Quantity;Price]" forKey:@"&&products"];
```

Bijvoorbeeld:

```objective-c
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
[contextData setObject:@";Running Shoes;1;69.95,;Running Socks;10;29.99" forKey:@"&&products"]; 
[contextData setObject:@"1234567890" forKey:@"m.purchaseid"]; 
[contextData setObject:@"1" forKey:@"m.purchase"]; 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"purchase" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"Order Confirmation" data:contextData]; 
```

*`products`* wordt rechtstreeks ingesteld op de afbeeldingsaanvraag en de andere variabelen worden ingesteld als contextgegevens. Alle variabelen van contextgegevens moeten door verwerkingsregels worden in kaart gebracht:

![](assets/map-products.png)

U hoeft de *`products`* variabele die verwerkingsregels gebruikt, omdat deze rechtstreeks is ingesteld op de afbeeldingsaanvraag van de SDK.
