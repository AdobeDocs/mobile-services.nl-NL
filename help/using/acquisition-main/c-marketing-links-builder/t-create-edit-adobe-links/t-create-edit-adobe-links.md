---
description: U kunt marketingkoppelingen maken of bewerken om deze diep te koppelen aan uw mobiele app of uw website.
keywords: mobiel
solution: Experience Cloud Services,Analytics
title: Marketingkoppelingen maken of bewerken
topic-fix: Metrics
uuid: 305a8265-38de-4d19-8c79-b3912f5aae7c
exl-id: a9b5c98d-77c1-4a40-96e5-f9e234d55ec5
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 0%

---

# Marketing-koppelingen maken of bewerken{#create-or-edit-marketing-links}

U kunt marketingkoppelingen maken of bewerken om deze diepgaand te koppelen aan uw mobiele app of uw website. Zie voor meer informatie [Koppelingen naar Apple Universal Links en Android App](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. Vouw in uw app in het navigatievenster aan de linkerkant uit **[!UICONTROL Acquisition]** en klik op **[!UICONTROL Marketing Link Builder]**.
1. Voer een van de volgende taken uit:

   * Als u een marketingkoppeling wilt maken, klikt u op **[!UICONTROL Create New]**.
   * Als u een koppeling wilt bewerken, klikt u op de naam van de koppeling in het dialoogvenster **[!UICONTROL Title]** kolom.

1. Typ gegevens in de volgende velden:

   * **[!UICONTROL Marketing Link Name]**:

      (**Vereist**) Geef een beschrijvende naam op voor uw marketingkoppeling. De naam wordt alleen weergegeven op de pagina Marketing Links in de gebruikersinterface van Adobe Mobile Services. Een beschrijvende naam helpt u of anderen in uw organisatie snel een specifieke koppeling te vinden en kan inzicht verschaffen in het doel ervan.

   * **[!UICONTROL Unique Tracking Code]**:

      (**Vereist**) Geef de gewenste trackingcode op of klik (![pictogram genereren](assets/icon_generate.png) om een nieuwe trackingcode te maken. U kunt rapporten weergeven waarin gedetailleerd gebruik wordt gemaakt van de trackingcode.

   * **[!UICONTROL Add Tracking Context Data]**:

      (**Optioneel**) Klik op de knop **[!UICONTROL +]** en typ de relevante informatie om uw campagne bij te houden met gebruik van contextgegevens. In de **[!UICONTROL Custom Context Data]** Selecteer een vooraf ingestelde tag of een van uw eigen tags. De gegevens van de context worden gebruikt voor het melden wanneer de Verbinding van de Marketing wordt opgesteld.

      De volgende labels met voorinstellingen zijn beschikbaar:

      * **Aangepaste contextgegevens**
Geef de sleutel en waarde op. Als u aangepaste contextgegevens toevoegt, moet u een verwerkingsregel maken. Zie voor meer informatie [Overzicht van verwerkingsregels](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) in de documentatie van Adobe Analytics.

      * **Bron**
Geef de oorspronkelijke referentie op, bijvoorbeeld &quot;nieuwsbrief&quot; of &quot;homepage&quot;.

      * **Normaal**
Geef het marketingmedium op, bijvoorbeeld &#39;&#39;banner&#39;&#39; of &#39;&#39;email&#39;&#39;.

      * **Inhoud**
Geef de naam of id van de advertentie op met de koppeling.

      * **Term**
Geef betaalde voorwaarden of andere zoektermen op voor de advertentie.
1. Klik op **[!UICONTROL Save]**.
1. Typ gegevens in de volgende velden:

   * **(Vereist)** In **[!UICONTROL Fallback URL]**, geeft u de URL op waarnaar gebruikers worden omgeleid wanneer een doel niet kan worden gevonden (bijvoorbeeld als de gebruiker zich op een bureaublad of een ander platform bevindt dat niet overeenkomt met een doelregel).
   * In **[!UICONTROL Marketing Link Options]**, selecteert u **[!UICONTROL Interstitials]** of **[!UICONTROL Universal and App Links]**.

      Zie voor meer informatie [Interstitiële](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) of [Koppelingen naar Apple Universal Links en Android App](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

   * **(Voorwaardelijk)** Indien **[!UICONTROL Universal or App Links]** is geselecteerd, in **[!UICONTROL Custom Path]** kunnen gebruikers het URL-pad na het domein definiëren met een willekeurige queryparameter. Zie voor meer informatie [Koppelingen naar Apple Universal Links en Android App](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. Klikken **[!UICONTROL Edit Deep Link Interstitial]** en configureer de koppeling.

   (**Optioneel**) Wanneer er meerdere doelen zijn, kunnen gebruikers worden gerouteerd, afhankelijk van het feit of ze een mobiele toepassing hebben geïnstalleerd. Als de app is geïnstalleerd, wordt een tijdelijke bestemmingspagina weergegeven.

   Zie voor meer informatie [Interstitiële](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md).

1. Klikken **[!UICONTROL Save]** en klik op **[!UICONTROL Next]**.
1. In de pagina van de Bestemming, vorm de verbinding.

   1. Klik op de knop **[!UICONTROL Decision]** icon (![beslissingspictogram](assets/icon_decision.png)) en selecteert u een van de volgende beslissingslocaties:

      * **[!UICONTROL Add Decision]**
      * **[!UICONTROL Add Path]**
   1. Als u **[!UICONTROL Add Decision]** selecteert u een van de volgende beslissingstypen:

      * **[!UICONTROL Operating Decision]**

         Tot de ondersteunde besturingssystemen behoren iOS, Android, AMX enzovoort.

      * **[!UICONTROL Device Type]**

         Tot de apparaattypen behoren apparaten zoals desktops, lezers, spelconsoles, mobiele telefoons, set top boxes enzovoort.
   1. Klik op de knop **[!UICONTROL Destination]** icon ( ![vierkant pictogram](assets/icon_square.png) ) en selecteert u een van de volgende doeltypen:

      * **[!UICONTROL App Store]**
      * **[!UICONTROL Web Link]**
      * **[!UICONTROL App Deep Link]**
      * **[!UICONTROL Hybrid Link]**

      >[!TIP]
      >
      >Wanneer u de **[!UICONTROL Web Link]** Het doeltype met een koppeling naar de App Store wordt niet bijgehouden. Als u acquisities wilt bijhouden, gebruikt u de opdracht **[!UICONTROL App Store]** doeltype.

      Zie voor meer informatie [Een nieuw doel voor een koppeling maken](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md).




1. Als u de marketingkoppeling wilt opslaan, klikt u op ![eleggen](assets/icon_elipses.png) en vervolgens **[!UICONTROL Save]**.
