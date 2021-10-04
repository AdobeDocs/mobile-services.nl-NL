---
description: In de volgende tabellen worden de metriek en afmetingen weergegeven die automatisch door de mobiele bibliotheek kunnen worden gemeten nadat de levenscyclus is geïmplementeerd.
solution: Experience Cloud,Analytics
title: Levenscycluscijfers
topic-fix: Developer and implementation
uuid: b795e383-d59b-4a3c-9e14-ffe8fb58412c
exl-id: b51b6c41-843f-499d-9cf2-7ce96ed82fc0
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '1085'
ht-degree: 1%

---

# Levenscycluswaarden {#lifecycle-metrics}

Hier volgen de meetwaarden en afmetingen die automatisch door de mobiele bibliotheek kunnen worden gemeten nadat de levenscyclus is geïmplementeerd.

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze recentste documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga om aan de slag te gaan naar [Experience Platform Launch](https://launch.adobe.com/).
* Ga naar [Github om te zien wat er in de SDK-opslagruimten van het Experience Platform staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Metrische gegevens en afmetingen van de levenscyclus {#section_78F036C4296F4BA3A47C2044F79C86C1}

Nadat de metriek van de levenscyclus worden gevormd, worden de metriek verzonden in de parameters van contextgegevens naar Analytics, parameters aan Doel met elke mbox vraag, en als signaal aan Audience Manager. Analytics en Target gebruiken dezelfde indeling, terwijl Audience Manager voor elke meting een ander voorvoegsel gebruikt.

Voor Analytics, worden de contextgegevens die met elke levenscyclusvolgende vraag worden verzonden automatisch gevangen binnen en door metrisch of afmeting te gebruiken gemeld die in de eerste kolom worden vermeld.

>[!TIP]
>
>De beschrijving bevat uitzonderingen.

### Metrics

* **Eerste keer starten**

   Wordt geactiveerd bij de eerste run na installatie of herinstallatie.

   * Contextgegevens/doelparameter voor analyse: `a.InstallEvent`
   * Audience Manager signaal: `c_a_InstallEvent`

* **Upgrades**

   Wordt geactiveerd bij de eerste uitvoering na de upgrade of wanneer het versienummer verandert.

   * Contextgegevens/doelparameter voor analyse: `a.UpgradeEvent`
   * Audience Manager signaal: `c_a_UpgradeEvent`

* **Dagelijkse deelnemers**

   Wordt geactiveerd wanneer de toepassing op een bepaalde dag wordt gebruikt.

   * Contextgegevens/doelparameter voor analyse: `a.DailyEngUserEvent`
   * Audience Manager signaal: `c_a_DailyEngUserEvent`

* **Maandelijkse deelnemers**

   Wordt geactiveerd wanneer de toepassing tijdens een bepaalde maand wordt gebruikt.

   * Contextgegevens/doelparameter voor analyse: `a.MonthlyEngUserEvent`
   * Audience Manager signaal: `c_a_MonthlyEngUserEvent`

* **Lanceringen**

   Wordt geactiveerd bij elke uitvoering, inclusief crashes en installaties. Wordt ook geactiveerd wanneer de toepassing vanaf de achtergrond wordt hervat nadat de time-out van de levenscyclussessie is overschreden.

   * Contextgegevens/doelparameter voor analyse: `a.LaunchEvent`
   * Audience Manager signaal: `c_a_LaunchEvent`

* **Crashes**

   Wordt geactiveerd wanneer de toepassing geen achtergrond heeft voordat deze wordt gesloten. De gebeurtenis wordt verzonden wanneer de toepassing na het vastlopen opnieuw wordt gestart.  Bij het rapporteren van Adobe Mobile-crashes wordt geen globale handler voor niet-afgevangen uitzonderingen geïmplementeerd.

   * Contextgegevens/doelparameter voor analyse: `a.CrashEvent`
   * Audience Manager signaal: `c_a_CrashEvent`

* **Lengte vorige sessie**

   Meldt het aantal seconden dat een vorige toepassingssessie heeft geduurd op basis van de duur van de toepassing en op de voorgrond.

   * Contextgegevens/doelparameter voor analyse: `a.PrevSessionLength`
   * Audience Manager signaal: `c_a_PrevSessionLength`

>[!IMPORTANT]
>
> De *Daily Engaged Users* en *Maandelijkse Betrokken Gebruikers* metriek worden niet automatisch opgeslagen in Analytics metrisch. U moet een verwerkingsregel maken die een aangepaste gebeurtenis instelt om deze metriek vast te leggen.

#### Dimensies

* **Installatiedatum**

   Datum van eerste lancering na installatie.  De datumnotatie is `MM/DD/YYYY`.

   * Contextgegevens/doel analyse: `a.InstallDate`
   * Publiek beheer: `c_a_InstallDate`

* **Toepassings-id**

   Hiermee worden de toepassingsnaam en -versie opgeslagen in de indeling `[AppName] [BundleVersion]`. Bijvoorbeeld, `myapp 1.1`.

   * Contextgegevens/doel analyse: `a.AppID`
   * Publiek beheer: `c_a_AppID`

* **Startnummer**

   Aantal keren dat de toepassing is gestart of van de achtergrond is verwijderd.

   * Contextgegevens/doel analyse: `a.Launches`
   * Publiek beheer: `c_a_Launches`

* **Dagen sinds eerste gebruik**

   Aantal dagen sinds eerste run.

   * Contextgegevens/doel analyse: `a.DaysSinceFirstUse`
   * Publiek beheer: `c_a_DaysSinceFirstUse`

* **Dagen sinds laatste gebruik**

   Aantal dagen sinds laatste gebruik.

   * Contextgegevens/doel analyse: `a.DaysSinceLastUse`
   * Publiek beheer: `c_a_DaysSinceLastUse`

* **Uur van dag**

   Meet het tijdstip waarop de app is gestart en gebruikt de numerieke notatie van 24 uur. Wordt gebruikt voor tijdsverdeling om piekgebruikstijden te bepalen.

   * Contextgegevens/doel analyse: `a.HourOfDay`
   * Publiek beheer: `c_a_HourOfDay`

* **Weekdag**

   Aantal weken dat de app is gestart.

   * Contextgegevens/doel analyse: `a.DayOfWeek`
   * Publiek beheer: `c_a_DayOfWeek`

* **Versie besturingssysteem**

   Aantal dagen sinds het versienummer van de toepassing is gewijzigd.

   * Contextgegevens/doel analyse: `a.OSVersion`
   * Publiek beheer: `c_a_OSVersion|OS version`

* **Dagen sinds laatste upgrade**

   Dagen sinds laatste upgrade.

   * Contextgegevens/doel analyse: `a.DaysSinceLastUpgrade`
   * Publiek beheer: `c_a_DaysSinceLastUpgrade`

* **Starten sinds laatste upgrade**

   Aantal keren starten nadat het versienummer van de toepassing is gewijzigd.

   * Contextgegevens/doel analyse: `a.LaunchesSinceUpgrade`
   * Publiek beheer: `c_a_LaunchesSinceUpgrade`

* **Apparaatnaam**

   Hiermee slaat u de apparaatnaam op.  Een door komma&#39;s gescheiden tekenreeks van twee cijfers die het iOS-apparaat identificeert. Het eerste aantal vertegenwoordigt typisch de apparatengeneratie, en het tweede aantal versies verschillende leden van de apparatenfamilie. Zie iOS-apparaatversies voor een lijst met veelgebruikte apparaatnamen.

   * Contextgegevens/doel analyse: `a.DeviceName`
   * Publiek beheer: `c_a_DeviceName`

* **Naam vervoerder**

   Hiermee wordt de naam van de mobiele serviceprovider opgeslagen, zoals opgegeven door het apparaat.

   * Contextgegevens/doel analyse: `a.CarrierName`
   * Publiek beheer: `c_a_CarrierName`

* **Resolutie**

   Breedte x Hoogte in werkelijke pixels.

   * Contextgegevens/doel analyse: `a.Resolution`
   * Publiek beheer: `c_a_Resolution`
   >[!IMPORTANT]
   >
   >De *Dagen sinds laatste verbetering*, *Lanceert sinds laatste verbetering*, en de *Naam van de Drager* afmetingen worden niet automatisch opgeslagen in een variabele Analytics. U moet een verwerkingsregel maken om de waarden naar een variabele Analytics te kopiëren voor rapportage.


## Extra mobiele meeteenheden en afmetingen {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

De volgende meetwaarden en afmetingen worden door de vermelde methode vastgelegd in variabelen voor mobiele oplossingen.

### Metrisch

* **Totale tijd van handeling**

   Bevolkt door methoden trackTimedAction.

   * Contextgegevens/doelparameter voor analyse: `a.action.time.total`
   * Audience Management-kenmerk: `c_a_action_time_total`

* **Tijd van handeling in toepassing**

   Bevolkt door methoden trackTimedAction.

   * Contextgegevens/doelparameter voor analyse: `a.action.time.inapp`
   * Audience Management-kenmerk: `c_a_action_time_inapp`

* **Lifetime-waarde (gebeurtenis)**

   Bevolkt door trackLifetimeValue-methoden.

   * Contextgegevens/doelparameter voor analyse: `a.ltv.amount`
   * Audience Management-kenmerk: `c_a_ltv_amount`


### Dimensies

* **Locatie (tot 10 km)**

   Wordt gevuld met methoden `trackLocation`.

   * Contextgegevens/doelparameter voor analyse:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Management-kenmerk:

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **Locatie (tot 100 m)**

   Bevolkt door trackLocation-methoden.

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

   Wordt gevuld door trackLocation-methoden wanneer het apparaat zich in een gedefinieerde POI bevindt.

   * Contextgegevens/doelparameter voor analyse: `a.loc.poi`
   * Audience Management-kenmerk: `c_a_loc_poi`

* **Afstand tot belangencentrum**

   Wordt gevuld door trackLocation-methoden wanneer het apparaat zich in een gedefinieerde POI bevindt.

   * Contextgegevens/doelparameter voor analyse: `a.loc.dist`
   * Audience Management-kenmerk: `c_a_loc_dist`

* **Lifetime-waarde (conversievariabele)**

   Bevolkt door trackLifetimeValue-methoden.

   * Contextgegevens/doelparameter voor analyse: `a.ltv.amount`
   * Audience Management-kenmerk: `c_a_ltv_amount`

* **Trackingcode**

   Bevolkt door Mobile App Acquisition. Automatisch gegenereerd door mobiele Adobe-services.

   * Contextgegevens/doelparameter voor analyse: `a.referrer.campaign.trackingcode`
   * Audience Management-kenmerk: `c_a_referrer_campaign_trackingcode`

* **Campaign**

   Naam van de campagne, die ook in de campagnevariabele wordt opgeslagen. Bevolkt door Mobile App Acquisition.

   * Contextgegevens/doelparameter voor analyse: `a.referrer.campaign.name`
   * Audience Management-kenmerk: `c_a_referrer_campaign_name`

* **Campagne-inhoud**

   De naam of id van de inhoud die de koppeling heeft weergegeven. Bevolkt door Mobile App Acquisition.

   * Contextgegevens/doelparameter voor analyse: `a.referrer.campaign.content`
   * Audience Management-kenmerk: `c_a_referrer_campaign_content`

* **Campagne normaal**

   Marketing medium, zoals banner of e-mail. Bevolkt door Mobile App Acquisition.

   * Contextgegevens/doelparameter voor analyse: `a.referrer.campaign.medium`
   * Audience Management-kenmerk: `c_a_referrer_campaign_medium`

* **Bron campagne**

   Originele referentie, zoals nieuwsbrief of sociaal medianetwerk. Bevolkt door Mobile App Acquisition.

   * Contextgegevens/doelparameter voor analyse: `a.referrer.campaign.source`
   * Audience Management-kenmerk: `c_a_referrer_campaign_source`

* **Campagneperiode**

   Betaalde trefwoorden of andere termen die u met deze overname wilt bijhouden. Bevolkt door Mobile App Acquisition.

   * Contextgegevens/doelparameter voor analyse: `a.referrer.campaign.term`
   * Audience Management-kenmerk: `c_a_referrer_campaign_term`
