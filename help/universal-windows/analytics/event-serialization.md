---
description: Serienummering van gebeurtenissen wordt niet ondersteund door verwerkingsregels. In de mobiele SDK moet u een speciale syntaxis gebruiken binnen de parameter van de contextgegevens om gebeurtenissen met serienummering rechtstreeks in te stellen op de serveraanroep.
seo-description: Serienummering van gebeurtenissen wordt niet ondersteund door verwerkingsregels. In de mobiele SDK moet u een speciale syntaxis gebruiken binnen de parameter van de contextgegevens om gebeurtenissen met serienummering rechtstreeks in te stellen op de serveraanroep.
seo-title: Serienummering voor gebeurtenissen
solution: Marketing Cloud,Analytics
title: Serienummering voor gebeurtenissen
topic: Developer and implementation
uuid: 7220a001-1174-4013-91ff-e8603d8ab265
translation-type: tm+mt
source-git-commit: f5ba33fe805c502b8ae91ddafcaa0b57e68704b8

---


# Serienummering voor gebeurtenissen {#event-serialization}

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

