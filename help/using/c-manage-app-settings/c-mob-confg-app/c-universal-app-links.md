---
description: Met Universal Links (iOS) en App Links (Android) kunt u verbinding maken met diepe koppelingen in uw iOS- of Android-apps.
keywords: mobile
seo-description: Met Universal Links (iOS) en App Links (Android) kunt u verbinding maken met diepe koppelingen in uw iOS- of Android-apps.
seo-title: Koppelingen naar Apple Universal Links en Android App
solution: Marketing Cloud,Analytics
title: Koppelingen naar Apple Universal Links en Android App
topic: Metrics
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# Koppelingen naar Apple Universal Links en Android App{#universal-links-and-app-links}

Met Universal Links (iOS) en App Links (Android) kunt u verbinding maken met diepe koppelingen in uw iOS- of Android-apps.

>[!IMPORTANT]
>
>Vanaf iOS 9.2 wordt deep linking niet ondersteund. U moet Apple Universal Links gebruiken voor een diepe koppeling naar uw app of website.

## Universele koppelingen {#section_F8147944679A42E59CF4FD8814E5EF12}

Met Universal Links kunt u verbinding maken met diepe koppelingen in uw iOS-app. Deze koppelingen worden ondersteund in iOS 9.2 of hoger. Wanneer een Universal Link wordt benaderd, leidt iOS de koppeling rechtstreeks naar de koppeling in uw app. Als uw app niet is geïnstalleerd, wordt in plaats daarvan een URL voor uw website in een browser geopend. Zie [Universele koppelingen](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html)ondersteunen voor meer informatie over Universal Links.

## Toepassingskoppelingen

Met App-koppelingen kunt u verbinding maken met diepe koppelingen in uw Android-app. Deze koppelingen worden ondersteund in Android 6.0 of hoger. Wanneer een App-koppeling wordt geopend, stuurt Android de koppeling rechtstreeks naar de koppeling in uw app. Als uw app niet is geïnstalleerd, wordt in plaats daarvan een URL voor uw website in een browser geopend. Raadpleeg de koppelingen voor Android-toepassingen [afhandelen voor meer informatie over App-koppelingen](https://developer.android.com/training/app-links/index.html).

## Creeer een Verbinding van de Marketing door een Universele of Verbinding van de App te gebruiken {#section_609ADEFFB9B441C4A8C45E936D0DC859}

U kunt een Marketing Link tot stand brengen die een Universele Verbinding of een Verbinding van de App gebruikt.

### Een Universal Link configureren

1. Als u Universal Links wilt instellen in uw iOS-app, gaat u naar [Universal Links beheren in Apple](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links).

2. Stel in Adobe Mobile Services de documenten voor de sitekoppeling in:

   a. Selecteer op de startpagina voor mobiele services de app waarvoor u Universal Links wilt instellen.

   b. Klik **[!UICONTROL Manage App Settings]**.

   c. Zorg ervoor dat de iOS-app die de Universal Links afhandelt, aan de **[!UICONTROL Add App Store Apps]** sectie wordt toegevoegd.

   >[!TIP]
   >
   >Als de **[!UICONTROL Add App Store Apps]** sectie niet wordt weergegeven, klikt u op de **[!UICONTROL Add App Store App]** koppeling.

   d. Selecteer een iOS-app in de **[!UICONTROL Universal Links and App Links Options]** sectie en typ de toepassings-id.

   f. Klik **[!UICONTROL Save]**.

   U moet ten minste één selectie voor de iOS-app en één toepassings-id opgeven, anders ontvangt u een fout.

   >[!IMPORTANT]
   >
   >U kunt de documenten bijwerken door op Bijwerken te klikken in de sectie Opties voor Universal-koppelingen en App-koppelingen. Wanneer u echter klikt **[!UICONTROL Update]**, wordt u gewaarschuwd dat dit invloed heeft op alle Universal Links of App Links die u in het verleden hebt gemaakt.

### Een Universal Link gebruiken

1. Maak in Adobe Mobile Services een marketingkoppeling die gebruikmaakt van Universal Links:

   a. Selecteer de app op de startpagina van Mobile Services en klik op **[!UICONTROL Acquisition]** > **[!UICONTROL Marketing Link Builder]**.

   b. Klik **[!UICONTROL Create New]**.

   c. Selecteer onder **[!UICONTROL Marketing Link Options]** de optie **[!UICONTROL Use Universal Links or App Links]**.

   d. Als u de documenten voor sitekoppelingen hebt geconfigureerd in de bovenstaande sectie *Site-associatie instellen in Adobe Mobile Services* , is deze optie standaard geselecteerd.

   Als u de documenten niet hebt geconfigureerd, is de **[!UICONTROL Use Universal Links or App Links]** optie uitgeschakeld en **[!UICONTROL Use Interstitials]** is deze standaard geselecteerd.

   e. Als de **[!UICONTROL Use Universal Links or App Links]** optie is geselecteerd, wordt het **[!UICONTROL Custom Path]** veld weergegeven.

   Hierdoor kunnen gebruikers het URL-pad na het domein definiëren met elke queryparameter. Als u bijvoorbeeld typt `my/universal/link?os=9.2`, wordt de volledige URL van de marketingkoppeling `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`.

   f. Klik op het **[!UICONTROL Decisions]** tabblad en configureer de beslissingstructuur.

   h. Als de iOS-app is geïnstalleerd, verwerkt de app de deplink met de bijbehorende logica. De uiteindelijke bestemming fungeert alleen als fallback wanneer de app niet is geïnstalleerd. Aangezien de app niet is geïnstalleerd, kan de uiteindelijke bestemming alleen een webkoppeling of app-winkel zijn.

   i. Klik **[!UICONTROL Save]**.

>[!TIP]
>
>Als een marketingkoppeling eenmaal is opgeslagen, kunnen de opties voor marketingkoppelingen niet meer worden gewijzigd. Dit is omdat u niet het gedrag van de Verbindingen van de Marketing wilt veranderen die reeds kunnen zijn verdeeld.


### Een toepassingskoppeling configureren

1. Ga naar Android-toepassingskoppelingen [toevoegen om App-koppelingen](https://developer.android.com/studio/write/app-link-indexing)in te stellen in uw Android-app.

1. Stel in Adobe Mobile Services de documenten voor de sitekoppeling in:

   a. Selecteer op de startpagina voor mobiele services de app waarvoor u App Links wilt instellen.

   b. Klik **[!UICONTROL Manage App Settings]**.

   c. Controleer of de Android-app die de Universal Links of App Links afhandelt, aan de **[!UICONTROL Add App Store Apps]** sectie is toegevoegd.

   >[!TIP]
   >
   >Als deze sectie niet wordt weergegeven, klikt u op de **[!UICONTROL Add App Store App]** koppeling.

   d. Blader naar de **[!UICONTROL Universal Links and App Links Options]** sectie.

   e. Klik op het **[!UICONTROL App Links (Android)]** tabblad.

   f. Selecteer een Android-toepassing en typ een vingerafdruk van het SHA-256-certificaat.

   g. Klik **[!UICONTROL Save]**.

   U moet ten minste één selectie voor de Android-app en één SHA-256-certificaat opgeven, anders ontvangt u een fout.

   >[!IMPORTANT]
   >
   >U kunt de documenten bijwerken door vanuit **[!UICONTROL Update]** de **[!UICONTROL Universal Links and App Links Options]** sectie te klikken. Wanneer u echter klikt **[!UICONTROL Update]**, wordt u gewaarschuwd dat dit invloed heeft op alle Universal Links of App Links die u in het verleden hebt gemaakt.

### App-koppeling gebruiken

1. Maak in Adobe Mobile Services een marketingkoppeling die gebruikmaakt van App-koppelingen:

   a. Selecteer de app op de startpagina van Mobile Services en klik op **[!UICONTROL Acquisition]** > **[!UICONTROL Marketing Link Builder]**.

   b. Klik **[!UICONTROL Create New]**.

   c. Selecteer in de **[!UICONTROL Marketing Link Options]** sectie **[!UICONTROL Use Universal Links or App Links]**.

   d. Als u de site-associatiedocumenten hebt geconfigureerd in stap 2, is deze optie standaard geselecteerd.

   Als dat niet het geval is, wordt de **[!UICONTROL Use Universal Links or App Links]** optie uitgeschakeld en **[!UICONTROL Use Interstitials]** standaard geselecteerd.

   e. Als deze optie **[!UICONTROL Use Universal Links or App Links]** is geselecteerd, wordt het **[!UICONTROL Custom Path]** veld weergegeven.

   Hierdoor kunnen gebruikers het URL-pad na het domein definiëren met elke queryparameter. Als u bijvoorbeeld typt `my/app/link?os=6.0`, wordt de volledige URL van de marketingkoppeling `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`.

   f. Klik op het **[!UICONTROL Decisions]** tabblad en configureer de beslissingstructuur.

   g. Als de Android-app is geïnstalleerd, handelt de toepassing de deplink met de bijbehorende logica af.

   De uiteindelijke bestemming fungeert alleen als fallback-case wanneer de app niet is geïnstalleerd. Aangezien de app niet is geïnstalleerd, kan de uiteindelijke bestemming alleen een webkoppeling of app-winkel zijn.

   h.  Klik **[!UICONTROL Save]**.

>[!TIP]
>
>Nadat een Verbinding van de Marketing wordt bewaard, **[!UICONTROL Marketing Links Options]** kan niet worden veranderd. Dit is omdat u niet het gedrag van de Verbindingen van de Marketing wilt veranderen die reeds kunnen zijn verdeeld.

## Marketingskoppelingen gebruiken

U kunt deze marketingkoppelingen nu gebruiken in berichten en andere gebieden in uw app.

>[!IMPORTANT]
>
>Er worden geen tellingen voor bijhouden van klikken weergegeven met Universal Links of App Links en u kunt ook geen interstitiële elementen gebruiken.

