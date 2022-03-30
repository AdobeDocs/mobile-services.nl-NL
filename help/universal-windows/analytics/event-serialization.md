---
description: Serienummering van gebeurtenissen wordt niet ondersteund door verwerkingsregels. In de mobiele SDK moet u een speciale syntaxis gebruiken binnen de parameter van de contextgegevens om gebeurtenissen met serienummering rechtstreeks in te stellen op de serveraanroep.
solution: Experience Cloud Services,Analytics
title: Gebeurtenisserialisatie
topic-fix: Developer and implementation
uuid: 7220a001-1174-4013-91ff-e8603d8ab265
exl-id: 9cb8d739-8b77-4fe7-8592-22e8cff172d4
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '70'
ht-degree: 8%

---

# Gebeurtenisserialisatie {#event-serialization}

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
