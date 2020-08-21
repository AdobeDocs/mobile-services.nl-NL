---
description: Nadat u de bibliotheek aan uw project toevoegt, kunt u om het even welke de methodevraag van Analytics overal in uw App (zorg ervoor u ADBMobile.h in uw klasse invoert) maken.
seo-description: Nadat u de bibliotheek aan uw project toevoegt, kunt u om het even welke de methodevraag van Analytics overal in uw App (zorg ervoor u ADBMobile.h in uw klasse invoert) maken.
seo-title: 'Analytics  '
title: 'Analytics  '
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 3%

---


# Analytics{#analytics}  

Nadat u de bibliotheek aan uw project toevoegt, kunt u om het even welke de methodevraag van Analytics overal in uw App (zorg ervoor u ADBMobile.h in uw klasse invoert) maken.

## Rapporten voor mobiele toepassingen inschakelen in Analytics {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

Voordat u code toevoegt, moet uw Analysesysteembeheerder het volgende invullen om het bijhouden van de levensduur van de mobiele toepassing in te schakelen. Dit zorgt ervoor dat uw rapportreeks klaar is om metriek te vangen aangezien u met ontwikkeling begint.


1. Open **[!UICONTROL Admin Tools]** > **[!UICONTROL Report Suites]** en selecteer uw mobiele rapportsuite(s).
1. Klik op **[!UICONTROL Edit Settings]** > **[!UICONTROL Mobile Management]** > **[!UICONTROL Mobile Application Reporting]**.

   ![](assets/mobile-settings.png)

1. Klik op **[!UICONTROL Enable Latest App Reports]**.

   U kunt ook klikken **[!UICONTROL Enable Mobile Location Tracking]** en **[!UICONTROL Enable Legacy Reporting and Attribution for background hits]**.

   ![](assets/enable-lifecycle.png)

De metriek van de levenscyclus zijn nu klaar om worden gevangen, en de Mobiele Rapporten van de Toepassing verschijnen in het **[!UICONTROL Reports]** menu in de marketing rapportinterface.

## Metrische gegevens over de levenscyclus verzamelen {#task_25D469C62DF84573AEB5E8E950B96205}

1. Als u gegevens over de levenscyclus in uw app wilt verzamelen, roept u `collectLifecycleData()` de `ApplicationUI` constructor aan.

   Bijvoorbeeld:

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   Als `collectLifecycleData()` tweemaal in de zelfde zitting wordt geroepen, dan zal uw toepassing een neerstorting op elke vraag na de eerste melden. De SDK stelt een markering in wanneer de toepassing wordt afgesloten die aangeeft dat de toepassing is afgesloten. Als deze markering niet is ingesteld, `collectLifecyleData()` wordt een crash gemeld.

## Gebeurtenissen, profielen en eVars {#concept_B885D5A71A5D45129CE7C1C3426A7D28}


Als u naar de [Klasse ADBMobile en Verwijzing](/help/blackberry/methods.md)van de Methode hebt gekeken, bent u waarschijnlijk benieuwd waar te om gebeurtenissen, steunen, steunen, erfgenamen, en lijsten te plaatsen. In versie 4 kunt u deze typen variabelen niet meer rechtstreeks in uw app toewijzen. In plaats daarvan gebruikt de SDK contextgegevens en verwerkingsregels om uw toepassingsgegevens toe te wijzen aan analytische variabelen voor rapportage.

De verwerkingsregels bieden u verschillende voordelen:

* U kunt de gegevenstoewijzing wijzigen zonder een update naar de App Store te verzenden.
* U kunt betekenisvolle namen voor gegevens gebruiken in plaats van het plaatsen van variabelen die voor een rapportreeks specifiek zijn.
* Het verzenden van extra gegevens heeft weinig effect. Deze waarden worden pas in rapporten weergegeven als ze met verwerkingsregels zijn toegewezen.

Om het even welke waarden die u rechtstreeks aan variabelen toewees zouden in plaats daarvan aan `data` HashMap moeten worden toegevoegd.

## Verwerkingsregels {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

De verwerkingsregels worden gebruikt om de gegevens te kopiëren u in de variabelen van contextgegevens naar gebeurtenissen, steunen, en andere variabelen voor het melden verzendt.

[Opleiding](https://tv.adobe.com/embed/1181/16506/) verwerkingsregels @ top 2013

[Verwerkingsregels](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Word gemachtigd om verwerkingsregels te gebruiken](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

U wordt aangeraden de variabelen van de contextgegevens te groeperen met behulp van &#39;namespaces&#39;, omdat u hiermee de logische volgorde kunt behouden. Als u bijvoorbeeld informatie over een product wilt verzamelen, kunt u de volgende variabelen definiëren:

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

Contextgegevensvariabelen worden alfabetisch gesorteerd in de interface met verwerkingsregels, zodat u met naamruimten snel variabelen kunt zien die zich in dezelfde naamruimte bevinden.

We hebben ook gehoord dat sommigen van u contextgegevenssleutels benoemen met het evar- of prop-nummer:

```js
"eVar1":"jimbo"
```

Dit zou het *lichtjes* gemakkelijker kunnen maken wanneer u de eenmalige toewijzing in verwerkingsregels uitvoert, maar u verliest leesbaarheid tijdens het zuiveren en de toekomstige codeupdates kunnen moeilijker zijn. In plaats daarvan raden we u ten zeerste aan beschrijvende namen te gebruiken voor sleutels en waarden:

```js
"username":"jimbo"
```

Contextvariabelen die tellergebeurtenissen definiëren, kunnen dezelfde sleutel en waarde hebben:

```js
"logon":"logon"
```

Contextgegevensvariabelen die incrementele gebeurtenissen definiëren, kunnen de gebeurtenis hebben als de sleutel en de hoeveelheid die moet worden verhoogd als de waarde:

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe behoudt de naamruimte `a.`. Naast die kleine beperking, moeten de variabelen van contextgegevens enkel in uw login bedrijf uniek zijn om botsingen te vermijden.

## Offline bijhouden inschakelen {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

Als u hits wilt opslaan wanneer het apparaat offline is, kunt u optioneel offline bijhouden inschakelen in het `ADBMobileConfig.json` bestand.

Let heel goed op de tijdstempelvereisten die in de configuratiebestandsverwijzing worden beschreven voordat u offline bijhouden inschakelt.

## Analysemethoden

Zie *Analysemethoden* in [Adobe Mobile Class en Method Reference](/help/blackberry/methods.md)voor een lijst met Analytics-methoden die beschikbaar zijn voor BlackBerry.