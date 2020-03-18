---
description: 'null'
seo-description: 'null'
seo-title: Analyse
solution: Marketing Cloud,Analytics
title: Analyse
topic: Developer and implementation
uuid: c2cef3d3-77a7-4a8e-bbe4-3db10a77996a
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analyse {#analytics}

Nadat u de bibliotheek aan uw project hebt toegevoegd, kunt u elke willekeurige aanroep van de methode Analytics overal in uw app uitvoeren.

>[!TIP]
>
>Zorg ervoor dat u `ADBMobile.h` naar de klasse importeert.

## Rapporten voor mobiele toepassingen inschakelen in Analytics {#section_F2F9234009184F20BA36B5CDE872B424}

Voordat u code toevoegt, moet uw Analysesysteembeheerder het volgende invullen om het bijhouden van de levensduur van de mobiele toepassing in te schakelen. Dit zorgt ervoor dat uw rapportreeks klaar is om metriek te vangen aangezien u met ontwikkeling begint.

1. Open **[!UICONTROL Admin Tools]** > **[!UICONTROL Report Suites]** en selecteer uw mobiele rapportsuite(s).

1. Klik op **[!UICONTROL Edit Settings]** > **[!UICONTROL Mobile Management]** > **[!UICONTROL Mobile Application Reporting]**.

   ![](assets/mobile-settings.png)

1. Klik op **[!UICONTROL Enable Latest App Reports]**.

   U kunt ook klikken **[!UICONTROL Enable Mobile Location Tracking]** of **[!UICONTROL Enable Legacy Reporting and Attribution for background hits]**.

   ![](assets/enable-lifecycle.png)

De metriek van de levenscyclus zijn nu klaar om worden gevangen, en de Mobiele Rapporten van de Toepassing verschijnen in het **[!UICONTROL Reports]** menu in de marketing rapportinterface.

### Nieuwe versies

Periodiek worden nieuwe versies van de rapportage van mobiele toepassingen uitgebracht. Nieuwe versies worden niet automatisch toegepast op uw rapportsuite. U moet deze stappen herhalen om de upgrade uit te voeren. Telkens wanneer u nieuwe Experience Cloud-functionaliteit toevoegt aan uw app, raden we u aan deze stappen te herhalen om ervoor te zorgen dat u over de nieuwste configuratie beschikt.

## Levenscycluswaarden {#section_532702562A7A43809407C9A2CBA80E1E}

Als u gegevens over de levenscyclus in uw app wilt verzamelen, voegt u aanroepen toe wanneer de toepassing wordt geactiveerd, zoals in de volgende voorbeelden wordt getoond.

### WinJS in default.js

```js
app.onactivated = function (args) { 
  if (args.detail.kind === activation.ActivationKind.launch) { 
   ... 
   // launched and resumed stuff  
   ADBMobile.Config.collectLifecycleData(); 
  } 
}; 
app.oncheckpoint = function (args) { 
  ADBMobile.Config.pauseCollectingLifecycleData(); 
}
```

### C# in App.xaml.cs

```js
public App() 
{ 
    this.InitializeComponent(); 
    this.Resuming += OnResuming; 
    this.Suspending += OnSuspending; 
} 
protected override void OnLaunched(LaunchActivatedEventArgs e) 
{   ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnResuming(object sender, object e) 
{ 
    ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnSuspending(object sender, SuspendingEventArgs e) 
{ 
    ... 
    ADBMobile.Config.PauseCollectingLifecycleData(); 
    ... 
}
```

### C++/CX in App.xaml.cpp

```js
App::App() 
{ 
 InitializeComponent(); 
 Resuming += ref new EventHandler<Object ^>(this, &App::OnResuming); 
 Suspending += ref new SuspendingEventHandler(this, &App::OnSuspending); 
} 
void App::OnResuming(Object ^sender, Object ^args) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
} 
void App::OnSuspending(Object^ sender, SuspendingEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::PauseCollectingLifecycleData(); 
 ... 
} 
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
}
```

Als `CollectLifecycleData()` tweemaal in de zelfde zitting wordt geroepen, meldt uw toepassing een botsing op elke vraag na de eerste. De SDK stelt een markering in wanneer de toepassing wordt afgesloten die aangeeft dat de toepassing is afgesloten. Als deze markering niet is ingesteld, `CollectLifecyleData()` wordt een crash gemeld.

## Gebeurtenissen, profielen en eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

Als u naar de methodes [van](/help/universal-windows/c-configuration/methods.md)SDK hebt gekeken, vraagt u zich waarschijnlijk af waar te om gebeurtenissen, steunen, steunen, erfgenamen, en lijsten te plaatsen. In versie 4 kunt u deze typen variabelen niet meer rechtstreeks in uw app toewijzen. In plaats daarvan gebruikt de SDK contextgegevens en verwerkingsregels om uw toepassingsgegevens toe te wijzen aan analytische variabelen voor rapportage.

De verwerkingsregels bieden u verschillende voordelen:

* U kunt de gegevenstoewijzing wijzigen zonder een update naar de App Store te verzenden.
* U kunt betekenisvolle namen voor gegevens gebruiken in plaats van het plaatsen van variabelen die voor een rapportreeks specifiek zijn.
* Het verzenden van extra gegevens heeft weinig effect. Deze waarden worden pas in rapporten weergegeven als ze met verwerkingsregels zijn toegewezen.

Waarden die u rechtstreeks toewijst aan variabelen, moeten worden toegevoegd aan contextgegevens.

## Verwerkingsregels {#section_66EE762EEA5E4728864166201617DEBF}

De verwerkingsregels worden gebruikt om de gegevens te kopiëren u in de variabelen van contextgegevens naar gebeurtenissen, steunen, en andere variabelen voor het melden verzendt.

[Opleiding](https://tv.adobe.com/embed/1181/16506/) verwerkingsregels @ top 2013

[Help bij verwerkingsregels](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Verwerkingsregels mogen gebruiken](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

U wordt aangeraden de variabelen van de contextgegevens te groeperen met behulp van &#39;namespaces&#39;, omdat u hiermee de logische volgorde kunt behouden. Als u bijvoorbeeld informatie over een product wilt verzamelen, kunt u de volgende variabelen definiëren:

```javascript
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

Stel contextvariabelen die tegengebeurtenissen definiëren in op de waarde &quot;1&quot;:

```js
"logon":"1"
```

Contextgegevensvariabelen die incrementele gebeurtenissen definiëren, kunnen de waarde hebben om te verhogen:

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe behoudt de naamruimte `a.`. Behalve deze beperking, moeten de variabelen van contextgegevens enkel in uw login bedrijf uniek zijn om botsingen te vermijden.

## Variabele voor producten {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Voor het instellen *`products`* in de mobiele SDK moet u een speciale syntaxis gebruiken. Voor meer informatie, zie de variabele [van](/help/universal-windows/analytics/products.md)Producten.

## (Optioneel) Offline bijhouden inschakelen {#section_955B2A03EB854742BDFC4A0A3C287009}

Als u hits wilt opslaan wanneer het apparaat offline is, kunt u offline bijhouden inschakelen in het bestand met [SDK-methoden](/help/universal-windows/c-configuration/methods.md) . Let goed op de tijdstempelvereisten die worden beschreven in de verwijzing naar het configuratiebestand voordat u offline bijhouden inschakelt.

## Geolocatie en aandachtspunten {#section_BAD34A8DD013454DB355121316BD7FD4}

Met Geo-location kunt u locatiegegevens (breedte/lengte) en vooraf gedefinieerde interessepunten meten. Elke `TrackLocation` vraag verzendt:

* Latitude/Longitude en POI (indien binnen een POI die is gedefinieerd in het `ADBMobileConfig.json` configuratiebestand).

   Deze worden doorgegeven aan mobiele oplossingsvariabelen voor automatische rapportage.

* Afstand van middelpunt en nauwkeurigheid die als contextgegevens worden doorgegeven.

   Vastleggen met een verwerkingsregel.

Een locatie volgen:

```js
var ADB = ADBMobile; 
ADB.Analytics.trackLocation(37.75345, -122.33207, null);
```

Als de volgende POI in het `ADBMobileConfig.json` configuratiedossier wordt bepaald:

```js
"poi" : [ 
            ["San Francisco",37.757144,-122.44812,7000], 
        ]
```

Wanneer wordt bepaald dat de locatie van het apparaat zich binnen een straal van 7000 meter van het gedefinieerde punt bevindt, `a.loc.poi` wordt een variabele met `San Francisco` contextgegevens met de waarde verzonden bij de `TrackLocation` hit. Een `a.loc.dist` contextvariabele wordt verzonden met de afstand in meters van de gedefinieerde coördinaten.

## Lifetime-waarde {#section_D2C6971545BA4D639FBE07F13EF08895}

Met de waarde Lifetime kunt u een levensduurwaarde voor elke gebruiker meten en als doel instellen. Telkens wanneer u een waarde met `TrackLifetimeValueIncrease`verzendt, wordt de waarde toegevoegd aan de bestaande waarde. De waarde van het leven wordt opgeslagen op apparaat en kan op elk ogenblik worden teruggewonnen door te roepen `GetLifetimeValue`. Dit kan worden gebruikt om levensduuraankopen, meningen, video voltooit, sociale aandelen, foto uploads, etc. op te slaan.

```js
// Lifetime Value Example 
var ADB = ADBMobile; 
var purchasePrice = 39.95; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ItemPurchaseEvent"] = "ItemPurchaseEvent"; 
cdata["PurchaseItem"] = "Item453"; 
cdata["PurchasePrice"] = purchasePrice; 
ADB.Analytics.trackLifetimeValueIncrease(purchasePrice, cdata);
```

## Gedetailleerde acties {#section_7FF8B6A913A0460EAA4CAE835E32D8C1}

Met getimede acties kunt u de tijd en de totale tijd tussen het begin en het einde van een actie meten. De SDK berekent de hoeveelheid tijd in de sessie en de totale tijd (cross-session) die nodig is om de handeling te voltooien. Dit kan worden gebruikt om segmenten te bepalen om op tijd aan aankoop te vergelijken, niveau over te gaan, controlestroom, etc.

* Totaal aantal seconden in app tussen begin- en eindsessies
* Totaal aantal seconden tussen begin en eind (kloktijd)

```js
// Timed Action Start Example 
var ADB = ADBMobile; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ExperienceName"] = experience; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
```

```js
// Timed Action Update Example 
var ADB = ADBMobile; 
var cdataUpdate = new Windows.Foundation.Collections.PropertySet(); 
cdataUpdate["ImageLiked"] = imageName; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata); 
```

```js
// Timed Action End Example 
var ADB = ADBMobile; 
ADB.Analytics.trackTimedActionEnd("TimeUntilPurchase");
```