---
description: U kunt deze informatie gebruiken om u te helpen postbacks zijn en hoe zij werken.
keywords: android;library;mobile;sdk
seo-description: U kunt deze informatie gebruiken om u te helpen postbacks zijn en hoe zij werken.
seo-title: Voorbeeld postbacks
solution: Marketing Cloud,Analytics
title: Voorbeeld postbacks
topic: Developer and implementation
uuid: 8010cd00-d42b-4e16-8403-692fab2550f1
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Postbacks, voorbeeld {#postbacks-example}

U kunt deze informatie gebruiken om u te helpen begrijpen wat postbacks zijn en hoe zij werken.

>[!CAUTION]
>
>Dit voorbeeld wordt alleen ter informatie verstrekt. Het `ADBMobileConfig.json` bestand moet worden geconfigureerd in de gebruikersinterface van Adobe Mobile en mag niet handmatig worden gewijzigd. Een manueel uitgegeven configuratiedossier kan gevaarlijk zijn wanneer u toegelaten verre berichtconfiguratie hebt.

## `ADBMobileConfig.json` definitie {#section_8751E8176F3546C09420341A39758AFF}

```js
"messages": [ 
    { 
        "messageId": "79ae37c9-89b9-465e-af7f-d3351771f1dc", 
        "template": "callback", 
        "payload": {  
            "templateurl": "https://my.server.com/?user={user.name}&zip={user.zip}&c16={%sdkver%}&c27=cln,{a.PrevSessionLength}", 
            "templatebody": "c2RrdmVyPXslc2RrdmVyJX0mY2I9eyVjYWNoZWJ1c3QlfSZjbGllbnRJZD17bi5jbGllbnQuaWR9JnRzPXsldGltZXN0YW1wVSV9JnRzej17JXRpbWVzdGFtcFolfQ==", 
            "contenttype": "application/x-www-form-urlencoded",  
            "timeout": 4 
        }, 
        "showOffline": true, 
        "showRule": "always", 
        "endDate": 2524730400, 
        "startDate": 0, 
        "audiences": [], 
        "triggers": [ 
            { 
                "key": "pageName", 
                "matches": "eq", 
                "values": [ 
                    "MainMenu" 
                ] 
            } 
        ] 
    } 
] 
```

## Codevoorbeeld {#section_D063DE82976D4EDEA97E804BD1C4718F}

```js
HashMap<String, Object> contextData = new HashMap<String, Object>(); 
contextData.put("user.name", "bob"); 
contextData.put("user.zip", "90210"); 
Analytics.trackState("MainMenu", contextData);
```

Omdat zijn staat is, brengt deze het volgen vraag het bovengenoemde postbackbericht teweeg. `“MainMenu”` De URL vervangt alle sjabloonvariabelen door waarden uit de hit. Ervan uitgaande dat de vorige sessie van de gebruiker 132 seconden lang was en dat die gebruiker versie 4.6.0 van de Android-SDK heeft, ziet de resulterende URL er als volgt uit:

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-AN&c27=cln,132`
