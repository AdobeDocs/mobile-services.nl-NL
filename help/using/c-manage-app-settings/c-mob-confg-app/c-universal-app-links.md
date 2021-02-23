---
description: Het is belangrijk dat u koppelingen maakt in apps en websites om de gebruikerservaring te behouden. Leer hoe Universal en App Link werken en hoe verschillend ze zijn.
seo-description: Met Universal Links (iOS) en App Links (Android) kunt u verbinding maken met diepe koppelingen in uw iOS- of Android-apps.
seo-title: Koppelingen naar Apple Universal Links en Android App
solution: Experience Cloud,Analytics
title: Handleiding voor Universal Links en App Links
topic: Metrics
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
translation-type: tm+mt
source-git-commit: bb41caaecaefe8168d9b19e151d43ec792e24db8
workflow-type: tm+mt
source-wordcount: '1025'
ht-degree: 0%

---


# Universele koppelingen vs. App-koppelingen: Hoe werken ze? {#universal-links-and-app-links}

Met Universal Links (iOS) en App Links (Android) kunt u verbinding maken met diepe koppelingen in uw iOS- of Android-apps.

>[!IMPORTANT]
>
>Vanaf iOS 9.2 wordt deep linking niet ondersteund. U moet Apple Universal Links gebruiken voor een diepe koppeling naar uw app of website.

## Universele koppelingen {#section_F8147944679A42E59CF4FD8814E5EF12}

Met Universal Links kunt u verbinding maken met diepe koppelingen in uw iOS-app. Deze koppelingen worden ondersteund in iOS 9.2 of hoger. Wanneer een Universal Link wordt benaderd, leidt iOS de koppeling rechtstreeks naar de koppeling in uw app. Als uw app niet is geïnstalleerd, wordt in plaats daarvan een URL voor uw website in een browser geopend. Voor meer informatie over Universele Verbindingen, zie [Universele Verbindingen](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html) steunen.

## Toepassingskoppelingen

Met App-koppelingen kunt u verbinding maken met diepe koppelingen in uw Android-app. Deze koppelingen worden ondersteund in Android 6.0 of hoger. Wanneer een App-koppeling wordt geopend, stuurt Android de koppeling rechtstreeks naar de koppeling in uw app. Als uw app niet is geïnstalleerd, wordt in plaats daarvan een URL voor uw website in een browser geopend. Zie [Android App-koppelingen afhandelen](https://developer.android.com/training/app-links/index.html) voor meer informatie over App-koppelingen.

## Creeer een Verbinding van de Marketing door een Universele of Verbinding {#section_609ADEFFB9B441C4A8C45E936D0DC859} te gebruiken App

U kunt een Marketing Link tot stand brengen die een Universele Verbinding of een Verbinding van de App gebruikt.

### Een Universal Link configureren

1. Als u Universal Links wilt instellen in uw iOS-app, gaat u naar [Universal Links afhandelen in Apple](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links).

2. In de Mobiele Diensten van Adobe, opstelling de plaats-vereniging documenten:

   a. Selecteer op de startpagina voor mobiele services de app waarvoor u Universal Links wilt instellen.

   b. Klik op **[!UICONTROL Manage App Settings]**.

   c. Zorg ervoor dat de iOS-app die de Universal Links afhandelt, wordt toegevoegd aan de sectie **[!UICONTROL Add App Store Apps]**.

   >[!TIP]
   >
   >Als de sectie **[!UICONTROL Add App Store Apps]** niet wordt weergegeven, klikt u op de koppeling **[!UICONTROL Add App Store App]**.

   d. Selecteer een iOS-toepassing in de sectie **[!UICONTROL Universal Links and App Links Options]** en typ de toepassings-id.

   f. Klik op **[!UICONTROL Save]**.

   U moet ten minste één selectie voor de iOS-app en één toepassings-id opgeven, anders ontvangt u een fout.

   >[!IMPORTANT]
   >
   >U kunt de documenten bijwerken door op Bijwerken te klikken in de sectie Opties voor Universal-koppelingen en App-koppelingen. Wanneer u echter op **[!UICONTROL Update]** klikt, wordt u gewaarschuwd dat dit van invloed is op alle Universal Links of App-koppelingen die u in het verleden hebt gemaakt.

### Een Universal Link gebruiken

1. In de Mobiele Diensten van Adobe, creeer een Verbinding van de Marketing die Universele Verbindingen gebruikt:

   a. Selecteer de app op de startpagina van Mobile Services en klik op **[!UICONTROL Acquisition]** > **[!UICONTROL Marketing Link Builder]**.

   b. Klik op **[!UICONTROL Create New]**.

   c. Selecteer **[!UICONTROL Use Universal Links or App Links]** onder **[!UICONTROL Marketing Link Options]**.

   d. Als u de site-associatiedocumenten hebt geconfigureerd in de sectie *Site-koppeling instellen in de sectie Adobe Mobile Services* hierboven, is deze optie standaard ingeschakeld.

   Als u de documenten niet hebt geconfigureerd, is de optie **[!UICONTROL Use Universal Links or App Links]** uitgeschakeld en is **[!UICONTROL Use Interstitials]** standaard geselecteerd.

   e. Als de optie **[!UICONTROL Use Universal Links or App Links]** is geselecteerd, wordt het veld **[!UICONTROL Custom Path]** weergegeven.

   Hierdoor kunnen gebruikers het URL-pad na het domein definiëren met elke queryparameter. Als u bijvoorbeeld `my/universal/link?os=9.2` typt, wordt de volledige URL van de marketingkoppeling `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`.

   f. Klik op de tab **[!UICONTROL Decisions]** en configureer de beslissingstructuur.

   h. Als de iOS-app is geïnstalleerd, handelt de app de deplink met de bijbehorende logica af. De uiteindelijke bestemming fungeert alleen als fallback wanneer de app niet is geïnstalleerd. Aangezien de app niet is geïnstalleerd, kan de uiteindelijke bestemming alleen een webkoppeling of app-winkel zijn.

   i. Klik op **[!UICONTROL Save]**.

>[!TIP]
>
>Als een marketingkoppeling eenmaal is opgeslagen, kunnen de opties voor marketingkoppelingen niet meer worden gewijzigd. Dit is omdat u niet het gedrag van de Verbindingen van de Marketing wilt veranderen die reeds kunnen zijn verdeeld.


### Een toepassingskoppeling configureren

1. Als u toepassingskoppelingen wilt instellen in uw Android-app, gaat u naar [Android-toepassingskoppelingen toevoegen](https://developer.android.com/studio/write/app-link-indexing).

1. In de Mobiele Diensten van Adobe, opstelling de plaats-vereniging documenten:

   a. Selecteer op de startpagina voor mobiele services de app waarvoor u App Links wilt instellen.

   b. Klik op **[!UICONTROL Manage App Settings]**.

   c. Zorg ervoor dat de Android-toepassing die de Universal Links of App Links afhandelt, wordt toegevoegd aan de sectie **[!UICONTROL Add App Store Apps]**.

   >[!TIP]
   >
   >Als deze sectie niet wordt weergegeven, klikt u op de koppeling **[!UICONTROL Add App Store App]**.

   d. Blader naar de sectie **[!UICONTROL Universal Links and App Links Options]**.

   e. Klik op het tabblad **[!UICONTROL App Links (Android)]**.

   f. Selecteer een Android-toepassing en typ een vingerafdruk van het SHA-256-certificaat.

   g. Klik op **[!UICONTROL Save]**.

   U moet ten minste één selectie voor de Android-app en één SHA-256-certificaat opgeven, anders ontvangt u een fout.

   >[!IMPORTANT]
   >
   >U kunt de documenten bijwerken door in de sectie **[!UICONTROL Universal Links and App Links Options]** op **[!UICONTROL Update]** te klikken. Wanneer u echter op **[!UICONTROL Update]** klikt, wordt u gewaarschuwd dat dit van invloed is op alle Universal Links of App-koppelingen die u in het verleden hebt gemaakt.

### App-koppeling gebruiken

1. In de Mobiele Diensten van Adobe, creeer een Verbinding van de Marketing die de Verbindingen van de Toepassing gebruikt:

   a. Selecteer de app op de startpagina van Mobile Services en klik op **[!UICONTROL Acquisition]** > **[!UICONTROL Marketing Link Builder]**.

   b. Klik op **[!UICONTROL Create New]**.

   c. Selecteer **[!UICONTROL Use Universal Links or App Links]** in de sectie **[!UICONTROL Marketing Link Options]**.

   d. Als u de site-associatiedocumenten hebt geconfigureerd in stap 2, is deze optie standaard geselecteerd.

   Als dat niet het geval is, wordt de optie **[!UICONTROL Use Universal Links or App Links]** uitgeschakeld en wordt **[!UICONTROL Use Interstitials]** standaard geselecteerd.

   e. Als **[!UICONTROL Use Universal Links or App Links]** wordt geselecteerd, wordt **[!UICONTROL Custom Path]** gebied getoond.

   Hierdoor kunnen gebruikers het URL-pad na het domein definiëren met elke queryparameter. Als u bijvoorbeeld `my/app/link?os=6.0` typt, wordt de volledige URL van de marketingkoppeling `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`.

   f. Klik op de tab **[!UICONTROL Decisions]** en configureer de beslissingstructuur.

   g. Als de Android-app is geïnstalleerd, handelt de toepassing de deplink met de bijbehorende logica af.

   De uiteindelijke bestemming fungeert alleen als fallback-case wanneer de app niet is geïnstalleerd. Aangezien de app niet is geïnstalleerd, kan de uiteindelijke bestemming alleen een webkoppeling of app-winkel zijn.

   h.  Klik op **[!UICONTROL Save]**.

>[!TIP]
>
>Nadat een Verbinding van de Marketing wordt bewaard, kan **[!UICONTROL Marketing Links Options]** niet worden veranderd. Dit is omdat u niet het gedrag van de Verbindingen van de Marketing wilt veranderen die reeds kunnen zijn verdeeld.

## Marketingskoppelingen gebruiken

U kunt deze marketingkoppelingen nu gebruiken in berichten en andere gebieden in uw app.

>[!IMPORTANT]
>
>Er worden geen tellingen voor bijhouden van klikken weergegeven met Universal Links of App Links en u kunt ook geen interstitiële elementen gebruiken.

