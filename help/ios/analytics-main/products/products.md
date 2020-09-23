---
description: De productvariabele kan niet worden ingesteld door verwerkingsregels te gebruiken. In de iOS 4.x SDK moet u een speciale syntaxis in de parameter van contextgegevens gebruiken om producten rechtstreeks in te stellen op de serveraanroep.
seo-description: De productvariabele kan niet worden ingesteld door verwerkingsregels te gebruiken. In de iOS 4.x SDK moet u een speciale syntaxis in de parameter van contextgegevens gebruiken om producten rechtstreeks in te stellen op de serveraanroep.
seo-title: Productvariabele
solution: Experience Cloud,Analytics
title: Productvariabele
topic: Developer and implementation
uuid: 6ece4d27-ef86-435c-a6f7-bd76be1c95ca
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 1%

---


# Variabele voor producten {#products-variable}

De productvariabele kan niet worden ingesteld door verwerkingsregels te gebruiken. In de iOS 4.x SDK moet u een speciale syntaxis in de parameter van contextgegevens gebruiken om producten rechtstreeks in te stellen op de serveraanroep.

Als u de *`products`* variabele wilt instellen, stelt u een contextgegevenssleutel in op `"&&products"`en stelt u de waarde in met de syntaxis die voor de *`products`* variabele is gedefinieerd:

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

U hoeft de *`products`* variabele niet aan de hand van verwerkingsregels toe te wijzen, omdat deze rechtstreeks is ingesteld op de afbeeldingsaanvraag van de SDK.
