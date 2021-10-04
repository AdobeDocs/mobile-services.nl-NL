---
description: Met deze informatie kunt u lokaal opgeslagen SDK-identiteiten ophalen uit uw Android-app en met aanvragen voor toegang tot GDPR-gegevens.
title: Opgeslagen id's ophalen
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
exl-id: 86c990d8-334b-4003-b0ac-d5404cb598e4
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---

# Opgeslagen id&#39;s ophalen{#retrieving-stored-identifiers}

Met deze informatie kunt u lokaal opgeslagen SDK-identiteiten ophalen uit uw Android-app en met aanvragen voor toegang tot GDPR-gegevens.

>[!IMPORTANT]
>
>Met de methode `getAllIdentifiersAsync` worden identiteiten opgehaald die in de SDK zijn opgeslagen. U moet deze methode **before** de gebruiker uit opteert.

SDK-identiteiten (indien van toepassing) worden lokaal opgeslagen en geretourneerd in een JSON-tekenreeks, die het volgende kan bevatten:

* Bedrijfcontext - IMS-organisatie-id&#39;s
* Gebruikersnamen
* Experience Cloud iD (MID), voorheen bekend als Marketing Cloud-ID
* Integratiecodes (ADID, Push ID)
* Gegevensbron-id&#39;s (DPID, DPUUID)
* Analytische id&#39;s (AVID, AID, VID en bijbehorende RSID&#39;s)
* Verouderde doel-id&#39;s (TNTID, TNT3rdpartyID)
* Audience Manager-id (UUID)

Hier volgt een voorbeeld van de methode `ADBMobile getAllIdentifiersAsync` in Android:

```java
Config.getAllIdentifiersAsync(new ConfigCallback<String>() { 
     @Override 
     public void call(String identitiesJson) {                 
         Log.d("ADBMobile Identities", identitiesJson); 
     } 
});
```
