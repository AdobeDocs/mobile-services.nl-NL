---
description: De productvariabele kan niet worden ingesteld met verwerkingsregels. In de mobiele SDK moet u een speciale syntaxis gebruiken binnen de parameter van de contextgegevens om producten rechtstreeks in te stellen op de serveraanroep.
solution: Experience Cloud,Analytics
title: Variabele voor producten
topic-fix: Developer and implementation
uuid: 2057a564-06ae-4171-bbe7-0baffa71608b
exl-id: b731e794-7134-4c6d-a41b-09ac9b84763d
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 1%

---

# Variabele voor producten{#products-variable}

De productvariabele kan niet worden ingesteld met verwerkingsregels. In de mobiele SDK moet u een speciale syntaxis gebruiken binnen de parameter van de contextgegevens om producten rechtstreeks in te stellen op de serveraanroep.

Als u de variabele *`products`* wilt instellen, stelt u een contextgegevenssleutel in op `"&&products"` en stelt u de waarde in met de syntaxis die is gedefinieerd voor *`products`*:

```js
cdata["&&products"] = "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]";
```

Bijvoorbeeld:

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&products"] = ";Running Shoes;1;69.95,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

*`products`* wordt rechtstreeks ingesteld op de afbeeldingsaanvraag en de andere variabelen worden ingesteld als contextgegevens. Alle variabelen van contextgegevens moeten worden toegewezen gebruikend verwerkingsregels:

![](assets/products-procrules.png)

U hoeft de *`products`*-variabele niet aan de hand van verwerkingsregels toe te wijzen, aangezien deze rechtstreeks is ingesteld op de afbeeldingsaanvraag van de SDK.
