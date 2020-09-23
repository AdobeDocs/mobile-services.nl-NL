---
description: U kunt uw app zo configureren dat deze Apple Push Notification Service (APNS) of Firebase Cloud Messaging (FCM) gebruikt.
keywords: mobile
seo-description: U kunt uw app zo configureren dat deze Apple Push Notification Service (APNS) of Firebase Cloud Messaging (FCM) gebruikt.
seo-title: App configureren voor gebruik van APNS of FCM
solution: Experience Cloud,Analytics
title: App configureren voor gebruik van APNS of FCM
topic: Metrics
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 11%

---


# Uw app configureren voor gebruik van APNS of FCM{#configure-app-to-use-apns-or-fcm}

U kunt uw app zo configureren dat deze Apple Push Notification Service (APNS) of Firebase Cloud Messaging (FCM) gebruikt.

## Android-apps {#section_41D304102CDF4586911EC1413AD35A10}

### Als FCM niet is ingeschakeld in uw app

Uw Android-app configureren voor gebruik van FCM in dit scenario:

1. Ga naar [https://firebase.google.com/](https://firebase.google.com/) en meld u aan met uw Google Dev-referenties.

1. Klik op **[!UICONTROL Get Started]** en selecteer **[!UICONTROL Add Project]**.

1. Voer een projectnaam in en klik op het selectievakje waarbij de voorwaarden van de controller worden geaccepteerd als u zich aanmeldt bij Google Analytics voor Firebase-gegevens.

1. Klik **[!UICONTROL Create project]** en wacht tot het project wordt gecreeerd.

1. Klik op het gemaakte project en de **[!UICONTROL Project Overview]** pagina voor het gemaakte project moet worden weergegeven. Klik op de knop met het Android-pictogram om een Android-app toe te voegen aan het project.

1. Voer zo nodig de naam van het toepassingspakket, de bijnaam van de toepassing en het handtekeningcertificaat in.

1. Volg de extra stappen die door de opstellingstovenaar worden voorgesteld. Ga terug naar de **[!UICONTROL Project Overview]** pagina nadat u de Firebase-instelling hebt gecontroleerd door de communicatie met de Firebase-servers te testen.

1. Klik op het tandwielpictogram rechts van de **[!UICONTROL Project Overview]** knop en klik **[!UICONTROL Project Settings]**.

1. Klik op het **[!UICONTROL Cloud Messaging]** tabblad.

1. Kopieer het bestand **[!UICONTROL Legacy server key]** en **[!UICONTROL Sender ID]** voor later gebruik.

   Bijvoorbeeld:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### Als FCM is ingeschakeld in uw app

Uw Android-app configureren voor gebruik van FCM in dit scenario:

1. Ga naar [https://firebase.google.com/](https://firebase.google.com/) en meld u aan met uw Google Dev-referenties.

1. Klik op **[!UICONTROL Get Started]**. Hiermee wordt de pagina met de projectindex geopend. Zoek het Firebase-ingeschakelde project dat is gekoppeld aan uw Android-app en klik op de projectkaart.

1. Het **[!UICONTROL Project Overview]** project moet dan worden geladen. Klik op het tandwielpictogram rechts van de **[!UICONTROL Project Overview]** knop en klik **[!UICONTROL Project Settings]**.

1. Klik op het **[!UICONTROL Cloud Messaging]** tabblad.

1. Kopieer het bestand **[!UICONTROL Legacy server key]** en **[!UICONTROL Sender ID]** voor later gebruik.

   Bijvoorbeeld:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## iOS-apps {#section_2031DAB485FC4D2B9027E42AD90B294D}

Uw iOS-app configureren voor het gebruik van APNS:

1. Ga naar [https://developer.apple.com/account](https://developer.apple.com/account) en meld u aan bij uw [Apple Developer-account](https://developer.apple.com/account).
1. Selecteer onder **[!UICONTROL iOS Apps]** de optie **[!UICONTROL Identifiers]**.
1. Ga naar Stap 11 als u een app-id hebt ingesteld voor push.
1. Druk op de **[!UICONTROL +]** knop om een nieuwe toepassings-id te maken.
1. Typ een beschrijving van de toepassings-id.
1. Typ een achtervoegsel voor de toepassings-id.

   >[!IMPORTANT]
   >
   >Voor ondersteuning van push moet u een expliciete toepassings-id gebruiken die **geen** jokerteken gebruikt (bijvoorbeeld `- com.tester.pushSample`).

1. Schakel onder **[!UICONTROL App Services]** het selectievakje **[!UICONTROL Push Notifications]** in.
1. Klik op **[!UICONTROL Continue]**.
1. Klik op **[!UICONTROL Submit]**.
1. Klik op **[!UICONTROL Done]**.
1. Selecteer uw app-id die is ingesteld voor het gebruik van pushberichten in de lijst en klik op **[!UICONTROL Edit]**.
1. Als er al een pushcertificaat is gemaakt, gaat u verder met stap 15.
1. Blader omlaag naar **[!UICONTROL Push Notifications]** en klik op de juiste knop **[!UICONTROL Create Certificate...]**.

   De knop waarop u klikt, is afhankelijk van het feit of u een certificaat voor ontwikkeling of productie maakt.
1. Voer de stappen uit voor het maken van uw CSR op de website van Apple, het uploaden van de CSR en het genereren van uw certificaat.
1. Blader omlaag naar de sectie **[!UICONTROL Push Notifications]** en download het SSL-certificaat dat u zojuist hebt gemaakt.
1. Dubbelklik op het gedownloade certificaat om het toe te voegen aan uw sleutelhanger.

### SSL-certificaat en persoonlijke sleutels

Ga als volgt te werk om uw SSL-certificaat en persoonlijke sleutel (APNS) op te halen:

1. Open **[!UICONTROL Keychain Access]**.
1. Klik op **[!UICONTROL My Certificates]** en zoek het juiste **[!UICONTROL iOS Push Services Certificate]** voor uw app en omgeving.

   U kunt het juiste certificaat identificeren door de bundle-id aan te passen en of het om Ontwikkeling of Productie gaat.

1. Vouw het certificaat uit en controleer of het een persoonlijke sleutel bevat.
1. Klik met de rechtermuisknop op de persoonlijke sleutel en selecteer **[!UICONTROL  Export " *`<name of key>`*]**.
1. Typ de benodigde gegevens in het dialoogvenster en sla het nieuwe `.p12` bestand op.

   U hoeft geen wachtwoord in te voeren.

1. Typ het **[!UICONTROL Private Key]** bestand in het `.p12` vak.

