---
description: In het rapport Paden weergeven, dat is gebaseerd op padanalyse, wordt een paddiagram weergegeven dat de paden vertegenwoordigt die tussen frames in de app zijn gemaakt.
keywords: mobiel
seo-description: In het rapport Paden weergeven, dat is gebaseerd op padanalyse, wordt een paddiagram weergegeven dat de paden vertegenwoordigt die tussen frames in de app zijn gemaakt.
seo-title: Rapport Paden weergeven
solution: Experience Cloud,Analytics
title: Rapport Paden weergeven
topic-fix: Reports,Metrics
uuid: bc73edce-0cc0-4349-9a48-e0a40cbe1b67
exl-id: 475dbe01-fa4d-433c-ac77-68f2a6972c0c
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# Rapport Paden weergeven {#view-paths}

In het **[!UICONTROL View Paths]**-rapport, dat is gebaseerd op padanalyse, wordt een paddiagram weergegeven dat de paden vertegenwoordigt die tussen de frames in de app zijn gemaakt.

>[!TIP]
>
>De **[!UICONTROL View Paths]** en **[!UICONTROL View Action]** rapporten zijn gelijkaardig omdat allebei het plakrapporten zijn. Met het **[!UICONTROL View Paths]**-rapport kunt u zien hoe gebruikers van het ene scherm naar het andere in uw app navigeren. In het **[!UICONTROL View Actions]**-rapport wordt de volgorde van handelingen (gebeurtenissen zoals klikken, selecties, vergroten/verkleinen, enzovoort) weergegeven die gebruikers in uw app uitvoeren. U kunt een trechterrapport gebruiken om navigatie en acties in één rapport te combineren. Zie [Trechter](/help/using/usage/reports-funnel.md) voor meer informatie.

![paden weergeven](assets/view_paths.png)

Elk knooppunt in de vorm van een vak staat voor een staat in de paden van de gebruiker via een app. In de bovenstaande illustratie geeft het bovenste knooppunt bijvoorbeeld het aantal gebruikers aan dat de app heeft gestart en naar de hoofdweergave is genavigeerd.

Wanneer u op een knooppunt klikt om de aanvullende opties voor het wijzigen van het diagram op te geven, worden extra opties weergegeven, zoals **[!UICONTROL Focus]** of **[!UICONTROL Expand]**. Wanneer u bijvoorbeeld op de status **[!UICONTROL MainView]** in het bovenste knooppunt klikt, worden de pictogrammen **[!UICONTROL Focus]** en **[!UICONTROL Expand]** weergegeven.

Als u de weergave wilt uitvouwen, klikt u op het pictogram **[!UICONTROL +]** om de extra paden weer te geven die naar het knooppunt komen of er van uitgaan. In de onderstaande afbeelding wordt met frame 1 de app gestart, met frame 2 wordt de hoofdpagina van de app weergegeven en met frame 3 zijn de volgende paden opgenomen die gebruikers hebben gekozen:

* Navigeren naar de camerarol
* navigeren naar de itemkiezer
* naar de camera navigeren
* navigeren naar de pagina met iteminfo

![](assets/view_paths_expand.png)

Klik ![focuspictogram](assets/icon_focus.png) om de knoop te isoleren en de wegen te tonen die in en uit de geselecteerde knoop komen. In de onderstaande afbeelding zijn de volgende paden voor gebruikers weergegeven die de hoofdweergave van de app bekeken:

* iteminfo
* itemkiezer
* Camerarol
* Camera

![padfocus weergeven](assets/view_paths_focus.png)

U kunt meerdere knooppunten activeren of uitbreiden voor een gedetailleerde weergave van de paden die gebruikers in uw app innemen. Bijvoorbeeld:

![weergavepad meerdere](assets/view_paths_mult.png)

U kunt de volgende opties voor dit rapport vormen:

* **[!UICONTROL Time Period]**
Klik op het  **[!UICONTROL Calendar]** pictogram om een aangepaste periode te selecteren of om een vooraf ingestelde tijdsperiode te selecteren in de vervolgkeuzelijst.
* **[!UICONTROL Customize]**
Pas uw rapporten aan door de  **[!UICONTROL Show By]** opties te veranderen, metriek en filters toe te voegen, extra reeksen (metriek) toe te voegen, en meer. Zie [Rapporten aanpassen](/help/using/usage/reports-customize/reports-customize.md) voor meer informatie.
* **[!UICONTROL Filter]**
Klik  **[!UICONTROL Filter]** om een filter te creëren dat verschillende rapporten overspant om te zien hoe een segment over alle mobiele rapporten presteert. Met een kleverig filter kunt u een filter definiëren dat wordt toegepast op alle rapporten die geen tekenen bevatten. Zie [Filter toevoegen](/help/using/usage/reports-customize/t-sticky-filter.md) voor meer informatie.
* **[!UICONTROL Download]**
Klik  **[!UICONTROL PDF]** of  **[!UICONTROL CSV]** om documenten te downloaden of te openen en deze te delen met gebruikers die geen toegang hebben tot Mobile Services of om het bestand in presentaties te gebruiken.
