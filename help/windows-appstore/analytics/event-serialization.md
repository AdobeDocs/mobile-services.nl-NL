---
description: Serienummering van gebeurtenissen wordt niet ondersteund door verwerkingsregels. In de mobiele SDK moet u een speciale syntaxis gebruiken binnen de parameter van de contextgegevens om gebeurtenissen met serienummering rechtstreeks in te stellen op de serveraanroep.
seo-description: Serienummering van gebeurtenissen wordt niet ondersteund door verwerkingsregels. In de mobiele SDK moet u een speciale syntaxis gebruiken binnen de parameter van de contextgegevens om gebeurtenissen met serienummering rechtstreeks in te stellen op de serveraanroep.
seo-title: Gebeurtenisserialisatie
solution: Experience Cloud,Analytics
title: Gebeurtenisserialisatie
topic: Developer and implementation
uuid: a5966d05-e218-446f-9f19-8664a84b74cd
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 7%

---


# Gebeurtenisserialisatie{#event-serialization}

Serienummering van gebeurtenissen wordt niet ondersteund door verwerkingsregels. In de mobiele SDK moet u een speciale syntaxis gebruiken in de parameter van de contextgegevens om gebeurtenissen met serienummering rechtstreeks in te stellen op de serveraanroep.

```js
cdata["&&events"] = "event1:12341234";
```

Bijvoorbeeld:

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add events 
cdata["&&events"] = "event1:12341234"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("action", cdata); 
// trackState example: 
ADB.Analytics.trackState("State Name", cdata);
```

