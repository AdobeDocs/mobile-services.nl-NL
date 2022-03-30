---
description: Hier is een voorbeeld van de productvariabele met Merchandising en product-specifieke gebeurtenissen.
solution: Experience Cloud Services,Analytics
title: Productvariabele met handelsstromen en productspecifieke gebeurtenissen
topic-fix: Developer and implementation
uuid: f913211e-97ad-4237-bfe4-7ded01295caf
exl-id: f438190d-0d2d-4bcd-a1c7-156e46e61162
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '76'
ht-degree: 0%

---

# Variabele voor producten met verkoopbare variabelen en productspecifieke gebeurtenissen {#products-variable-with-merchandising-evars-and-product-specific-events}

Hier is een voorbeeld van de productvariabele met Merchandising en product-specifieke gebeurtenissen.

```
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
[contextData setObject:@"event1" forKey:@"&&events"]; 
[contextData setObject:@";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99" forKey:@"&&products"]; 
[contextData setObject:@"1234567890" forKey:@"m.purchaseid"]; 
[contextData setObject:@"1" forKey:@"m.purchase"]; 
  
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"purchase" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"Order Confirmation" data:contextData];
```

>[!TIP]
>
>Als u een productspecifieke gebeurtenis activeert met de opdracht *`&&products`* variabele, moet u die gebeurtenis ook instellen in het dialoogvenster *`&&events`* variabele. Als u die gebeurtenis niet instelt, wordt deze tijdens de verwerking uitgefilterd.
