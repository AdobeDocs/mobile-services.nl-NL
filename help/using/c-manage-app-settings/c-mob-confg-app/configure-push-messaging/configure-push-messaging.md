---
description: Met deze informatie kunt u de opties voor pushservices configureren op de pagina Toepassingsinstellingen beheren terwijl u een nieuwe app maakt of een bestaande app bewerkt.
keywords: mobiel
solution: Experience Cloud Services,Analytics
title: Push Messaging configureren
topic-fix: Metrics
uuid: 6763858d-6046-4d36-87c0-cf3600a44fb1
exl-id: d4989c31-2692-4062-8fae-d41c3e3c179b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Pushberichten configureren{#configure-push-messaging}

Met deze informatie kunt u de opties voor pushservices op de pagina Toepassingsinstellingen beheren configureren wanneer u een nieuwe app maakt of een bestaande app bewerkt.

Voordat u pushberichten configureert, moet u de vereiste taken uitvoeren in [Vereisten voor het inschakelen van pushberichten](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md).

* **Overwegingen bij de rapportsuite**

   U kunt één app store-app voor Apple en één voor Google configureren in elke rapportsuite. Als u aanvullende apps nodig hebt, bijvoorbeeld één voor een productieomgeving en één voor een ontwikkelomgeving, stelt u een nieuwe app store-app en een nieuwe rapportsuite in voor elke omgeving.

>[!IMPORTANT]
>
>Het verplaatsen van uw app naar een nieuwe rapportsuite wordt niet ondersteund. Als u naar een nieuwe rapportreeks migreert, kan uw dupconfiguratie breken, en de berichten zouden niet kunnen worden verzonden.

1. Typ informatie in de volgende velden onder **[!UICONTROL Push Services]**:

   * Apple

      **[!UICONTROL Private Key]**

      Bladeren naar en een geldige persoonlijke sleutel selecteren `.p12`, `.key`, of `.pen`.

      >[!IMPORTANT]
      >Als het bestand dat u selecteert voor de **[!UICONTROL Private Key]** invoer bevat ook een certificaat, u hoeft het certificaat niet op te geven.

   * **[!UICONTROL Certificate]**

      Geef een geldig certificaat op. Deze optie is alleen vereist als de optie **[!UICONTROL Private Key]** invoer doet dit **niet** bevatten een certificaat. Ga voor meer informatie over het verkrijgen van het SSL-certificaat en de persoonlijke sleutel naar [App configureren voor gebruik van APNS of FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

   * Google

      **[!UICONTROL API Key]**

      Geef een geldige API-sleutel op. Ga voor meer informatie over het verkrijgen van de API-sleutel naar [App configureren voor gebruik van APNS of FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

      Raadpleeg de volgende onderwerpen voor meer informatie:

      * [Push Messaging in Android](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [Push Messaging in iOS](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. Klik op **[!UICONTROL Save]**.
