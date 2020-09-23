---
description: Serienummering van gebeurtenissen wordt niet ondersteund door verwerkingsregels. In Mobiele SDK, moet u een speciale syntaxis in de parameter van contextgegevens gebruiken om geserialiseerde gebeurtenissen op de servervraag direct te plaatsen.
keywords: android;library;mobile;sdk
seo-description: Serienummering van gebeurtenissen wordt niet ondersteund door verwerkingsregels. In Mobiele SDK, moet u een speciale syntaxis in de parameter van contextgegevens gebruiken om geserialiseerde gebeurtenissen op de servervraag direct te plaatsen.
seo-title: Serienummering van gebeurtenissen
solution: Experience Cloud,Analytics
title: Serienummering van gebeurtenissen
topic: Developer and implementation
uuid: acdeda16-ab83-4cfc-907d-33448b801b31
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '104'
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

