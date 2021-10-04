---
description: Met deze informatie kunt u lokaal opgeslagen Experience Cloud SDK-identiteiten ophalen van uw iOS-app en met aanvragen voor toegang tot GDPR-gegevens.
title: Opgeslagen id's ophalen
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
exl-id: ec8592af-fb08-4ab3-99a1-51ac5697a3d8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 2%

---

# Opgeslagen id&#39;s ophalen{#retrieving-stored-identifiers}

Met deze informatie kunt u lokaal opgeslagen Experience Cloud SDK-identiteiten ophalen van uw iOS-app en met aanvragen voor toegang tot GDPR-gegevens.

Voor meer informatie over GDPR, zie [GDPR en Uw Zaken](https://www.adobe.com/nl/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>De methode `getAllIdentifiersAsync` wint identiteiten terug die in Experience Cloud SDKs worden opgeslagen. U moet deze methode **before** de gebruiker uit opteert.

Experience Cloud SDK-identiteiten (zoals van toepassing) worden lokaal opgeslagen en geretourneerd in een JSON-tekenreeks, die het volgende kan bevatten:

* Bedrijfcontext - IMS-organisatie-id&#39;s
* Gebruikersnamen
* Experience Cloud iD (MID), voorheen bekend als Marketing Cloud-ID
* Integratiecodes (ADID, Push ID)
* Gegevensbron-id&#39;s (DPID, DPUUID)
* Analytische id&#39;s (AVID, AID, VID en bijbehorende RSID&#39;s)
* Verouderde doel-id&#39;s (TNTID, TNT3rdpartyID)
* Audience Manager-id (UUID)

Hier volgt een voorbeeld van de methode `ADBMobile getAllIdentifiersAsync` in iOS:

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```
