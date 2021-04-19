---
description: U kunt deze informatie gebruiken om een nieuwe app te maken en de belangrijkste maatstaven te configureren;de SDK-opties voor Adobe Analytics en Adobe Audience Manager configureren;aankoop- en id-serviceopties configureren;en het configuratiebestand, de SDK's en ontwikkelaars- en testergereedschappen downloaden.
keywords: mobiel
seo-description: U kunt deze informatie gebruiken om een nieuwe app te maken en de belangrijkste maatstaven te configureren;de SDK-opties voor Adobe Analytics en Adobe Audience Manager configureren;aankoop- en id-serviceopties configureren;en het configuratiebestand, de SDK's en ontwikkelaars- en testergereedschappen downloaden.
seo-title: Een nieuwe app toevoegen
solution: Experience Cloud,Analytics
title: Een nieuwe app toevoegen
topic-fix: Metrics
uuid: 706b5e4d-1318-4a9e-8c69-ffabf51fa02c
exl-id: 30dca517-61ac-495b-aa91-3febd1cb8639
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 0%

---

# Nieuwe app toevoegen{#add-a-new-app}

U kunt deze informatie gebruiken om een nieuwe app te maken en de belangrijkste maatstaven te configureren;u kunt de SDK-opties configureren voor Adobe Analytics en Adobe Audience Manager; aanschaf- en id-serviceopties configureren; en download het configuratiebestand, de SDK&#39;s en ontwikkelaars- en testergereedschappen.

Deze instructies helpen u bij het toevoegen van een nieuwe app en het configureren van Adobe Analytics- en Adobe Audience Manager-integratie.

Voordat u uw app kunt configureren, moet u deze toevoegen in de gebruikersinterface van Adobe Mobile Services. Nadat u de app hebt gemaakt, wordt de juiste configuratie gegenereerd en u kunt deze configuratie opgeven voor de ontwikkelaars die de Mobile SDK voor de app implementeren.

1. Meld u aan bij Adobe Mobile Services en voer een van de volgende taken uit:

   * Klik **[!UICONTROL Create New]** om een app te maken.
   * Als u aanvullende toepassingen wilt toevoegen, klikt u op Apps beheren in het navigatiemenu aan de linkerkant en klikt u op **[!UICONTROL Add]**.

      Zie [Aanmelden](/help/using/gs/gs-signin.md) voor meer informatie over aanmelden.

      >[!TIP]
      >
      >Als u bestaande apps wilt beheren, klikt u op Toepassingen beheren in het navigatiemenu aan de linkerkant en klikt u op de toepassing die u wilt wijzigen. U kunt wijzigingen aanbrengen op de pagina App Information.

1. Typ gegevens in de volgende velden:

   **[!UICONTROL Report Suite]**

   Geef de rapportsuite op waarin de rapportgegevens worden verzameld en opgeslagen in Adobe Analytics. Elke app is verbonden met één analytische rapportsuite. Als u toepassingsgegevens naar meerdere rapportenreeksen verzendt, voegt u een nieuwe app voor elke rapportsuite toe. Elke app is verbonden met één analytische rapportsuite. Als u toepassingsgegevens naar meerdere rapportenreeksen verzendt, voegt u een nieuwe app voor elke rapportsuite toe.

   Als u beheerdersrechten voor Analytics hebt gekregen in Adobe Mobile, kunt u een nieuwe rapportsuite maken in Adobe Mobile. Als u een nieuwe rapportsuite wilt maken, selecteert u **[!UICONTROL New Report Suite]** en typt u informatie in de volgende velden:

   * **[!UICONTROL Report Suite ID]**

      Deze id is een unieke identificatie van de rapportsuite in Adobe Analytics. Het bedrijfsvoorvoegsel wordt automatisch aan het begin van de id toegevoegd.

   * **[!UICONTROL Copy Settings From]**

      De variabelen, de gebeurtenissen, de verwerkingsregels, en andere montages worden opstelling in de nieuwe rapportreeks precies zoals zij in deze rapportreeks zijn. Een rapportsuite die in Mobile Services is gemaakt, is alleen offline (of met tijdstempel) beschikbaar als de rapportsuite **[!UICONTROL Copy Settings From]** wordt gebruikt de Mobile App-sjabloon is, of als u een rapportsuite maakt die offline is ingeschakeld.

   * **[!UICONTROL Timezone]**

      Alle rapportdatums bevinden zich in deze tijdzone. Met deze instelling wordt geprobeerd een tijdzone te gebruiken die dicht bij het browsergebruik ligt.

   * **[!UICONTROL Currency]**

      Opbrengsten worden bijgehouden en gerapporteerd als dit type valuta.
   >[!TIP]
   >
   >Als u een virtuele rapportsuite (VRS) wilt gebruiken, raadpleegt u [Virtuele rapportsuite](/help/using/manage-apps/c-mob-vrs.md).

   * **[!UICONTROL Icon]**

      (**Optioneel**) Als u naar een pictogram voor uw app wilt bladeren en dit wilt selecteren, klikt u op **[!UICONTROL Icon]**.

   * **[!UICONTROL Name]**

      (**Optioneel**) Typ een beschrijvende naam voor de app. Met deze naam kunt u snel een app vinden en een betekenisvolle naam kan u helpen snel inzicht te krijgen in het doel en de instellingen van de app.

   * **[!UICONTROL Type]**

      Selecteer een type in de vervolgkeuzelijst. Welke rapporten beschikbaar zijn in het navigatiemenu aan de linkerkant, is afhankelijk van het type app dat u selecteert.

      Hier volgen de beschikbare typen:

      * **[!UICONTROL Standard]**

         U kunt de optie **[!UICONTROL Standard]** geselecteerd laten voor de meeste apps.

      * **[!UICONTROL Publication]**

         U kunt deze optie selecteren als uw app is gemaakt met Adobe Digital Publishing Suite.

      * **[!UICONTROL Game]**

         Deze optie is vergelijkbaar met de optie **[!UICONTROL Standard]**, behalve dat **[!UICONTROL Game]** de terminologie in de rapporten bijwerkt naar termen voor games. Gebruikers worden bijvoorbeeld gewijzigd in spelers. Gamespecifieke rapporten worden automatisch weergegeven voor game-apps.
   * **[!UICONTROL Description]**

      (**Optioneel**) Typ een beschrijving voor de app.



1. Klik **[!UICONTROL Save]** om de nieuwe app toe te voegen.

   Nadat de app is toegevoegd, kunt u op de pagina App Information controleren of er aanvullende opties zijn geconfigureerd. Zie [Toepassingsinstellingen beheren](/help/using/c-manage-app-settings/c-manage-app-settings.md) voor meer informatie.
