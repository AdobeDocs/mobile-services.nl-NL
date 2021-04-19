---
description: Hier volgt een aantal informatie waarmee u de Android-extensie kunt configureren. Hiermee kunt u gegevens verzamelen van uw Android Wearable-app.
seo-description: Hier volgt een aantal informatie waarmee u de Android-extensie kunt configureren. Hiermee kunt u gegevens verzamelen van uw Android Wearable-app.
seo-title: Android Wearables - aanvullende opmerkingen
solution: Experience Cloud,Analytics
title: Android Wearables - aanvullende opmerkingen
topic-fix: Developer and implementation
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
exl-id: ae8cf2d1-d2b0-456b-bbd3-3980e00bbc84
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Android-oormerken: extra notities{#android-wearables-additional-notes}

Hier volgt een aantal informatie waarmee u de Android-extensie kunt configureren. Hiermee kunt u gegevens verzamelen van uw Android Wearable-app.

* De extensie Adobe Mobile Android Wearables vereist Android versie 4.4 (KitKat) of hoger.
* Er is één extra contextwaarde, `A.RunMode`, die is toegevoegd om aan te geven of de gegevens uit de bevattende app of de extensie afkomstig zijn.

   * `RunMode` = `Application`

      De hit komt van de handheld app.

   * `RunMode` =  `Extension`

      De hit komt van de draagbare app.

* De SDK synchroniseert automatisch de `aid`/`vid`/`visitor` `service id`/`privacy` status van de handheld app naar de draagbare app, dus roep `setPrivacyStatus`/`setUserIdentifier`/`idSync` niet aan vanuit de draagbare app.
* [Berichten](/help/android/messaging-main/messaging/messaging.md) in de app,  [Doel](/help/android/target-main/target.md) en  [Audience ](/help/android/audience-manager/audiencemgmt.md) Managerzijn uitgeschakeld voor de betrouwbare app.
