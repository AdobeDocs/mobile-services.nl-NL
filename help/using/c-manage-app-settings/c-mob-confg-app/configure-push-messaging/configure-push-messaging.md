---
description: Met deze informatie kunt u de opties voor pushservices configureren op de pagina Toepassingsinstellingen beheren terwijl u een nieuwe app maakt of een bestaande app bewerkt.
keywords: mobile
seo-description: Met deze informatie kunt u de opties voor pushservices configureren op de pagina Toepassingsinstellingen beheren terwijl u een nieuwe app maakt of een bestaande app bewerkt.
seo-title: Push Messaging configureren
solution: Marketing Cloud,Analytics
title: Push Messaging configureren
topic: Metrics
uuid: 6763858d-6046-4d36-87c0-cf3600a44fb1
translation-type: tm+mt
source-git-commit: 2c85c31d2fa54de26771553a6d349d3101e0048c

---


# Pushberichten configureren{#configure-push-messaging}

Met deze informatie kunt u de opties voor pushservices op de pagina Toepassingsinstellingen beheren configureren wanneer u een nieuwe app maakt of een bestaande app bewerkt.

Alvorens u duw overseinen vormt, voltooi de eerste vereiste taken in [Eerste vereisten om het Overseinen](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)van de Duw toe te laten.

* **Overwegingen bij de rapportsuite**

   U kunt in elke rapportsuite één app store-app configureren voor Apple en één voor Google. Als u aanvullende apps nodig hebt, bijvoorbeeld één voor een productieomgeving en één voor een ontwikkelomgeving, stelt u een nieuwe app store-app en een nieuwe rapportsuite in voor elke omgeving.

>[!IMPORTANT]
>
>Het verplaatsen van uw app naar een nieuwe rapportsuite wordt niet ondersteund. Als u naar een nieuwe rapportreeks migreert, kan uw dupconfiguratie breken, en de berichten zouden niet kunnen worden verzonden.

1. Typ gegevens in de volgende velden onder **[!UICONTROL Push Services]**:

   * Apple

      **[!UICONTROL Private Key]**

      Blader naar en selecteer de geldige persoonlijke sleutel `.p12`, `.key`of `.pen`.

      >[!IMPORTANT]
      >Als het bestand dat u voor de **[!UICONTROL Private Key]** invoer selecteert, ook een certificaat bevat, hoeft u het certificaat niet op te geven.

   * **[!UICONTROL Certificate]**

      Geef een geldig certificaat op. Deze optie is alleen vereist als de **[!UICONTROL Private Key]** invoer **geen** certificaat bevat. Zie App [configureren voor gebruik van APNS of FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)voor meer informatie over het verkrijgen van het SSL-certificaat en de persoonlijke sleutel.

   * Google

      **[!UICONTROL API Key]**

      Geef een geldige API-sleutel op. Zie App [configureren voor gebruik van APNS of FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)voor meer informatie over het verkrijgen van de API-sleutel.

      Raadpleeg de volgende onderwerpen voor meer informatie:

      * [Push Messaging in Android](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [Push Messaging in iOS](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. Klik op **[!UICONTROL Save]**.
