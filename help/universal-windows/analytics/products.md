---
description: De productvariabele kan niet worden ingesteld met verwerkingsregels. In de mobiele SDK moet u een speciale syntaxis gebruiken binnen de parameter van de contextgegevens om producten rechtstreeks in te stellen op de serveraanroep.
solution: Experience Cloud Services,Analytics
title: Variabele voor producten
topic-fix: Developer and implementation
uuid: 607983d6-48ac-4274-bfc8-b1ca4e5dad1b
exl-id: 0575236c-9858-4bf9-a2ce-6e2667d58ddd
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 1%

---

# Variabele voor producten {#products-variable}

De productvariabele kan niet worden ingesteld met verwerkingsregels. In de mobiele SDK moet u een speciale syntaxis gebruiken binnen de parameter van de contextgegevens om producten rechtstreeks in te stellen op de serveraanroep.

Als u de *`products`* variabele, een sneltoets voor contextgegevens instellen op `"&&products"`en stel de waarde in met de syntaxis die voor de * is gedefinieerd`products` variabele:

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

De *`products`* wordt rechtstreeks ingesteld op de afbeeldingsaanvraag en de andere variabelen worden ingesteld als contextgegevens. Alle variabelen van contextgegevens moeten worden toegewezen gebruikend verwerkingsregels:

![](assets/products-procrules.png)

U hoeft de *`products`* variabele die verwerkingsregels gebruikt, omdat deze rechtstreeks is ingesteld op de afbeeldingsaanvraag van de SDK.

## Variabele voor producten met verkoopbare variabelen en productspecifieke gebeurtenissen {#section_685D53AD3D064F9A8E225F995A9BA545}

Een voorbeeld van de *`products`* variabele met Merchandising Vars en productspecifieke gebeurtenissen.

```
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&events"] = "event1 "; 
cdata["&&products"] = ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
  
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>Als u een productspecifieke gebeurtenis activeert met de *`&&products`* variabele, moet u die gebeurtenis ook instellen in het dialoogvenster *`&&events`* anders wordt de gebeurtenis tijdens de verwerking uitgefilterd.
