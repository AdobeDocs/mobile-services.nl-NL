---
description: De productvariabele kan niet worden ingesteld met verwerkingsregels. In de mobiele SDK moet u een speciale syntaxis gebruiken binnen de parameter van de contextgegevens om producten rechtstreeks in te stellen op de serveraanroep.
seo-description: De productvariabele kan niet worden ingesteld met verwerkingsregels. In de mobiele SDK moet u een speciale syntaxis gebruiken binnen de parameter van de contextgegevens om producten rechtstreeks in te stellen op de serveraanroep.
seo-title: Variabele voor producten
solution: Marketing Cloud,Analytics
title: Variabele voor producten
topic: Developer and implementation
uuid: 607983d6-48ac-4274-bfc8-b1ca4e5dad1b
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Variabele voor producten {#products-variable}

De productvariabele kan niet worden ingesteld met verwerkingsregels. In de mobiele SDK moet u een speciale syntaxis gebruiken binnen de parameter van de contextgegevens om producten rechtstreeks in te stellen op de serveraanroep.

Om de *`products`* variabele te plaatsen, plaats een sleutel van contextgegevens aan `"&&products"`, en plaats de waarde gebruikend de syntaxis die voor de *`products` variabele wordt bepaald:

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

De eigenschap *`products`* wordt rechtstreeks ingesteld op de afbeeldingsaanvraag en de andere variabelen worden ingesteld als contextgegevens. Alle variabelen van contextgegevens moeten worden toegewezen gebruikend verwerkingsregels:

![](assets/products-procrules.png)

U hoeft de *`products`* variabele niet aan de hand van verwerkingsregels toe te wijzen, omdat deze rechtstreeks is ingesteld op de afbeeldingsaanvraag van de SDK.

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
>Als u een productspecifieke gebeurtenis activeert met behulp van de *`&&products`* variabele, moet u die gebeurtenis ook in de *`&&events`* variabele instellen, anders wordt de gebeurtenis tijdens de verwerking uitgefilterd.

