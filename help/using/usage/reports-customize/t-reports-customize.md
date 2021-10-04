---
description: Deze informatie helpt u de ingebouwde rapporten aan te passen door extra filters (segmenten) toe te voegen.
keywords: mobiel
solution: Experience Cloud,Analytics
title: Filters toevoegen aan rapporten
topic-fix: Reports,Metrics
uuid: 19c395cc-2e07-4588-825b-f2f8b10a87c1
exl-id: eb0589e9-668e-42d7-8f7a-00d7f0a2e3ff
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Filters toevoegen aan rapporten{#add-filters-to-reports}

Deze informatie helpt u de ingebouwde rapporten aan te passen door extra filters (segmenten) toe te voegen.

>[!IMPORTANT]
>
>Metrische gegevens voor mobiele apps zijn ook beschikbaar in marketingrapporten en -analyses, ad-hocanalyses, gegevensopslagruimten en andere analytische rapportageinterfaces. Als een afbraak of rapporttype niet beschikbaar in Adobe Mobiel is, kan het worden geproduceerd door een verschillende rapporteringsinterface te gebruiken.

In dit voorbeeld, zullen wij het **[!UICONTROL Users & Sessions]** rapport aanpassen, maar de instructies zijn op om het even welk rapport van toepassing.

1. Open uw app en klik op **[!UICONTROL Usage]** > **[!UICONTROL Users & Sessions]**.

   ![](assets/customize1.png)

   Dit rapport bevat een volledige overloopweergave van gebruikers van de app. Metrische gegevens voor zowel de iOS- als de Android-versie van deze app worden echter verzameld in dezelfde rapportsuite. Wij kunnen gebruikers door mobiel OS segmenteren door een douanefilter aan de Gebruikers metrisch toe te voegen.

1. Klik op **[!UICONTROL Customize]**.

   ![](assets/customize2.png)

1. Klik onder **[!UICONTROL Users]** op **[!UICONTROL Add Filter]** en klik op **[!UICONTROL Add Rule]**.

1. Selecteer **[!UICONTROL Operating Systems]**, en van de drop-down lijst, en selecteer **[!UICONTROL iOS]**.

   ![](assets/customize3.png)

   Als u Android als filter wilt toevoegen, moet u deze stap herhalen.

1. Klik **[!UICONTROL And]**, selecteer **[!UICONTROL Operating Systems]** van de drop-down lijst, en selecteer **[!UICONTROL Android]**.

   De filters moeten er nu als volgt uitzien:

   ![](assets/customize4.png)

1. Klik op **[!UICONTROL Update]**.
1. Klik op **[!UICONTROL Run]** om het rapport opnieuw te genereren.

   In dit rapport worden nu gebruikers weergegeven die zijn opgesplitst naar besturingssysteem. De rapporttitel is gewijzigd en komt overeen met de filters die op het rapport zijn toegepast.

   ![](assets/customize5.png)

   U kunt dit rapport verder aanpassen. Vanuit iOS 8.3 kunt u de metrische gegevens Eerste starten toevoegen met een versiefilter van het besturingssysteem iOS 8.3 om te zien hoeveel iOS 8.3-klanten hun apps hebben geüpgraded en een eerste keer hebben gestart.
1. Klik onder **[!UICONTROL First Launches]** op **[!UICONTROL Add Filter]**, klik op **[!UICONTROL Add Rule]**, selecteer **[!UICONTROL Operating Systems]** in de vervolgkeuzelijst en selecteer **[!UICONTROL iOS]**.
1. Klik **[!UICONTROL And]**, selecteer **[!UICONTROL Operating System Versions]** van de drop-down lijst, en selecteer **[!UICONTROL iOS 8.3]**.

   De filters moeten er nu als volgt uitzien:

   ![](assets/customize6.png)

1. Klik op **[!UICONTROL Update]** en **[!UICONTROL Run]**.

   In dit rapport worden nu gebruikers met iOS 8.3 getoond die de app voor het eerst hebben gestart.

   ![](assets/customize7.png)

   Neem wat tijd om de verschillende opties in het menu van de rapportaanpassing te testen, en ervoor te zorgen dat u referentie uw favorieten. De rapport-URL&#39;s in Adobe Mobile zijn functioneel en kunnen worden gemaild of toegevoegd aan uw favorieten.
