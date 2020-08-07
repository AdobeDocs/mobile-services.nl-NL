---
description: Hier volgt de referentie-informatie voor de standaard mobiele metriek en afmetingen.
keywords: mobile
seo-description: Hier volgt de referentie-informatie voor de standaard mobiele metriek en afmetingen.
seo-title: Referentie voor mobiele Dimension
solution: Marketing Cloud,Analytics
title: Referentie voor mobiele Dimension
topic: Metrics
uuid: 96170ae7-8553-4f3e-ae01-65e5b664adf4
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 1%

---


# Verwijzing naar mobiele meeteenheden en afmetingen {#mobile-metrics-and-dimensions-reference}

Deze informatie helpt u meer over de standaard mobiele metriek en afmetingen te begrijpen.

>[!TIP]
>
>De afmetingen en metrische toestemmingen die in Adobe Analytics worden geplaatst zijn op de Mobiele Diensten van toepassing. Wanneer u probeert om een rapport zonder de juiste toestemmingen in werking te stellen, komt een fout voor.

## Cijfers {#section_6704C815147D44AF96151D626BEB813C}

Hier volgt een lijst met standaard mobiele meetgegevens:

* **Eerste keer starten**

   Wordt geactiveerd bij de eerste uitvoering na een installatie of een nieuwe installatie.

* **Upgrades**

   Teweeggebracht op de eerste looppas na een verbetering of wanneer het versieaantal verandert.

* **Dagelijkse deelnemers**

   Wordt geactiveerd wanneer de toepassing op een bepaalde dag wordt gebruikt.

   >[!TIP]
   >
   >De gebeurtenis Daily Engaged Users wordt niet automatisch opgeslagen in een metrische analyse. U moet een verwerkingsregel maken die een aangepaste gebeurtenis instelt om deze metrische waarde vast te leggen.

* **Maandelijkse deelnemers**

   Wordt geactiveerd wanneer de toepassing tijdens een maand wordt gebruikt.

   >[!TIP]
   >De gebeurtenis Maandelijkse gecodeerde gebruikers wordt niet automatisch opgeslagen in een metrische analyse. U moet een verwerkingsregel maken die een aangepaste gebeurtenis instelt om deze metrische waarde vast te leggen.

* **Lanceringen**

   Teweeggebracht op een looppas die geen installatie of een verbetering is. Dit wordt ook geactiveerd wanneer de toepassing de achtergrond verlaat. Standaard wordt een nieuwe opstart gestart wanneer de toepassing gedurende vijf of meer minuten op de achtergrond wordt uitgevoerd. De hoeveelheid achtergrondtijd voordat een nieuwe start wordt gestart, kan worden geconfigureerd in **[!UICONTROL SDK Analytics Options]** de pagina Toepassingsinstellingen beheren. Zie de rij Time-out *sessie (seconden)* in de rij [Analyseopties](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md)SDK configureren voor meer informatie.

   >[!IMPORTANT]
   >Omdat de manier waarop bezoeken in [!UICONTROL Adobe Analytics] en mobiele toepassingen worden gestart [!UICONTROL Adobe Mobile Services] wordt berekend, ziet u mogelijk verschillende resultaten in de rapportage. Zie Bezoekingen [vergelijken en Mobiele toepassingen starten](https://helpx.adobe.com/analytics/kb/compare-visits-and-mobile-app-launches.html)voor meer informatie.

* **Crashes**

   Wordt geactiveerd wanneer de toepassing niet correct wordt afgesloten. Deze gebeurtenis wordt verzonden wanneer de toepassing start nadat de toepassing is vastgelopen.

   >[!TIP]
   >De toepassing loopt vast als afsluiten niet wordt aangeroepen.

* **Totale lengte sessie**

   Geaggregeerde totale sessielengte.

## Dimensies {#section_1784C7E859F64CCEB95C5DD1DCF5C98D}

Hier volgt een lijst met standaard mobiele afmetingen:

* **Installatiedatum**

   Datum van de eerste start na de installatie. De datum is in de notatie *MM/DD/JJJJ* .

* **Toepassings-id**

   Hiermee slaat u de toepassingsnaam en -versie op in de volgende indeling: `[AppName] [BundleVersion]`. Bijvoorbeeld, `myapp 1.1`.

* **Startnummer**

   Aantal keren dat de toepassing is gestart of van de achtergrond is verwijderd.

* **Dagen sinds eerste gebruik**

   Aantal dagen sinds de eerste run.

* **Dagen sinds laatste gebruik**

   Aantal dagen sinds laatste gebruik.

* **Uur van dag**

   Meet het uur waarin de app is gestart en gebruikt de numerieke notatie van 24 uur. Deze dimensie wordt ook gebruikt voor tijd het ontleden om piekgebruikstijden te bepalen.

* **Weekdag**

   Aantal weken dat de app is gestart.

* **Besturingssysteem**

   Besturingssysteem van het apparaat.

* **Versie besturingssysteem**

   Versie van besturingssysteem.

* **Dagen sinds laatste upgrade**

   Aantal dagen sinds het versienummer van de toepassing is gewijzigd.

   >[!TIP]
   >
   >De dagen sinds laatste verbetering wordt niet automatisch opgeslagen in een variabele Analytics. U moet een verwerkingsregel maken om deze waarde te kopiëren naar een variabele Analytics voor rapportage.

* **Starten vanaf laatste upgrade**

   Aantal keren starten nadat het versienummer van de toepassing is gewijzigd.

   >[!TIP]
   >
   >De lanceringen sinds laatste verbetering wordt niet automatisch opgeslagen in een variabele Analytics. U moet een verwerkingsregel maken om deze waarde te kopiëren naar een variabele Analytics voor rapportage.

* **Apparaatnaam**

   Hiermee slaat u de apparaatnaam op. In iOS identificeert een door komma&#39;s gescheiden tekenreeks van twee cijfers het iOS-apparaat. Het eerste getal vertegenwoordigt het genereren van het apparaat en de tweede getalversies van verschillende leden van de apparaatfamilie. Zie [iOS-apparaatversies](/help/ios/reference/device-versions.md)voor een volledige lijst met veelgebruikte apparaatnamen.

* **Naam vervoerder**

   Hiermee wordt de naam van de mobiele serviceprovider opgeslagen.

* **Resolutie**

   Breedte en hoogte in werkelijke pixels.
