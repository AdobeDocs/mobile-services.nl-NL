---
description: Hier volgen de afmetingen en metriek die automatisch door de mobiele bibliotheek kunnen worden gemeten, nadat de levenscyclus is geïmplementeerd, en een koppeling om de gegevens van de levenscyclus problemen op te lossen.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud,Analytics
title: Levenscycluswaarden
topic-fix: Developer and implementation
uuid: 5a371f11-6521-410f-a01f-fc3b285b050f
exl-id: d7436411-65bd-4cf7-ae3e-cec829a7690a
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# Levenscycluswaarden {#lifecycle-metrics}

Hier volgen de afmetingen en metriek die automatisch door de mobiele bibliotheek kunnen worden gemeten, nadat de levenscyclus is geïmplementeerd, en een koppeling om de gegevens van de levenscyclus problemen op te lossen.

Ga voor meer informatie naar de Knowledge Base op [Problemen met levenscyclusgegevens oplossen](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html).

## Metrische gegevens en afmetingen van de levenscyclus {#section_78F036C4296F4BA3A47C2044F79C86C1}

Wanneer gevormd, worden de metriek van de levenscyclus verzonden in de parameters van contextgegevens naar Analytics, in parameters aan Doel met elke mbox vraag, en als signaal aan publieksbeheer. Analytics en Target gebruiken dezelfde indeling, terwijl het publieksbeheer voor elke meting een ander voorvoegsel gebruikt.

Voor Analytics, worden de contextgegevens die met elke levenscyclusvolgende vraag worden verzonden automatisch gevangen en op door metrisch of afmeting te gebruiken gemeld.

### Metrics

* **a.media.name**

   Wordt geactiveerd bij de eerste run na installatie of herinstallatie.

   * Contextgegevens/doelparameter voor analyse: `a.InstallEvent`
   * Audience Manager signaal: `c_a_InstallEvent`

* **Upgrades**

   Teweeggebracht bij de eerste looppas na een verbetering of wanneer het versieaantal verandert.

   * Contextgegevens/doelparameter voor analyse: `a.UpgradeEvent`
   * Audience Manager signaal: `c_a_UpgradeEvent`

* **Dagelijkse deelnemers**

   Wordt geactiveerd wanneer de toepassing op een bepaalde dag wordt gebruikt.

   >[!IMPORTANT]
   >
   >Deze metrisch wordt niet automatisch opgeslagen in metrisch Analytics. U moet een verwerkingsregel maken die een aangepaste gebeurtenis instelt om deze metrische waarde vast te leggen.

   * Contextgegevens/doelparameter voor analyse: `a.DailyEngUserEvent`
   * Audience Manager signaal: `c_a_DailyEngUserEvent`

* **Maandelijkse deelnemers**

   Wordt geactiveerd wanneer de toepassing tijdens een bepaalde maand wordt gebruikt.  >>>>

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

   Wordt geactiveerd wanneer de toepassing geen achtergrond heeft voordat deze wordt gesloten. De gebeurtenis wordt verzonden wanneer de toepassing na de crash wordt gestart. Bij het rapporteren van Adobe Mobile-crashes wordt geen globale handler voor niet-afgevangen uitzonderingen geïmplementeerd.

   * Contextgegevens/doelparameter voor analyse: `a.CrashEvent`
   * Audience Manager signaal: `c_a_CrashEvent`

* **Lengte vorige sessie**

   Meldt het aantal seconden dat een vorige toepassingssessie heeft geduurd, op basis van de duur van de toepassing en op de voorgrond.

   * Contextgegevens/doelparameter voor analyse: `a.PrevSessionLength`
   * Audience Manager signaal: `c_a_PrevSessionLength`

### Dimensies

* **Installatiedatum**

   Datum van eerste lancering na installatie. De datumnotatie is `MM/DD/YYYY`.

   * Contextgegevens/doelparameter voor analyse: `a.InstallDate`
   * Audience Manager signaal: `c_a_InstallDate`

* **Toepassings-id**

   Hiermee slaat u de toepassingsnaam en -versie op in de volgende indeling:
   `[AppName] [BundleVersion]`.

   Een voorbeeld van deze indeling is `myapp 1.1`.

   * Contextgegevens/doelparameter voor analyse: `a.AppID`
   * Audience Manager signaal: `c_a_AppID`

* **Startnummer**

   Aantal keren dat de toepassing is gestart of van de achtergrond is verwijderd.

   * Contextgegevens/doelparameter voor analyse: `a.Launches`
   * Audience Manager signaal: `c_a_Launches`

* **Dagen sinds eerste gebruik**

   Aantal dagen sinds de eerste run.

   * Contextgegevens/doelparameter voor analyse: `a.DaysSinceFirstUse`
   * Audience Manager signaal: `c_a_DaysSinceFirstUse`

* **Dagen sinds laatste gebruik**

   Aantal dagen sinds laatste gebruik.

   * Contextgegevens/doelparameter voor analyse: `a.DaysSinceLastUse`
   * Audience Manager signaal: `c_a_DaysSinceLastUse`

* **Uur van dag**

   Hiermee wordt het uur gemeten waarop de app is gestart. Deze metrische waarde gebruikt het 24-uurs numerieke formaat en voor tijd het ontleden gebruikt om piekgebruikstijden te bepalen.

   * Contextgegevens/doelparameter voor analyse: `a.HourOfDay`
   * Audience Manager signaal: `c_a_HourOfDay`

* **Weekdag**

   Aantal dagen in een week waarin de app is gestart.

   * Contextgegevens/doelparameter voor analyse: `a.DayOfWeek`
   * Audience Manager signaal: `c_a_DayOfWeek`

* **Versie besturingssysteem**

   De versie van het besturingssysteem.

   * Contextgegevens/doelparameter voor analyse: `a.OSVersion`
   * Audience Manager signaal: `c_a_OSVersion`

* **Dagen sinds laatste upgrade**

   Aantal dagen sinds het versienummer van de toepassing is gewijzigd.

   >[!IMPORTANT]
   >
   >Deze metrische waarde wordt niet automatisch opgeslagen in een variabele Analytics. U moet een verwerkingsregel maken om deze waarde te kopiëren naar een variabele Analytics voor rapportage.

   * Contextgegevens/doelparameter voor analyse: `a.DaysSinceLastUpgrade`
   * Audience Manager signaal: `c_a_DaysSinceLastUpgrade`

* **Starten sinds laatste upgrade**

   Aantal keren starten nadat het versienummer van de toepassing is gewijzigd.

   >[!IMPORTANT]
   >
   >Deze metrische waarde wordt niet automatisch opgeslagen in een variabele Analytics. U moet een verwerkingsregel maken om deze waarde te kopiëren naar een variabele Analytics voor rapportage.

   * Contextgegevens/doelparameter voor analyse: `a.LaunchesSinceUpgrade`
   * Audience Manager signaal: `c_a_LaunchesSinceUpgrade`

* **Apparaatnaam**

   Hiermee slaat u de apparaatnaam op.

   * Contextgegevens/doelparameter voor analyse: `a.DeviceName`
   * Audience Manager signaal: `c_a_DeviceName`

* **Naam vervoerder**

   Hiermee wordt de naam van de mobiele serviceprovider opgeslagen, zoals opgegeven door het apparaat.

   >[!IMPORTANT]
   >
   >Deze metrische waarde wordt niet automatisch opgeslagen in een variabele Analytics. U moet een verwerkingsregel maken om deze waarde te kopiëren naar een variabele Analytics voor rapportage.

   * Contextgegevens/doelparameter voor analyse: `a.CarrierName`
   * Audience Manager signaal: `c_a_CarrierName`

* **Resolutie**

   Breedte x Hoogte in werkelijke pixels.

   * Contextgegevens/doelparameter voor analyse: `a.Resolution`
   * Audience Manager signaal: `c_a_Resolution`

## Extra mobiele meeteenheden en afmetingen {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

De volgende meetwaarden en afmetingen worden door de vermelde methode vastgelegd in variabelen voor mobiele oplossingen.

* **Locatie (tot 10 km)**

   Wordt gevuld met methoden `trackLocation`.

   * Contextgegevens/doelparameter voor analyse:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Management-kenmerk:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Locatie (tot 100 m)**

   Wordt gevuld met methoden `trackLocation`.

   * Contextgegevens/doelparameter voor analyse:

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Management-kenmerk:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **Locatie (tot 1 m)**

   Wordt gevuld met methoden `trackLocation`.

   * Contextgegevens/doelparameter voor analyse:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Management-kenmerk:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **Naam van belangenpunt**

   Wordt gevuld door `trackLocation`-methoden wanneer het apparaat zich binnen een gedefinieerde POI bevindt.

   * Contextgegevens/doelparameter voor analyse:

      * `a.loc.poi`
   * Audience Management-kenmerk:

      * `c_a_loc_poi`


* **Afstand tot belangencentrum**

   Wordt gevuld door `trackLocation`-methoden wanneer het apparaat zich binnen een gedefinieerde POI bevindt.

   * Contextgegevens/doelparameter voor analyse:

      * `a.loc.dist`
   * Audience Management-kenmerk:

      * `c_a_loc_dist`
