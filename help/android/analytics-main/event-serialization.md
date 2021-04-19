---
description: Serienummering van gebeurtenissen wordt niet ondersteund door verwerkingsregels. In Mobiele SDK, moet u een speciale syntaxis in de parameter van contextgegevens gebruiken om geserialiseerde gebeurtenissen op de servervraag direct te plaatsen.
keywords: android;bibliotheek;mobile;sdk
seo-description: Serienummering van gebeurtenissen wordt niet ondersteund door verwerkingsregels. In Mobiele SDK, moet u een speciale syntaxis in de parameter van contextgegevens gebruiken om geserialiseerde gebeurtenissen op de servervraag direct te plaatsen.
seo-title: Serienummering van gebeurtenissen
solution: Experience Cloud,Analytics
title: Serienummering van gebeurtenissen
topic-fix: Developer and implementation
uuid: acdeda16-ab83-4cfc-907d-33448b801b31
exl-id: 03556912-fdcc-402e-b1de-233771f4e719
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 3%

---

# Gebeurtenisserialisatie {#event-serialization}

Serienummering van gebeurtenissen wordt niet ondersteund door verwerkingsregels. In Mobiele SDK, moet u een speciale syntaxis in de parameter van contextgegevens gebruiken om geserialiseerde gebeurtenissen op de servervraag direct te plaatsen.

```java
cdata.put("&&events", "event1:12341234");
```

Bijvoorbeeld:

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add events 
cdata.put("&&events", "event1:12341234"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("action", cdata); 
// trackState example: 
Analytics.trackState("State Name", cdata);
```
