---
description: Hier volgt een aantal informatie waarmee u de Android-extensie kunt configureren. Hiermee kunt u gegevens verzamelen van uw Android Wearable-app.
seo-description: Hier volgt een aantal informatie waarmee u de Android-extensie kunt configureren. Hiermee kunt u gegevens verzamelen van uw Android Wearable-app.
seo-title: Android Wearables - aanvullende opmerkingen
solution: Marketing Cloud,Analytics
title: Android Wearables - aanvullende opmerkingen
topic: Developer and implementation
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Android-oormerken: aanvullende opmerkingen{#android-wearables-additional-notes}

Hier volgt een aantal informatie waarmee u de Android-extensie kunt configureren. Hiermee kunt u gegevens verzamelen van uw Android Wearable-app.

* De extensie Adobe Mobile Android Wearables vereist Android versie 4.4 (KitKat) of hoger.
* Er is één extra contextwaarde `A.RunMode`toegevoegd om aan te geven of de gegevens afkomstig zijn van de bevattende app of de extensie.

   * `RunMode` = `Application`

      De hit komt van de handheld app.

   * `RunMode` = `Extension`

      De hit komt van de draagbare app.

* De SDK synchroniseert automatisch de status `aid`/`vid`/`visitor` `service id`/`privacy` van de handheld-app naar de draagbare app, dus roep `setPrivacyStatus`/`setUserIdentifier`/`idSync` niet vanuit de draagbare app.
* [Berichten](/help/android/messaging-main/messaging/messaging.md)in de app, [Doel](/help/android/target-main/target.md)en [Audience Manager](/help/android/audience-manager/audiencemgmt.md) zijn uitgeschakeld voor de betrouwbare app.

