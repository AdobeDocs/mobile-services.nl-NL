---
description: Definitie en voorbeelden van broncode voor de functie Postbacks.
solution: Experience Cloud Services,Analytics
title: Voorbeeld van terugzending
topic-fix: Developer and implementation
uuid: 809c5646-7a80-40df-984b-0af89d854259
exl-id: 3ec5abf1-a406-48b6-91b1-fbcb0a9094ee
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---

# Voorbeeld van terugzending {#postback-example}

Definitie en voorbeelden van broncode voor de functie Postbacks.

>[!CAUTION]
>
>Dit voorbeeld wordt alleen ter informatie verstrekt. De `ADBMobileConfig.json` bestand moet worden geconfigureerd in de gebruikersinterface van Adobe Mobile en mag niet handmatig worden gewijzigd. Een manueel uitgegeven configuratiedossier kan gevaarlijk zijn wanneer u toegelaten verre berichtconfiguratie hebt.

## ADBMobileConfig.json-definitie {#section_0F6EC001AB6D488E815F50C7F5DA022E}

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

## Codevoorbeeld {#section_8169B88A2C634CB788DA574EE8C4B1DC}

```objective-c
NSDictionary *contextData = @{@"user.name":@"bob", @"user.zip":@"90210"}; 
[ADBMobile trackState:@"MainMenu" data:contextData];
```

Omdat de staat `"MainMenu"`, brengt deze het volgen vraag het bovengenoemde postbackbericht teweeg. De URL vervangt alle sjabloonvariabelen door waarden uit de hit. Ervan uitgaande dat de vorige sessie van de gebruiker 132 seconden lang was en dat de gebruiker iOS SDK versie 4.6.0 gebruikt, is dit een voorbeeld van de resulterende URL:

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-iOS&c27=cln,132`
