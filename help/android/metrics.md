---
description: Hier volgen de afmetingen en metriek die automatisch door de mobiele bibliotheek kunnen worden gemeten, nadat de levenscyclus is geïmplementeerd, en een koppeling om de gegevens van de levenscyclus problemen op te lossen.
keywords: android;library;mobile;sdk
seo-description: Hier volgen de afmetingen en metriek die automatisch door de mobiele bibliotheek kunnen worden gemeten, nadat de levenscyclus is geïmplementeerd, en een koppeling om de gegevens van de levenscyclus problemen op te lossen.
seo-title: Levenscycluswaarden
solution: Marketing Cloud,Analytics
title: Levenscycluswaarden
topic: Developer and implementation
uuid: a8f3ebac-be3b-4948-82bb-105d46cfff6d
translation-type: tm+mt
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# Levenscycluswaarden{#lifecycle-metrics}

Deze sectie bevat informatie over de metriek en afmetingen die automatisch door de mobiele bibliotheek kunnen worden gemeten nadat de levenscyclus is geïmplementeerd, en een koppeling om de gegevens van de levenscyclus problemen op te lossen. Ga voor meer informatie over probleemoplossing naar [Problemen met levenscyclusgegevens](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html)oplossen.

## Nieuwe release van Adobe Experience Platform Mobile SDK

Op zoek naar informatie en documentatie over de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via het [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga om aan de slag te gaan naar Adobe Experience Platform Launch.
* Ga naar [Github om te zien wat er in de repositories van Experience Platform SDK staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Metrische gegevens en afmetingen van de levenscyclus {#section_78F036C4296F4BA3A47C2044F79C86C1}

Wanneer gevormd, worden de metriek van de levenscyclus verzonden in de parameters van contextgegevens naar Analytics, in parameters aan Doel met elke mbox vraag, en als signaal aan publieksbeheer. Analytics en Target gebruiken dezelfde indeling, terwijl het publieksbeheer voor elke meting een ander voorvoegsel gebruikt.

Voor Analytics, worden de contextgegevens die met elke levenscyclusvolgende vraag worden verzonden automatisch binnen gevangen en gemeld door metrisch of afmeting te gebruiken, en de uitzonderingen worden genoteerd.

### Metrisch

* **Eerste keer starten**

   Wordt geactiveerd bij de eerste run na installatie of herinstallatie.

   * Contextgegevens/doelparameter voor analyse: `a.InstallEvent`
   * Audience Manager-signaal: `c_a_InstallEvent`

* **Upgrades**

   Teweeggebracht bij de eerste looppas na een verbetering of wanneer het versieaantal verandert.

   * Contextgegevens/doelparameter voor analyse: `a.UpgradeEvent`
   * Audience Manager-signaal: `c_a_UpgradeEvent`

* **Dagelijkse deelnemers**

   Wordt geactiveerd wanneer de toepassing op een bepaalde dag wordt gebruikt.

   >[!IMPORTANT]
   >
   >Deze metrisch wordt niet automatisch opgeslagen in metrisch Analytics. U moet een verwerkingsregel maken die een aangepaste gebeurtenis instelt om deze metrische waarde vast te leggen.

   * Contextgegevens/doelparameter voor analyse: `a.DailyEngUserEvent`
   * Audience Manager-signaal: `c_a_DailyEngUserEvent`

* **Maandelijkse deelnemers**

   Wordt geactiveerd wanneer de toepassing tijdens een bepaalde maand wordt gebruikt.

   >[!IMPORTANT]
   >
   >Deze metrisch wordt niet automatisch opgeslagen in metrisch Analytics. U moet een verwerkingsregel maken die een aangepaste gebeurtenis instelt om deze metrische waarde vast te leggen.

   * Contextgegevens/doelparameter voor analyse: `a.MonthlyEngUserEvent`
   * Audience Manager-signaal: `c_a_MonthlyEngUserEvent`

* **Starten**

   Teweeggebracht bij elke looppas, met inbegrip van neerstortingen en installaties. Wordt ook geactiveerd op een hervat vanaf de achtergrond wanneer de time-out van de levenscyclussessie is overschreden.

   >[!IMPORTANT]
   >
   >Deze metrisch wordt niet automatisch opgeslagen in metrisch Analytics. U moet een verwerkingsregel maken die een aangepaste gebeurtenis instelt om deze metrische waarde vast te leggen.

   * Contextgegevens/doelparameter voor analyse: `a.LaunchEvent`
   * Audience Manager-signaal: `c_a_LaunchEvent`

* **Crashes**

   Wordt geactiveerd wanneer de toepassing geen achtergrond heeft voordat deze wordt gesloten. De gebeurtenis wordt verzonden wanneer de toepassing na de crash wordt gestart.  Adobe Mobile-crashrapportage implementeert geen algemene handler voor niet-afgevangen uitzonderingen.

   * Contextgegevens/doelparameter voor analyse: `a.CrashEvent`
   * Audience Manager-signaal: `c_a_CrashEvent`

* **Lengte vorige sessie**

   Meldt het aantal seconden dat een vorige toepassingssessie heeft geduurd, op basis van de duur van de toepassing en op de voorgrond.

   * Contextgegevens/doelparameter voor analyse: `a.PrevSessionLength`
   * Audience Manager-signaal: `c_a_PrevSessionLength`


### Afmetingen

* **Installatiedatum**

   Datum van eerste lancering na installatie. De datumnotatie is MM/DD/YYYY.

   * Contextgegevens/doelparameter voor analyse: `a.InstallDate`
   * Audience Manager: `c_a_InstallDate`

* **Toepassings-id**

   Hiermee slaat u de toepassingsnaam en -versie op in de `[AppName] [BundleVersion]` indeling. Een voorbeeld van deze indeling is `myapp 1.1`.

   * Contextgegevens/doelparameter voor analyse: `a.AppID`
   * Audience Manager: `c_a_AppID`

* **Startnummer**

   Aantal keren dat de toepassing is gestart of van de achtergrond is verwijderd.

   * Contextgegevens/doelparameter voor analyse: `a.Launches`
   * Audience Manager: `c_a_Launches`

* **Dagen sinds eerste gebruik**

   Aantal dagen sinds de eerste run.

   * Contextgegevens/doelparameter voor analyse: `a.DaysSinceFirstUse`
   * Audience Manager: `c_a_DaysSinceFirstUse`

* **Dagen sinds laatste gebruik**

   Aantal dagen sinds laatste gebruik.

   * Contextgegevens/doelparameter voor analyse: `a.DaysSinceLastUse`
   * Audience Manager: `c_a_DaysSinceLastUse`

* **Uur van dag**

   Hiermee wordt het uur gemeten waarop de app is gestart.  Deze metrische waarde gebruikt het 24-uurs numerieke formaat en voor tijd het ontleden gebruikt om piekgebruikstijden te bepalen.

   * Contextgegevens/doelparameter voor analyse: `a.HourOfDay`
   * Audience Manager: `c_a_HourOfDay`

* **Weekdag**

   Aantal dagen in een week waarin de app is gestart.

   * Contextgegevens/doelparameter voor analyse: `a.DayOfWeek`
   * Audience Manager: `c_a_DayOfWeek`

* **Versie besturingssysteem**

   De versie van het besturingssysteem.

   * Contextgegevens/doelparameter voor analyse: `a.OSVersion`
   * Audience Manager: `c_a_OSVersion`

* **Dagen sinds laatste upgrade**

   Aantal dagen sinds het versienummer van de toepassing is gewijzigd.

   >[!IMPORTANT]
   >
   >Deze metrische waarde wordt niet automatisch opgeslagen in een variabele Analytics. U moet een verwerkingsregel maken om deze waarde te kopiëren naar een variabele Analytics voor rapportage.

   * Contextgegevens/doelparameter voor analyse: `a.DaysSinceLastUpgrade`
   * Audience Manager: `c_a_DaysSinceLastUpgrade`

* **Starten sinds laatste upgrade**

   Aantal keren starten nadat het versienummer van de toepassing is gewijzigd.

   >[!IMPORTANT]
   >
   >Deze metrische waarde wordt niet automatisch opgeslagen in een variabele Analytics. U moet een verwerkingsregel maken om deze waarde te kopiëren naar een variabele Analytics voor rapportage.

   * Contextgegevens/doelparameter voor analyse: `a.LaunchesSinceUpgrade`
   * Audience Manager: `c_a_LaunchesSinceUpgrade`

* **Apparaatnaam**

   Hiermee slaat u de apparaatnaam op.

   * Contextgegevens/doelparameter voor analyse: `a.DeviceName`
   * Audience Manager: `c_a_DeviceName`

* **Naam vervoerder**

   Hiermee wordt de naam van de mobiele serviceprovider opgeslagen, zoals opgegeven door het apparaat.  Belangrijk:  Deze metrische waarde wordt niet automatisch opgeslagen in een variabele Analytics. U moet een verwerkingsregel maken om deze waarde te kopiëren naar een variabele Analytics voor rapportage.

   >[!IMPORTANT]
   >
   >Deze metrische waarde wordt niet automatisch opgeslagen in een variabele Analytics. U moet een verwerkingsregel maken om deze waarde te kopiëren naar een variabele Analytics voor rapportage.

   * Contextgegevens/doelparameter voor analyse: `a.CarrierName`
   * Audience Manager: `c_a_CarrierName`

* **Resolutie**

   Breedte x Hoogte in werkelijke pixels.

   * Contextgegevens/doelparameter voor analyse: `a.Resolution`
   * Audience Manager: `c_a_Resolution`

## Extra mobiele meeteenheden en afmetingen {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

De volgende meetwaarden en afmetingen worden in mobiele oplossingsvariabelen vastgelegd met de methode die in de kolom **Beschrijving** wordt vermeld.

### Metrisch

* **Totale tijd van handeling**

   Bevolkt met `trackTimedAction` methoden.

   * Contextgegevens/doelparameter voor analyse: `a.action.time.total`
   * Audience Manager Trait: `c_a_action_time_total`

* **Tijd van handeling in toepassing**

   Bevolkt met `trackTimedAction` methoden.

   * Contextgegevens/doelparameter voor analyse: `a.action.time.inapp`
   * Audience Manager Trait: `c_a_action_time_inapp`

* **Lifetime-waarde (gebeurtenis)**

   Bevolkt met `trackLifetimeValue` methoden.

   * Contextgegevens/doelparameter voor analyse: `a.ltv.amount`
   * Audience Manager Trait: `c_a_ltv_amount`

### Afmetingen

* **Locatie (tot 10 km)**

   Bevolkt met `trackLocation` methoden.

   * Contextgegevens/doelparameters voor analyse:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Manager Traits:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Locatie (tot 100 m)**

   Bevolkt door trackLocation-methoden.

   * Contextgegevens/doelparameters voor analyse:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Manager Traits:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Locatie (tot 1 m)**

   Bevolkt door trackLocation-methoden.

   * Contextgegevens/doelparameters voor analyse:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Manager Traits:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Naam van belangenpunt**

   Wordt gevuld door trackLocation-methoden wanneer het apparaat zich binnen een gedefinieerde POI bevindt.

   * Contextgegevens/doelparameters voor analyse: `a.loc.poi`
   * Audience Manager Trait: `c_a_loc_poi`

* **Afstand tot belangencentrum**

   Wordt gevuld door trackLocation-methoden wanneer het apparaat zich binnen een gedefinieerde POI bevindt.

   * Contextgegevens/doelparameters voor analyse: `a.loc.dist`
   * Audience Manager Trait: `c_a_loc_dist`

* **Lifetime-waarde (conversievariabele)**

   Bevolkt door trackLifetimeValue-methoden.

   * Contextgegevens/doelparameters voor analyse: `a.ltv.amount`
   * Audience Manager Trait: `c_a_ltv_amount`

* **Trackingcode**

   Wordt gevuld door Mobile App Acquisition en wordt automatisch gegenereerd door Adobe Mobile-services.

   * Contextgegevens/doelparameters voor analyse: `a.referrer.campaign.trackingcode`
   * Audience Manager Trait: `c_a_referrer_campaign_trackingcode`

* **Campagne**

   Naam van de campagne, die ook in de campagnevariabele wordt opgeslagen. Bevolkt door Mobile App Acquisition.

   * Contextgegevens/doelparameters voor analyse: `a.referrer.campaign.name`
   * Audience Manager Trait: `c_a_referrer_campaign_name`

* **Campagne-inhoud**

   De naam of id van de inhoud die de koppeling heeft weergegeven. Bevolkt door Mobile App Acquisition.

   * Contextgegevens/doelparameters voor analyse: `a.referrer.campaign.content`
   * Audience Manager Trait: `c_a_referrer_campaign_content`

* **Campagne normaal**

   Marketingmedium, zoals een banner of e-mail. Bevolkt door Mobile App Acquisition.

   * Contextgegevens/doelparameters voor analyse: `a.referrer.campaign.medium`
   * Audience Manager Trait: `c_a_referrer_campaign_medium`

* **Bron campagne**

   Originele referentie, zoals een nieuwsbrief of een netwerk van sociale media. Bevolkt door Mobile App Acquisition.

   * Contextgegevens/doelparameters voor analyse: `a.referrer.campaign.source`
   * Audience Manager Trait: `c_a_referrer_campaign_source`

* **Campagneperiode**

   Betaalde trefwoorden of andere termen die u met deze overname wilt bijhouden. Bevolkt door Mobile App Acquisition.

   * Contextgegevens/doelparameters voor analyse: `a.referrer.campaign.term`
   * Audience Manager Trait: `c_a_referrer_campaign_term`
