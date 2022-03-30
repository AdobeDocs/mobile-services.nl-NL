---
description: Hier volgt een aantal informatie waarmee u de Android-extensie kunt configureren. Hiermee kunt u gegevens verzamelen van uw Android Wearable-app.
solution: Experience Cloud Services,Analytics
title: Android Wearables - aanvullende opmerkingen
topic-fix: Developer and implementation
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
exl-id: ae8cf2d1-d2b0-456b-bbd3-3980e00bbc84
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Android-oormerken: aanvullende opmerkingen{#android-wearables-additional-notes}

Hier volgt een aantal informatie waarmee u de Android-extensie kunt configureren. Hiermee kunt u gegevens verzamelen van uw Android Wearable-app.

* De extensie Adobe Mobile Android Wearables vereist Android versie 4.4 (KitKat) of hoger.
* Er is één extra contextwaarde, `A.RunMode`, die is toegevoegd om aan te geven of de gegevens afkomstig zijn van de bevattende app of de extensie.

   * `RunMode` = `Application`

      De hit komt van de handheld app.

   * `RunMode` = `Extension`

      De hit komt van de draagbare app.

* De SDK synchroniseert automatisch de `aid`/`vid`/`visitor` `service id`/`privacy` status van de handheld-app naar de draagbare app. Roep daarom niet `setPrivacyStatus`/`setUserIdentifier`/`idSync` uit de draagbare app.
* [In-app berichten](/help/android/messaging-main/messaging/messaging.md), [Doel](/help/android/target-main/target.md), en [Audience Manager](/help/android/audience-manager/audiencemgmt.md) zijn uitgeschakeld voor de verhandelbare app.
