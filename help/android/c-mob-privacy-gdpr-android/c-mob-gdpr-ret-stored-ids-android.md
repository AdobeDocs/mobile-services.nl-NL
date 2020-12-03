---
description: Met deze informatie kunt u lokaal opgeslagen SDK-identiteiten ophalen uit uw Android-app en met aanvragen voor toegang tot GDPR-gegevens.
seo-description: Met deze informatie kunt u lokaal opgeslagen SDK-identiteiten ophalen uit uw Android-app en met aanvragen voor toegang tot GDPR-gegevens.
seo-title: Opgeslagen id's ophalen
title: Opgeslagen id's ophalen
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---


# Opgeslagen id&#39;s ophalen{#retrieving-stored-identifiers}

Met deze informatie kunt u lokaal opgeslagen SDK-identiteiten ophalen uit uw Android-app en met aanvragen voor toegang tot GDPR-gegevens.

>[!IMPORTANT]
>
>De `getAllIdentifiersAsync` methode wint identiteiten terug die in SDK worden opgeslagen. U moet deze methode aanroepen **voordat** de gebruiker de functie uitschakelt.

SDK-identiteiten (indien van toepassing) worden lokaal opgeslagen en geretourneerd in een JSON-tekenreeks, die het volgende kan bevatten:

* Bedrijfcontext - IMS-organisatie-id&#39;s
* Gebruikersnamen
* Experience Cloud iD (MID), voorheen bekend als Marketing Cloud-ID
* Integratiecodes (ADID, Push ID)
* Gegevensbron-id&#39;s (DPID, DPUUID)
* Analytische id&#39;s (AVID, AID, VID en bijbehorende RSID&#39;s)
* Verouderde doel-id&#39;s (TNTID, TNT3rdpartyID)
* Audience Manager-id (UUID)

Hier volgt een voorbeeld van de `ADBMobile getAllIdentifiersAsync` methode in Android:

```java
Config.getAllIdentifiersAsync(new ConfigCallback<String>() { 
     @Override 
     public void call(String identitiesJson) {                 
         Log.d("ADBMobile Identities", identitiesJson); 
     } 
});
```
