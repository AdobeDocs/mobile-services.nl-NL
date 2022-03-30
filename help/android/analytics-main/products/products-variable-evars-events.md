---
description: Hier is een voorbeeld van de productvariabele met Merchandising en product-specifieke gebeurtenissen.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Productvariabele met handelsstromen en productspecifieke gebeurtenissen
topic-fix: Developer and implementation
uuid: 64f822a0-6ccf-48e7-8886-31b93d8198a3
exl-id: 2ede6341-3068-4423-a509-c0ec3a2db5e8
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 0%

---

# Variabele voor producten met verkoopbare variabelen en productspecifieke gebeurtenissen {#products-variable-with-merchandising-evars-and-product-specific-events}

Hier is een voorbeeld van de productvariabele met Merchandising en product-specifieke gebeurtenissen.

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata.put("&&events", "event1"); 
cdata.put("&&products", ";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99"); 
cdata.put("myapp.purchase", "1"); 
cdata.put("myapp.purchaseid", "1234567890"); 
  
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("purchase", cdata); 
// trackState example: 
Analytics.trackState("Order Confirmation", cdata);
```

>[!TIP]
>
>Als u een productspecifieke gebeurtenis activeert met de opdracht *`&&products`* variabele, moet u die gebeurtenis ook instellen in het dialoogvenster *`&&events`* variabele. Als u die gebeurtenis niet instelt, wordt deze tijdens de verwerking uitgefilterd.
