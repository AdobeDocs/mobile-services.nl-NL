---
description: Een voorbeeld van de productvariabele met Merchandising Vars en productspecifieke gebeurtenissen.
seo-description: Een voorbeeld van de productvariabele met Merchandising Vars en productspecifieke gebeurtenissen.
seo-title: Productvariabele met handelsstromen en productspecifieke gebeurtenissen
solution: Experience Cloud,Analytics
title: Productvariabele met handelsstromen en productspecifieke gebeurtenissen
topic-fix: Developer and implementation
uuid: 94e882e4-b19d-4c48-9dfb-331465490347
exl-id: 3a90f624-da13-4c26-9e4c-3a4af33bc5ee
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# Variabele voor producten met verkoopbare variabelen en productspecifieke gebeurtenissen{#products-variable-with-merchandising-evars-and-product-specific-events}

Een voorbeeld van de productvariabele met Merchandising Vars en productspecifieke gebeurtenissen.

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
>Als u een product-specifieke gebeurtenis gebruikend de *`&&products`* variabele teweegbrengt, moet u die gebeurtenis in *`&&events`* variabele ook plaatsen, anders wordt de gebeurtenis gefilterd uit tijdens verwerking.
