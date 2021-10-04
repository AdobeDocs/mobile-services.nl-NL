---
description: U kunt marketingkoppelingen maken of bewerken om deze diep te koppelen aan uw mobiele app of uw website.
keywords: mobiel
solution: Experience Cloud,Analytics
title: Marketingkoppelingen maken of bewerken
topic-fix: Metrics
uuid: 305a8265-38de-4d19-8c79-b3912f5aae7c
exl-id: a9b5c98d-77c1-4a40-96e5-f9e234d55ec5
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 0%

---

# Marketing-koppelingen maken of bewerken{#create-or-edit-marketing-links}

U kunt marketingkoppelingen maken of bewerken om deze diepgaand te koppelen aan uw mobiele app of uw website. Zie [Universele koppelingen en Android-toepassingskoppelingen toepassen](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md) voor meer informatie.

1. Vouw **[!UICONTROL Acquisition]** in het navigatievenster aan de linkerkant van uw app uit en klik op **[!UICONTROL Marketing Link Builder]**.
1. Voer een van de volgende taken uit:

   * Als u een marketingkoppeling wilt maken, klikt u op **[!UICONTROL Create New]**.
   * Als u een koppeling wilt bewerken, klikt u op de naam van de koppeling in de kolom **[!UICONTROL Title]**.

1. Typ gegevens in de volgende velden:

   * **[!UICONTROL Marketing Link Name]**:

      (**Required**) specificeer een beschrijvende naam voor uw Verbinding van de Marketing. De naam wordt alleen weergegeven op de pagina Marketing Links in de gebruikersinterface van Adobe Mobile Services. Een beschrijvende naam helpt u of anderen in uw organisatie snel een specifieke koppeling te vinden en kan inzicht verschaffen in het doel ervan.

   * **[!UICONTROL Unique Tracking Code]**:

      (**Required**) specificeer de gewenste het volgen code of klik (![produceer pictogram](assets/icon_generate.png) om een nieuwe het volgen code tot stand te brengen. U kunt rapporten weergeven waarin gedetailleerd gebruik wordt gemaakt van de trackingcode.

   * **[!UICONTROL Add Tracking Context Data]**:

      (**Optioneel**) Klik op het pictogram **[!UICONTROL +]** en typ de relevante informatie om uw campagne bij te houden met gebruik van contextgegevens. Selecteer in de vervolgkeuzelijst **[!UICONTROL Custom Context Data]** een vooraf ingestelde tag of een van uw eigen tags. De gegevens van de context worden gebruikt voor het melden wanneer de Verbinding van de Marketing wordt opgesteld.

      De volgende labels met voorinstellingen zijn beschikbaar:

      * **Aangepaste**
contextgegevensGeef de sleutel en waarde op. Als u aangepaste contextgegevens toevoegt, moet u een verwerkingsregel maken. Zie [Overzicht van verwerkingsregels](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) in de documentatie van Adobe Analytics voor meer informatie.

      * ****
SourceSpecify the original reference rer, such as &quot;newsletter&quot; or &quot;homepage&quot;.

      * ****
MediumGeef het marketingmedium op, bijvoorbeeld &#39;&#39;banner&#39;&#39; of &#39;&#39;email&#39;&#39;.

      * ****
InhoudGeef de naam of id van de advertentie op met de koppeling.

      * ****
TermGeef betaalde voorwaarden of andere zoektermen voor de advertentie op.
1. Klik op **[!UICONTROL Save]**.
1. Typ gegevens in de volgende velden:

   * **(Vereist)** Geef  **[!UICONTROL Fallback URL]** in de URL op waarnaar gebruikers worden omgeleid wanneer een doel niet kan worden gevonden (bijvoorbeeld als de gebruiker zich op een bureaublad of een ander platform bevindt dat niet overeenkomt met een doelregel).
   * Selecteer **[!UICONTROL Interstitials]** of **[!UICONTROL Universal and App Links]** in **[!UICONTROL Marketing Link Options]**.

      Zie [Interstitials](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) of [Universele koppelingen en Android-toepassingskoppelingen toepassen](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md) voor meer informatie.

   * **(Voorwaardelijk)** Als deze optie  **[!UICONTROL Universal or App Links]** is geselecteerd, kunnen gebruikers in  **[!UICONTROL Custom Path]** het domein het URL-pad na het domein definiëren met elke queryparameter. Zie [Universele koppelingen en Android-toepassingskoppelingen toepassen](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md) voor meer informatie.

1. Klik **[!UICONTROL Edit Deep Link Interstitial]** en vorm de verbinding.

   (**Optioneel**) Als er meerdere doelen zijn, kunnen gebruikers worden gerouteerd, afhankelijk van het feit of ze een mobiele toepassing hebben geïnstalleerd. Als de app is geïnstalleerd, wordt een tijdelijke bestemmingspagina weergegeven.

   Zie [Interstitials](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) voor meer informatie.

1. Klik **[!UICONTROL Save]** en klik **[!UICONTROL Next]**.
1. In de pagina van de Bestemming, vorm de verbinding.

   1. Klik op het pictogram **[!UICONTROL Decision]** (![beslissingspictogram](assets/icon_decision.png)) en selecteer een van de volgende beslissingslocaties:

      * **[!UICONTROL Add Decision]**
      * **[!UICONTROL Add Path]**
   1. Als u **[!UICONTROL Add Decision]** selecteerde, selecteer één van de volgende besluittypes:

      * **[!UICONTROL Operating Decision]**

         Tot de ondersteunde besturingssystemen behoren iOS, Android, AMX enzovoort.

      * **[!UICONTROL Device Type]**

         Tot de apparaattypen behoren apparaten zoals desktops, lezers, spelconsoles, mobiele telefoons, set top boxes enzovoort.
   1. Klik op het pictogram **[!UICONTROL Destination]** ( ![vierkant pictogram](assets/icon_square.png)) en selecteer een van de volgende doeltypen:

      * **[!UICONTROL App Store]**
      * **[!UICONTROL Web Link]**
      * **[!UICONTROL App Deep Link]**
      * **[!UICONTROL Hybrid Link]**

      >[!TIP]
      >
      >Wanneer u het doeltype **[!UICONTROL Web Link]** gebruikt met een koppeling naar de App Store, wordt de overname niet bijgehouden. Om verwervingen te volgen, gebruik **[!UICONTROL App Store]** bestemmingstype.

      Zie [Een nieuwe koppelingsbestemming maken](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md) voor meer informatie.




1. Om de Verbinding van de Marketing te bewaren, klik ![elipses](assets/icon_elipses.png) en dan **[!UICONTROL Save]**.
