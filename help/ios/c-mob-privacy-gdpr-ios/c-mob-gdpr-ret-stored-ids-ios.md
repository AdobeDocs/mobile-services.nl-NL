---
description: Met deze informatie kunt u lokaal opgeslagen gegevens ophalen, de identiteit van de Experience Cloud SDK ophalen van uw iOS-app en met aanvragen voor toegang tot GDPR-gegevens.
seo-description: Met deze informatie kunt u lokaal opgeslagen gegevens ophalen, de identiteit van de Experience Cloud SDK ophalen van uw iOS-app en met aanvragen voor toegang tot GDPR-gegevens.
seo-title: Opgeslagen id's ophalen
title: Opgeslagen id's ophalen
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Opgeslagen id&#39;s ophalen{#retrieving-stored-identifiers}

Met deze informatie kunt u lokaal opgeslagen gegevens ophalen, de identiteit van de Experience Cloud SDK ophalen van uw iOS-app en met aanvragen voor toegang tot GDPR-gegevens.

Zie [GDPR en Uw bedrijf](https://www.adobe.com/privacy/general-data-protection-regulation.html)voor meer informatie over GDPR.

>[!IMPORTANT]
>
>De `getAllIdentifiersAsync` methode haalt identiteiten op die zijn opgeslagen in de Experience Cloud SDK&#39;s. U moet deze methode aanroepen **voordat** de gebruiker de functie uitschakelt.

Experience Cloud SDK-identiteiten (zoals van toepassing) worden lokaal opgeslagen en geretourneerd in een JSON-tekenreeks, die het volgende kan bevatten:

* Bedrijfcontext - IMS-organisatie-id&#39;s
* Gebruikersnamen
* Experience Cloud iD (MID), voorheen bekend als Marketing Cloud ID
* Integratiecodes (ADID, Push ID)
* Gegevensbron-id&#39;s (DPID, DPUUID)
* Analytische id&#39;s (AVID, AID, VID en bijbehorende RSID&#39;s)
* Verouderde doel-id&#39;s (TNTID, TNT3rdpartyID)
* Audience Manager-id (UUID)

Hier volgt een voorbeeld van de `ADBMobile getAllIdentifiersAsync` methode in iOS:

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```

