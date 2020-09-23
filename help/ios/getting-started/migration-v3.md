---
description: Met deze informatie kunt u migreren van versie 3.x of 2.x van de iOS-bibliotheek naar versie 4.x.
seo-description: Met deze informatie kunt u migreren van versie 3.x of 2.x van de iOS-bibliotheek naar versie 4.x.
seo-title: Migreren naar de 4.x iOS-bibliotheek
solution: Experience Cloud,Analytics
title: Migreren naar de 4.x iOS-bibliotheek
topic: Developer and implementation
uuid: 5668972b-f355-4e03-9df0-8c82ddf6809b
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 2%

---


# Migreren naar de 4.x iOS-bibliotheek{#migrating-to-the-x-ios-library}

Met deze informatie kunt u migreren van versie 3.x of 2.x van de iOS-bibliotheek naar versie 4.x.

>[!IMPORTANT]
>
>De SDK gebruikt `NSUserDefaults` om gegevens op te slaan die nodig zijn voor het berekenen van unieke gebruikers, levenscyclusmetriek en andere gegevens met betrekking tot de belangrijkste SDK-functionaliteit.  Als u de waarden in de SDK wijzigt of verwijdert, kan onverwacht gedrag leiden tot inconsistenties in de gegevens. `NSUserDefaults`

In versie 4.x van de iOS SDK-bibliotheek worden de methoden public geconsolideerd in één header. De functionaliteit is nu ook toegankelijk via methoden op klasseniveau, zodat u geen aanwijzingen, instanties of singletons hoeft bij te houden.

## Gebeurtenissen, profielen en eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

In versie 4 kunt u niet langer rechtstreeks in uw app variabelen zoals gebeurtenissen, eVars, props, haren en lijsten toewijzen. In plaats daarvan gebruikt de SDK contextgegevens en verwerkingsregels om uw toepassingsgegevens toe te wijzen aan analytische variabelen voor rapportage.

De verwerkingsregels bieden de volgende voordelen:

* U kunt de gegevenstoewijzing wijzigen zonder een update naar de App Store te verzenden.
* U kunt betekenisvolle namen voor gegevens gebruiken in plaats van het plaatsen van variabelen die voor een rapportreeks specifiek zijn.
* Het verzenden van extra gegevens heeft weinig effect.

   Deze waarden worden pas in rapporten weergegeven als ze met verwerkingsregels zijn toegewezen.

>[!TIP]
>
>Waarden die u rechtstreeks toewijst aan variabelen, moeten nu worden toegevoegd aan het `data` NSDictionary.

## Ongebruikte eigenschappen verwijderen {#section_145222EAA20F4CC2977DD883FDDBBFC5}

Het nieuwe `ADBMobileConfig.json` bestand bevat toepassingsspecifieke, algemene instellingen en vervangt de meeste configuratievariabelen die in vorige versies werden gebruikt. Hier volgt een voorbeeld van een `ADBMobileConfig.json` bestand:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 5, 
        "privacyDefault" : "optedin", 
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 5 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```


### Het configuratiebestand verplaatsen

Het configuratiebestand verplaatsen:

1. Verplaats de waarde die voor de variabele in de eerste kolom is ingesteld naar de variabele in de tweede kolom.
1. Verwijder de oude configuratievariabele uit uw code.

### Migratiegegevens

De volgende lijsten maken een lijst van de configuratievariabelen die u naar het configuratiedossier moet bewegen.

#### Migreren van versie 3.x

Verplaats de waarde van de eerste kolom naar de variabele in de tweede kolom.

| Configuratievariabele | Variabele in het `ADBMobileConfig.json` bestand |
|--- |--- |
| offlineTrackingEnabled | &quot;offlineEnabled&quot; |
| offlineHitLimit | &quot;batchLimit&quot; |
| reportSuiteIDs | &quot;sids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | Verwijderen, niet meer gebruikt. |
| linkTrackEvents | Verwijderen, niet meer gebruikt. |


#### Migreren van versie 2.x

Verplaats de waarde van de eerste kolom naar de variabele in de tweede kolom.

| Configuratievariabele | Variabele in het `ADBMobileConfig.json` bestand |
|--- |--- |
| trackOffline | &quot;offlineEnabled&quot; |
| offlineLimit | &quot;batchLimit&quot; |
| account | &quot;sids&quot; |
| trackingServer | &quot;server&quot;, verwijdert u het `"https://"` voorvoegsel. Het protocolvoorvoegsel wordt automatisch toegevoegd op basis van de instelling &quot;ssl&quot;. |
| trackingServerSecure | Verwijderen. Voor veilige verbindingen definieert u &quot;server&quot; en schakelt u &quot;ssl&quot; in. |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | Verwijderen, niet meer gebruikt. |
| linkTrackEvents | Verwijderen, niet meer gebruikt. |
| timestamp | Verwijderen, niet meer configureerbaar. |
| dc | Verwijderen, niet meer gebruikt. |
| userAgent | Verwijderen, niet meer configureerbaar. |
| dynamicVariablePrefix | Verwijderen, niet meer gebruikt. |
| visitorNamespace | Verwijderen, niet meer gebruikt. |
| usePlugins | Verwijderen, niet meer gebruikt. |
| useBestPractices alle aanroepen naar churn measurement ( getChurnInstance ) | Verwijderen, vervangen door levenscyclusmetriek. Zie [Levenscyclusstatistieken](//help/ios/metrics.md)voor meer informatie. |


## Trackaanroepen en trackingvariabelen bijwerken {#section_96E7D9B3CDAC444789503B7E7F139AB9}

In plaats van de web-focused `track` en `trackLink` vraag te gebruiken, gebruikt versie 4 SDK de volgende methodes:

* `trackState:data:` frames zijn de weergaven die beschikbaar zijn in uw app, zoals `home dashboard`, `app settings`, `cart`enzovoort.

   Deze staten zijn vergelijkbaar met pagina&#39;s op een website en `trackState` roepen paginaweergaven met meer pagina&#39;s aan.

* `trackAction:data:` handelingen, zoals `logons`, `banner taps`, `feed subscriptions`en andere metingen die in uw app voorkomen en die u wilt meten.

De `data` parameter voor beide methoden is een methode `NSDictionary` met naam-waardeparen die als contextgegevens worden verzonden.

### Gebeurtenissen, profielen, variabelen

In versie 4 kunt u niet langer rechtstreeks in uw app variabelen zoals gebeurtenissen, eVars, props, haren en lijsten toewijzen. De SDK gebruikt nu contextgegevens en verwerkingsregels om uw toepassingsgegevens toe te wijzen aan analytische variabelen voor rapportage.

De verwerkingsregels bieden de volgende voordelen:

* U kunt de gegevenstoewijzing wijzigen zonder een update naar de App Store te verzenden.
* U kunt betekenisvolle namen voor gegevens gebruiken in plaats van het plaatsen van variabelen die voor een rapportreeks specifiek zijn.
* Het verzenden van extra gegevens heeft weinig effect.

   Deze waarden worden pas in rapporten weergegeven als ze met verwerkingsregels zijn toegewezen. Voor meer informatie, zie de Regels en de Gegevens [van de](/help/ios/getting-started/proc-rules.md)Verwerking.

Waarden die u rechtstreeks aan variabelen hebt toegewezen, moeten in `data` `NSDictionary` plaats daarvan aan de variabelen worden toegevoegd. Dit betekent dat aanroepen naar `setProp`, `setEvar`en toewijzingen aan permanente contextgegevens allemaal moeten worden verwijderd en dat de waarden aan de `data` parameter moeten worden toegevoegd.

### AppSection/Server, GeoZip, transactie-id, Campaign en andere standaardvariabelen

De gegevens die u op het meetobject instelde, inclusief de hierboven vermelde variabelen, moeten in `data` `NSDictionary` plaats daarvan aan het object worden toegevoegd. De enige gegevens die met een `trackState` of een `trackAction` vraag worden verzonden zijn de lading in de `data` parameter.

### Trackingaanroepen vervangen

Vervang in uw code de volgende methoden door een aanroep van `trackState` of `trackAction`:

#### Migreren van versie 3.x

* `trackAppState (trackState)`
* `trackEvents (trackAction)`
* `track (trackAction)`
* `trackWithContextData (trackAction)`
* `trackLinkURL (trackAction)`

#### Migreren van versie 2.x

* `track (trackState)`
* `trackLink (trackAction)`

## Custom visitor ID {#section_2CF930C13BA64F04959846E578B608F3}

Vervang de `visitorID` variabele door een vraag aan `setUserIdentifier:`.

## Offline bijhouden {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline bijhouden is ingeschakeld in het `ADBMobileConfig.json` bestand en alle andere offlineconfiguratie wordt automatisch uitgevoerd.

In uw code, verwijder vraag aan de volgende methodes:

### Versie 3.x

* `setOnline`
* `setOffline`

### Versie 2.x

* `forceOffline`
* `forceOnline`

## Variabele voor producten {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Aangezien de productvariabele niet beschikbaar is in verwerkingsregels, kunt u de volgende syntaxis gebruiken om in te stellen `products`:

```objective-c
//create a processing rule to set the corresponding product event. 
// for example, set prodView event when context data a.action = "product view" 
[ADBMobile trackAction:@"LikeButtonClicked"  
                  data:@{@"&&products" : @";Cool Shoe"}];
```

![](assets/prod-view.png)