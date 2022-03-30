---
description: Het is belangrijk dat u koppelingen maakt in apps en websites om de gebruikerservaring te behouden. Leer hoe Universal en App Link werken en hoe verschillend ze zijn.
solution: Experience Cloud Services,Analytics
title: Handleiding voor Universal Links en App Links
topic-fix: Metrics
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
exl-id: 6613189f-7a14-4066-89e9-996d4fe7f128
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 0%

---

# Universele koppelingen vs. App-koppelingen: Hoe werken ze? {#universal-links-and-app-links}

Met Universal Links (iOS) en App Links (Android) kunt u verbinding maken met diepe koppelingen in uw iOS- of Android-apps.

>[!IMPORTANT]
>
>Vanaf iOS 9.2 wordt deep linking niet ondersteund. U moet Apple Universal Links gebruiken voor een diepe koppeling naar uw app of website.

## Universele koppelingen {#section_F8147944679A42E59CF4FD8814E5EF12}

Met Universal Links kunt u verbinding maken met diepe koppelingen in uw iOS-app. Deze koppelingen worden ondersteund in iOS 9.2 of hoger. Wanneer u toegang hebt tot een Universal Link, stuurt iOS de koppeling rechtstreeks naar de koppeling in uw app. Als uw app niet is geïnstalleerd, wordt in plaats daarvan een URL voor uw website in een browser geopend. Voor meer informatie over Universal Links raadpleegt u [Universele koppelingen ondersteunen](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html).

## Toepassingskoppelingen

Met App-koppelingen kunt u verbinding maken met diepe koppelingen in uw Android-app. Deze koppelingen worden ondersteund in Android 6.0 of hoger. Wanneer een App-koppeling wordt geopend, stuurt Android de koppeling rechtstreeks naar de koppeling in uw app. Als uw app niet is geïnstalleerd, wordt in plaats daarvan een URL voor uw website in een browser geopend. Zie voor meer informatie over App-koppelingen de [Android-toepassingskoppelingen afhandelen](https://developer.android.com/training/app-links/index.html).

## Creeer een Verbinding van de Marketing door een Universele of Verbinding van de App te gebruiken {#section_609ADEFFB9B441C4A8C45E936D0DC859}

U kunt een Marketing Link tot stand brengen die een Universele Verbinding of een Verbinding van de App gebruikt.

### Een Universal Link configureren

1. Ga naar [Universele koppelingen in Apple afhandelen](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links).

2. Stel in Adobe Mobile Services de site-associatiedocumenten in:

   a. Selecteer op de homepage van Mobile Services de app waarvoor u Universal Links wilt instellen.

   b. Klikken **[!UICONTROL Manage App Settings]**.

   c. Zorg ervoor dat de iOS-app die de Universal Links afhandelt, is toegevoegd aan de **[!UICONTROL Add App Store Apps]** sectie.

   >[!TIP]
   >
   >Als de **[!UICONTROL Add App Store Apps]** niet wordt weergegeven, klikt u op de knop **[!UICONTROL Add App Store App]** koppeling.

   d. In de **[!UICONTROL Universal Links and App Links Options]** selecteert u een iOS-toepassing en typt u de toepassings-id.

   f. Klikken **[!UICONTROL Save]**.

   U moet ten minste één iOS-toepassingsselectie en één toepassings-id opgeven, anders ontvangt u een fout.

   >[!IMPORTANT]
   >
   >U kunt de documenten bijwerken door op Bijwerken te klikken in de sectie Opties voor Universal-koppelingen en App-koppelingen. Wanneer u echter op **[!UICONTROL Update]**, wordt u gewaarschuwd dat dit van invloed is op alle Universal Links of App Links die u in het verleden hebt gemaakt.

### Een Universal Link gebruiken

1. In de Diensten van Adobe Mobile, creeer een Verbinding van de Marketing die Universele Verbindingen gebruikt:

   a. Selecteer de app op de homepage van Mobile Services en klik op **[!UICONTROL Acquisition]** > **[!UICONTROL Marketing Link Builder]**.

   b. Klikken **[!UICONTROL Create New]**.

   c. Onder **[!UICONTROL Marketing Link Options]**, selecteert u **[!UICONTROL Use Universal Links or App Links]**.

   d. Als u de site-koppelingsdocumenten hebt geconfigureerd in het dialoogvenster *Site-associatiedocumenten instellen in Adobe Mobile Services* in de bovenstaande sectie is deze optie standaard geselecteerd.

   Als u de documenten niet hebt geconfigureerd, **[!UICONTROL Use Universal Links or App Links]** optie is uitgeschakeld en **[!UICONTROL Use Interstitials]** is standaard geselecteerd.

   e. Als de **[!UICONTROL Use Universal Links or App Links]** is geselecteerd, wordt de **[!UICONTROL Custom Path]** wordt weergegeven.

   Hierdoor kunnen gebruikers het URL-pad na het domein definiëren met elke queryparameter. Als u bijvoorbeeld `my/universal/link?os=9.2`, wordt de volledige URL van de marketinglink `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`.

   f. Klik op de knop **[!UICONTROL Decisions]** en configureer de beslissingstructuur.

   h. Als de iOS-app is geïnstalleerd, handelt de toepassing de koppeling met de bijbehorende logica af. De uiteindelijke bestemming fungeert alleen als fallback wanneer de app niet is geïnstalleerd. Aangezien de app niet is geïnstalleerd, kan de uiteindelijke bestemming alleen een webkoppeling of app-winkel zijn.

   i. Klikken **[!UICONTROL Save]**.

>[!TIP]
>
>Als een marketingkoppeling eenmaal is opgeslagen, kunnen de opties voor marketingkoppelingen niet meer worden gewijzigd. Dit is omdat u niet het gedrag van de Verbindingen van de Marketing wilt veranderen die reeds kunnen zijn verdeeld.


### Een toepassingskoppeling configureren

1. Ga naar om App-koppelingen in te stellen in uw Android-app naar [Android-toepassingskoppelingen toevoegen](https://developer.android.com/studio/write/app-link-indexing).

1. Stel in Adobe Mobile Services de site-associatiedocumenten in:

   a. Selecteer op de startpagina van Mobile Services de app waarvoor u App Links wilt instellen.

   b. Klikken **[!UICONTROL Manage App Settings]**.

   c. Zorg ervoor dat de Android-app die Universal Links of App Links afhandelt, is toegevoegd aan de **[!UICONTROL Add App Store Apps]** sectie.

   >[!TIP]
   >
   >Als deze sectie niet wordt weergegeven, klikt u op de knop **[!UICONTROL Add App Store App]** koppeling.

   d. Naar de **[!UICONTROL Universal Links and App Links Options]** sectie.

   e. Klik op de knop **[!UICONTROL App Links (Android)]** tab.

   f. Selecteer een Android-toepassing en typ een vingerafdruk van het SHA-256-certificaat.

   g. Klikken **[!UICONTROL Save]**.

   U moet ten minste één selectie voor de Android-app en één SHA-256-certificaat opgeven, anders ontvangt u een fout.

   >[!IMPORTANT]
   >
   >U kunt de documenten bijwerken door op **[!UICONTROL Update]** van de **[!UICONTROL Universal Links and App Links Options]** sectie. Wanneer u echter op **[!UICONTROL Update]**, wordt u gewaarschuwd dat dit van invloed is op alle Universal Links of App Links die u in het verleden hebt gemaakt.

### App-koppeling gebruiken

1. In de Diensten van Adobe Mobile, creeer een Verbinding van de Marketing die de Verbindingen van de Toepassing gebruikt:

   a. Selecteer de app op de homepage van Mobile Services en klik op **[!UICONTROL Acquisition]** > **[!UICONTROL Marketing Link Builder]**.

   b. Klikken **[!UICONTROL Create New]**.

   c. In de **[!UICONTROL Marketing Link Options]** sectie, selecteert u **[!UICONTROL Use Universal Links or App Links]**.

   d. Als u de site-associatiedocumenten hebt geconfigureerd in stap 2, is deze optie standaard geselecteerd.

   Zo niet, dan **[!UICONTROL Use Universal Links or App Links]** deze optie is uitgeschakeld, en **[!UICONTROL Use Interstitials]** is standaard geselecteerd.

   e. Indien **[!UICONTROL Use Universal Links or App Links]** is geselecteerd, **[!UICONTROL Custom Path]** wordt weergegeven.

   Hierdoor kunnen gebruikers het URL-pad na het domein definiëren met elke queryparameter. Als u bijvoorbeeld `my/app/link?os=6.0`, wordt de volledige URL van de marketinglink `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`.

   f. Klik op de knop **[!UICONTROL Decisions]** en configureer de beslissingstructuur.

   g. Als de Android-app is geïnstalleerd, handelt de toepassing de deplink met de bijbehorende logica af.

   De uiteindelijke bestemming fungeert alleen als fallback-case wanneer de app niet is geïnstalleerd. Aangezien de app niet is geïnstalleerd, kan de uiteindelijke bestemming alleen een webkoppeling of app-winkel zijn.

   h. Klikken **[!UICONTROL Save]**.

>[!TIP]
>
>Nadat een marketingkoppeling is opgeslagen, wordt de **[!UICONTROL Marketing Links Options]** kan niet worden gewijzigd. Dit is omdat u niet het gedrag van de Verbindingen van de Marketing wilt veranderen die reeds kunnen zijn verdeeld.

## Marketingskoppelingen gebruiken

U kunt deze marketingkoppelingen nu gebruiken in berichten en andere gebieden in uw app.

>[!IMPORTANT]
>
>Er worden geen tellingen voor bijhouden van klikken weergegeven met Universal Links of App Links en u kunt ook geen interstitiële elementen gebruiken.
