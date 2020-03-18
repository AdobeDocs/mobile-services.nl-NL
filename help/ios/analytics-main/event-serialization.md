---
description: Serienummering van gebeurtenissen wordt niet ondersteund door verwerkingsregels. In Mobiele SDK, moet u een speciale syntaxis in de parameter van contextgegevens gebruiken om geserialiseerde gebeurtenissen op de servervraag direct te plaatsen.
seo-description: Serienummering van gebeurtenissen wordt niet ondersteund door verwerkingsregels. In Mobiele SDK, moet u een speciale syntaxis in de parameter van contextgegevens gebruiken om geserialiseerde gebeurtenissen op de servervraag direct te plaatsen.
seo-title: Serienummering van gebeurtenissen
solution: Marketing Cloud,Analytics
title: Serienummering van gebeurtenissen
topic: Developer and implementation
uuid: 19a27df4-0998-403d-800c-26ff61149208
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Serienummering voor gebeurtenissen {#event-serialization}

Serienummering van gebeurtenissen wordt niet ondersteund door verwerkingsregels. In Mobiele SDK, moet u een speciale syntaxis in de parameter van contextgegevens gebruiken om geserialiseerde gebeurtenissen op de servervraag direct te plaatsen.

```objective-c
[contextData setObject:@"eventN:serial number" forKey:@"&&events"];
```

Bijvoorbeeld:

```objective-c
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
 
// add events 
[contextData setObject:@"event1:12341234" forKey:@"&&events"]; 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"action" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"State Name" data:contextData]; 
```

