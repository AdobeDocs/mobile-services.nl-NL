---
description: U kunt deze informatie gebruiken om een nieuwe app te maken en de belangrijkste maatstaven ervan te configureren;de SDK-opties configureren voor Adobe Analytics en Adobe Audience Manager;aankoop- en id-serviceopties configureren en het configuratiebestand, de SDK's en ontwikkelaars- en testergereedschappen downloaden.
keywords: mobile
seo-description: U kunt deze informatie gebruiken om een nieuwe app te maken en de belangrijkste maatstaven ervan te configureren;de SDK-opties configureren voor Adobe Analytics en Adobe Audience Manager;aankoop- en id-serviceopties configureren en het configuratiebestand, de SDK's en ontwikkelaars- en testergereedschappen downloaden.
seo-title: Een nieuwe app toevoegen
solution: Marketing Cloud,Analytics
title: Een nieuwe app toevoegen
topic: Metrics
uuid: 706b5e4d-1318-4a9e-8c69-ffabf51fa02c
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Een nieuwe app toevoegen{#add-a-new-app}

U kunt deze informatie gebruiken om een nieuwe app te maken en de belangrijkste maatstaven te configureren; de SDK-opties configureren voor Adobe Analytics en Adobe Audience Manager; aanschaf- en id-serviceopties configureren; en download het configuratiebestand, de SDK&#39;s en ontwikkelaars- en testergereedschappen.

Met deze instructies kunt u een nieuwe app toevoegen en de integratie van Adobe Analytics en Adobe Audience Manager configureren.

Voordat u uw app kunt configureren, moet u deze toevoegen in de gebruikersinterface van Adobe Mobile Services. Nadat u de app hebt gemaakt, wordt de juiste configuratie gegenereerd en u kunt deze configuratie opgeven voor de ontwikkelaars die de Mobile SDK voor de app implementeren.

1. Meld u aan bij Adobe Mobile Services en voer een van de volgende taken uit:

   * Klik **[!UICONTROL Create New]** om een app te maken.
   * Als u aanvullende toepassingen wilt toevoegen, klikt u op Toepassingen beheren in het navigatiemenu aan de linkerkant en klikt u **[!UICONTROL Add]** op Toepassingen beheren.

      Zie [Aanmelden](/help/using/gs/gs-signin.md)voor meer informatie over aanmelden.

      >[!TIP]
      >
      >Als u bestaande apps wilt beheren, klikt u op Toepassingen beheren in het navigatiemenu aan de linkerkant en klikt u op de toepassing die u wilt wijzigen. U kunt wijzigingen aanbrengen op de pagina App Information.

1. Typ gegevens in de volgende velden:

   **[!UICONTROL Report Suite]**

   Geef de rapportsuite op waarin de rapportgegevens worden verzameld en opgeslagen in Adobe Analytics. Elke app is verbonden met één analytische rapportsuite. Als u toepassingsgegevens naar meerdere rapportenreeksen verzendt, voegt u een nieuwe app voor elke rapportsuite toe. Elke app is verbonden met één analytische rapportsuite. Als u toepassingsgegevens naar meerdere rapportenreeksen verzendt, voegt u een nieuwe app voor elke rapportsuite toe.

   Als u beheerdersrechten voor Analytics hebt gekregen in Adobe Mobile, kunt u een nieuwe rapportsuite maken in Adobe Mobile. Als u een nieuwe rapportsuite wilt maken, selecteert **[!UICONTROL New Report Suite]** en typt u gegevens in de volgende velden:

   * **[!UICONTROL Report Suite ID]**

      Deze id is een unieke identificatie van de rapportsuite in Adobe Analytics. Het bedrijfsvoorvoegsel wordt automatisch aan het begin van de id toegevoegd.

   * **[!UICONTROL Copy Settings From]**

      De variabelen, de gebeurtenissen, de verwerkingsregels, en andere montages worden opstelling in de nieuwe rapportreeks precies zoals zij in deze rapportreeks zijn. Een rapportsuite die in Mobile Services is gemaakt, is alleen offline (of met tijdstempel) beschikbaar als de gebruikte **[!UICONTROL Copy Settings From]** rapportsuite de Mobile App-sjabloon was of als u een rapportsuite maakt die offline is ingeschakeld.

   * **[!UICONTROL Timezone]**

      Alle rapportdatums bevinden zich in deze tijdzone. Met deze instelling wordt geprobeerd een tijdzone te gebruiken die dicht bij het browsergebruik ligt.

   * **[!UICONTROL Currency]**

      Opbrengsten worden bijgehouden en gerapporteerd als dit type valuta.
   >[!TIP]
   >
   >Zie [Virtuele rapportsets](/help/using/manage-apps/c-mob-vrs.md)voor informatie over het gebruik van een virtuele rapporteringssuite (VRS).

   * **[!UICONTROL Icon]**

      (**Optioneel**) Als u naar een pictogram voor uw app wilt bladeren en dit wilt selecteren, klikt u op **[!UICONTROL Icon]**.

   * **[!UICONTROL Name]**

      (**Optioneel**) Typ een beschrijvende naam voor de app. Met deze naam kunt u snel een app vinden en een betekenisvolle naam kan u helpen snel inzicht te krijgen in het doel en de instellingen van de app.

   * **[!UICONTROL Type]**

      Selecteer een type in de vervolgkeuzelijst. Welke rapporten beschikbaar zijn in het navigatiemenu aan de linkerkant, is afhankelijk van het type app dat u selecteert.

      Hier volgen de beschikbare typen:

      * **[!UICONTROL Standard]**

         U kunt de optie **[!UICONTROL Standard}** geselecteerd laten voor de meeste toepassingen.

      * **[!UICONTROL Publication]**

         U kunt deze optie selecteren als uw app is gemaakt met Adobe Digital Publishing Suite.

      * **[!UICONTROL Game]**

         Deze optie lijkt op de **[!UICONTROL Standard]** **[!UICONTROL Game]** optie, behalve dat de terminologie die in de rapporten wordt gebruikt aan termijnen voor spelen wordt bijgewerkt. Gebruikers worden bijvoorbeeld gewijzigd in spelers. Gamespecifieke rapporten worden automatisch weergegeven voor game-apps.
   * **[!UICONTROL Description]**

      (**Optioneel**) Typ een beschrijving voor de app.



1. Klik **[!UICONTROL Save]** om de nieuwe app toe te voegen.

   Nadat de app is toegevoegd, kunt u op de pagina App Information controleren of er aanvullende opties zijn geconfigureerd. Zie Toepassingsinstellingen [beheren voor meer informatie](/help/using/c-manage-app-settings/c-manage-app-settings.md).
