---
description: U kunt uw app zo configureren dat deze gebruikmaakt van de Apple Push Notification Service (APNS) of Firebase Cloud Messaging (FCM).
keywords: mobiel
solution: Experience Cloud Services,Analytics
title: App configureren voor gebruik van APNS of FCM
topic-fix: Metrics
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
exl-id: 9064e1f3-f176-4699-b1e6-90f29e1af0d3
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 12%

---

# Uw app configureren voor gebruik van APNS of FCM{#configure-app-to-use-apns-or-fcm}

U kunt uw app zo configureren dat deze gebruikmaakt van de Apple Push Notification Service (APNS) of Firebase Cloud Messaging (FCM).

## Android-apps {#section_41D304102CDF4586911EC1413AD35A10}

### Als FCM niet is ingeschakeld in uw app

Uw Android-app configureren voor gebruik van FCM in dit scenario:

1. Ga naar [https://firebase.google.com/](https://firebase.google.com/) en meld u aan met uw Google Dev-referenties.

1. Klik op **[!UICONTROL Get Started]** en selecteer **[!UICONTROL Add Project]**.

1. Voer een projectnaam in en klik op het selectievakje waarbij de voorwaarden van de controller worden geaccepteerd als u zich aanmeldt bij Google Analytics voor Firebase-gegevens.

1. Klikken **[!UICONTROL Create project]** en wacht tot het project is gemaakt.

1. Klik op het gemaakte project en de **[!UICONTROL Project Overview]** de pagina voor het gemaakte project moet worden weergegeven. Klik op de knop met het Android-pictogram om een Android-app toe te voegen aan het project.

1. Voer zo nodig de naam van het toepassingspakket, de bijnaam van de toepassing en het handtekeningcertificaat in.

1. Volg de extra stappen die door de opstellingstovenaar worden voorgesteld. Nadat u de Firebase-instelling hebt gecontroleerd door de communicatie met de Firebase-servers te testen, gaat u terug naar de **[!UICONTROL Project Overview]** pagina.

1. Klik op het tandwielpictogram rechts van **[!UICONTROL Project Overview]** en klik op **[!UICONTROL Project Settings]**.

1. Klik op de knop **[!UICONTROL Cloud Messaging]** tab.

1. Kopieer de **[!UICONTROL Legacy server key]** en **[!UICONTROL Sender ID]** voor later gebruik.

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

1. De **[!UICONTROL Project Overview]** voor het project wordt geladen. Klik op het tandwielpictogram rechts van **[!UICONTROL Project Overview]** en klik op **[!UICONTROL Project Settings]**.

1. Klik op de knop **[!UICONTROL Cloud Messaging]** tab.

1. Kopieer de **[!UICONTROL Legacy server key]** en **[!UICONTROL Sender ID]** voor later gebruik.

   Bijvoorbeeld:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## iOS-apps {#section_2031DAB485FC4D2B9027E42AD90B294D}

Om uw iOS-app te configureren voor het gebruik van APNS:

1. Ga naar [https://developer.apple.com/account](https://developer.apple.com/account) en meld u aan bij uw [Apple Developer-account](https://developer.apple.com/account).
1. Selecteer onder **[!UICONTROL iOS Apps]** de optie **[!UICONTROL Identifiers]**.
1. Ga naar Stap 11 als u een app-id hebt ingesteld voor push.
1. Druk op **[!UICONTROL +]** om een nieuwe toepassings-id te maken.
1. Typ een beschrijving van de toepassings-id.
1. Typ een achtervoegsel voor de toepassings-id.

   >[!IMPORTANT]
   >
   >Voor ondersteuning van push moet u een expliciete toepassings-id gebruiken die **niet** een jokerteken gebruiken (bijvoorbeeld `- com.tester.pushSample`).

1. Schakel onder **[!UICONTROL App Services]** het selectievakje **[!UICONTROL Push Notifications]** in.
1. Klik op **[!UICONTROL Continue]**.
1. Klik op **[!UICONTROL Submit]**.
1. Klik op **[!UICONTROL Done]**.
1. Selecteer uw app-id die is ingesteld voor het gebruik van pushberichten in de lijst en klik op **[!UICONTROL Edit]**.
1. Als er al een pushcertificaat is gemaakt, gaat u verder met stap 15.
1. Blader omlaag naar **[!UICONTROL Push Notifications]** en klik op de juiste knop **[!UICONTROL Create Certificate...]**.

   De knop waarop u klikt, is afhankelijk van het feit of u een certificaat voor ontwikkeling of productie maakt.
1. Voer de stappen uit om uw CSR-bestand te maken op de Apple-website, de CSR te uploaden en uw certificaat te genereren.
1. Blader omlaag naar de sectie **[!UICONTROL Push Notifications]** en download het SSL-certificaat dat u zojuist hebt gemaakt.
1. Dubbelklik op het gedownloade certificaat om het toe te voegen aan uw sleutelhanger.

### SSL-certificaat en persoonlijke sleutels

Ga als volgt te werk om uw SSL-certificaat en persoonlijke sleutel (APNS) op te halen:

1. Open **[!UICONTROL Keychain Access]**.
1. Klik op **[!UICONTROL My Certificates]** en zoek het juiste **[!UICONTROL iOS Push Services Certificate]** voor uw app en omgeving.

   U kunt het juiste certificaat identificeren door de bundle-id aan te passen en of het om Ontwikkeling of Productie gaat.

1. Vouw het certificaat uit en controleer of het een persoonlijke sleutel bevat.
1. Klik met de rechtermuisknop op de persoonlijke sleutel en selecteer **[!UICONTROL  Export " *`<name of key>`*]**.
1. Typ de benodigde gegevens in het dialoogvenster en sla uw nieuwe gegevens op `.p12` bestand.

   U hoeft geen wachtwoord in te voeren.

1. In de **[!UICONTROL Private Key]**, typt u de `.p12` bestand.
