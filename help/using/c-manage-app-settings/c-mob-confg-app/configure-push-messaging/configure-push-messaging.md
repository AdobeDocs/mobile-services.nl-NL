---
description: Met deze informatie kunt u de opties voor pushservices configureren op de pagina Toepassingsinstellingen beheren terwijl u een nieuwe app maakt of een bestaande app bewerkt.
keywords: mobiel
solution: Experience Cloud,Analytics
title: Push Messaging configureren
topic-fix: Metrics
uuid: 6763858d-6046-4d36-87c0-cf3600a44fb1
exl-id: d4989c31-2692-4062-8fae-d41c3e3c179b
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Pushberichten configureren{#configure-push-messaging}

Met deze informatie kunt u de opties voor pushservices op de pagina Toepassingsinstellingen beheren configureren wanneer u een nieuwe app maakt of een bestaande app bewerkt.

Alvorens u duw overseinen vormt, voltooi de in eerste instantie vereiste taken in [Vereisten om het Overseinen van de Duw toe te laten](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md).

* **Overwegingen bij de rapportsuite**

   U kunt in elke rapportsuite één app store-app configureren voor Apple en één voor Google. Als u aanvullende apps nodig hebt, bijvoorbeeld één voor een productieomgeving en één voor een ontwikkelomgeving, stelt u een nieuwe app store-app en een nieuwe rapportsuite in voor elke omgeving.

>[!IMPORTANT]
>
>Het verplaatsen van uw app naar een nieuwe rapportsuite wordt niet ondersteund. Als u naar een nieuwe rapportreeks migreert, kan uw dupconfiguratie breken, en de berichten zouden niet kunnen worden verzonden.

1. Typ informatie in de volgende velden onder **[!UICONTROL Push Services]**:

   * Apple

      **[!UICONTROL Private Key]**

      Blader naar en selecteer uw geldige persoonlijke sleutel `.p12`, `.key` of `.pen`.

      >[!IMPORTANT]
      >Als het bestand dat u selecteert voor de invoer **[!UICONTROL Private Key]** ook een certificaat bevat, hoeft u het certificaat niet op te geven.

   * **[!UICONTROL Certificate]**

      Geef een geldig certificaat op. Deze optie is alleen vereist wanneer de **[!UICONTROL Private Key]**-invoer **geen** een certificaat bevat. Zie [App configureren voor gebruik van APNS of FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md) voor meer informatie over het verkrijgen van het SSL-certificaat en de persoonlijke sleutel.

   * Google

      **[!UICONTROL API Key]**

      Geef een geldige API-sleutel op. Zie [App configureren voor gebruik van APNS of FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md) voor meer informatie over het verkrijgen van de API-sleutel.

      Raadpleeg de volgende onderwerpen voor meer informatie:

      * [Push Messaging in Android](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [Push Messaging in iOS](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. Klik op **[!UICONTROL Save]**.
