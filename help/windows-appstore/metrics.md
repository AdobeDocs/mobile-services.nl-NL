---
description: Hier worden de metriek en afmetingen weergegeven die automatisch door de mobiele bibliotheek kunnen worden gemeten.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Levenscycluswaarden
topic-fix: Developer and implementation
uuid: c483271f-f620-46f4-aad8-d5f02d763f7d
exl-id: a1e4eeca-8b8f-47ca-a489-acc338238c42
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 3%

---

# Levenscycluswaarden{#lifecycle-metrics}

Hier worden de metriek en afmetingen weergegeven die automatisch door de mobiele bibliotheek kunnen worden gemeten.

Zie voor meer informatie [Levenscyclusgegevens oplossen](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html).

## Metrische gegevens en afmetingen van de levenscyclus {#section_78F036C4296F4BA3A47C2044F79C86C1}

Wanneer gevormd, worden de metriek van de levenscyclus verzonden in de parameters van contextgegevens naar Analytics, in parameters aan Doel met elke mbox vraag, en als signaal aan Audience Manager. Analytics en Target gebruiken dezelfde indeling en Audience Manager gebruikt voor elke meting een ander voorvoegsel.

Voor Analytics, worden de contextgegevens die met elke levenscyclusvolgende vraag worden verzonden automatisch binnen gevangen en gemeld door metrisch of afmeting te gebruiken hieronder wordt vermeld, en de uitzonderingen worden genoteerd.

### Metrics

* **Eerste keer starten**

   Wordt geactiveerd bij de eerste run na installatie of herinstallatie.

   * Contextgegevens/doelparameter voor analyse: `a.InstallEvent`
   * Audience Manager signaal: `c_a_InstallEvent`

* **Upgrades**

   Teweeggebracht bij de eerste looppas na een verbetering of wanneer het versieaantal verandert.

   * Contextgegevens/doelparameter voor analyse: `a.UpgradeEvent`
   * Audience Manager signaal: `c_a_UpgradeEvent`

* **Dagelijkse deelnemers**

   Wordt geactiveerd wanneer de toepassing op een bepaalde dag wordt gebruikt.

   >[!TIP]
   >
   >Deze metrisch wordt niet automatisch opgeslagen in metrisch Analytics. U moet een verwerkingsregel maken die een aangepaste gebeurtenis instelt om deze metrische waarde vast te leggen.

   * Contextgegevens/doelparameter voor analyse: `a.DailyEngUserEvent`
   * Audience Manager signaal: `c_a_DailyEngUserEvent`

* **Maandelijkse deelnemers**

   Wordt geactiveerd wanneer de toepassing tijdens een bepaalde maand wordt gebruikt.

   >[!IMPORTANT]
   >
   >Deze metrisch wordt niet automatisch opgeslagen in metrisch Analytics. U moet een verwerkingsregel maken die een aangepaste gebeurtenis instelt om deze metrische waarde vast te leggen.

   * Contextgegevens/doelparameter voor analyse: `a.MonthlyEngUserEvent`
   * Audience Manager signaal: `c_a_MonthlyEngUserEvent`

* **Lanceringen**

   Teweeggebracht bij elke looppas, met inbegrip van neerstortingen en installaties. Wordt ook geactiveerd op een hervat vanaf de achtergrond wanneer de time-out van de levenscyclussessie is overschreden.

   * Contextgegevens/doelparameter voor analyse: `a.LaunchEvent`
   * Audience Manager signaal: `c_a_LaunchEvent`

* **Crashes**

   Wordt geactiveerd wanneer de toepassing geen achtergrond heeft voordat deze wordt gesloten. De gebeurtenis wordt verzonden wanneer de toepassing na de crash wordt gestart. Bij het rapporteren van crash door Adobe Mobile wordt geen globale handler voor niet-afgevangen uitzonderingen geïmplementeerd.

   * Contextgegevens/doelparameter voor analyse: `a.CrashEvent`
   * Audience Manager signaal: `c_a_CrashEvent`

* **Lengte vorige sessie**

   Meldt het aantal seconden dat een vorige toepassingssessie heeft geduurd, op basis van de duur van de toepassing en op de voorgrond.

   * Contextgegevens/doelparameter voor analyse: `a.PrevSessionLength`
   * Audience Manager signaal: `c_a_PrevSessionLength`

### Dimensies

* **Installatiedatum**

   Datum van eerste lancering na installatie. De datumnotatie is `MM/DD/YYYY`.

   * Contextgegevens/doel voor analyse: `a.InstallDate`
   * Audience Manager: `c_a_InstallDate`

* **Toepassings-id**

   Hiermee worden de toepassingsnaam en -versie opgeslagen in het dialoogvenster `[AppName] [BundleVersion]` gebruiken. Een voorbeeld van deze indeling is `myapp 1.1`.

   * Contextgegevens/doel voor analyse: `a.AppID`
   * Audience Manager: `c_a_AppID`

* **Startnummer**

   Aantal keren dat de toepassing is gestart of van de achtergrond is verwijderd.

   * Contextgegevens/doel voor analyse: `a.Launches`
   * Audience Manager: `c_a_Launches`

* **Dagen sinds eerste gebruik**

   Aantal dagen sinds de eerste run.

   * Contextgegevens/doel voor analyse: `a.DaysSinceFirstUse`
   * Audience Manager: `c_a_DaysSinceFirstUse`

* **Dagen sinds laatste gebruik**

   Aantal dagen sinds laatste gebruik.

   * Contextgegevens/doel voor analyse: `a.DaysSinceLastUse`
   * Audience Manager: `c_a_DaysSinceLastUse`

* **Uur van dag**

   Hiermee wordt het uur gemeten waarop de app is gestart. Deze metrische waarde gebruikt het 24-uurs numerieke formaat en wordt gebruikt voor tijd het ontleden om piekgebruikstijden te bepalen.

   * Contextgegevens/doel voor analyse: `a.HourOfDay`
   * Audience Manager: `c_a_HourOfDay`

* **Weekdag**

   Aantal dagen in een week waarin de app is gestart.

   * Contextgegevens/doel voor analyse: `a.DayOfWeek`
   * Audience Manager: `c_a_DayOfWeek`

* **Versie besturingssysteem**

   De versie van het besturingssysteem.

   * Contextgegevens/doel voor analyse: `a.OSVersion`
   * Audience Manager: `c_a_OSVersion`

* **Dagen sinds laatste upgrade**

   Aantal dagen sinds het versienummer van de toepassing is gewijzigd.

   >[!IMPORTANT]
   >
   >Deze metrische waarde wordt niet automatisch opgeslagen in een variabele Analytics. U moet een verwerkingsregel maken om deze waarde te kopiëren naar een variabele Analytics voor rapportage.

   * Contextgegevens/doel voor analyse: `a.DaysSinceLastUpgrade`
   * Audience Manager: `c_a_DaysSinceLastUpgrade`

* **Starten sinds laatste upgrade**

   Aantal keren starten nadat het versienummer van de toepassing is gewijzigd.

   >[!IMPORTANT]
   >
   >Deze metrische waarde wordt niet automatisch opgeslagen in een variabele Analytics. U moet een verwerkingsregel maken om deze waarde te kopiëren naar een variabele Analytics voor rapportage.

   * Contextgegevens/doel voor analyse: `a.LaunchesSinceUpgrade`
   * Audience Manager: `c_a_LaunchesSinceUpgrade`

* **Apparaatnaam**

   Hiermee slaat u de apparaatnaam op.

   * Contextgegevens/doel voor analyse: `a.DeviceName`
   * Audience Manager: `c_a_DeviceName`

* **Naam vervoerder**

   Hiermee wordt de naam van de mobiele serviceprovider opgeslagen, zoals opgegeven door het apparaat.

   >[!IMPORTANT]
   >
   >Deze metrische waarde wordt niet automatisch opgeslagen in een variabele Analytics. U moet een verwerkingsregel maken om deze waarde te kopiëren naar een variabele Analytics voor rapportage.

   * Contextgegevens/doel voor analyse: `a.CarrierName`
   * Audience Manager: `c_a_CarrierName`

* **Resolutie**

   Breedte x Hoogte in werkelijke pixels.

   * Contextgegevens/doel voor analyse: `a.Resolution`
   * Audience Manager: `c_a_Resolution`


## Extra mobiele meeteenheden en afmetingen {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

De volgende meetwaarden en afmetingen worden in de variabelen van de mobiele oplossing vastgelegd door de methodes die in de beschrijving worden vermeld.

### Metrisch

* **Totale tijd van handeling**

   Bevolkt door `trackTimedAction` methoden.

   * Contextgegevens/doelparameter voor analyse: `a.action.time.total`
   * Audience Manager: `c_a_action_time_total`

* **Tijd van handeling in toepassing**

   Bevolkt door `trackTimedAction` methoden.

   * Contextgegevens/doelparameter voor analyse: `a.action.time.inapp`
   * Audience Manager: `c_a_action_time_inapp`

* **Lifetime-waarde (gebeurtenis)**

   Bevolkt door `trackLifetimeValue` methoden.

   * Contextgegevens/doelparameter voor analyse: `a.ltv.amount`
   * Audience Manager: `c_a_ltv_amount`

## Dimensies

* **Locatie (tot 10 km)**

   Bevolkt door `trackLocation` methoden.

   * Contextgegevens/doelparameter voor analyse:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Manager:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Locatie (tot 100 m)**

   Bevolkt door `trackLocation` methoden.

   * Contextgegevens/doelparameter voor analyse:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Manager:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Locatie (tot 1 m)**

   Bevolkt door `trackLocation` methoden.

   * Contextgegevens/doelparameter voor analyse:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Manager:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Naam van belangenpunt**

   Bevolkt door `trackLocation` methoden wanneer het apparaat zich binnen een gedefinieerde POI bevindt.

   * Contextgegevens/doelparameter voor analyse: `a.loc.poi`
   * Audience Manager: `c_a_loc_poi`

* **Afstand tot belangencentrum**

   Bevolkt door `trackLocation` methoden wanneer het apparaat zich binnen een gedefinieerde POI bevindt.

   * Contextgegevens/doelparameter voor analyse: `a.loc.dist`
   * Audience Manager: `c_a_loc_dist`

* **Lifetime-waarde (conversievariabele)**

   Bevolkt door `trackLifetimeValue` methoden.

   * Contextgegevens/doelparameter voor analyse: `a.ltv.amount`
   * Audience Manager: `c_a_ltv_amount`
