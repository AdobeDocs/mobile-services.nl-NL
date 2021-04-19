---
description: In deze sectie wordt beschreven hoe u van de 3.x-versie van een eerdere Windows Mobile SDK naar de Windows 8.1 Universal App Store 4.x SDK voor Experience Cloud Solutions kunt migreren.
seo-description: In deze sectie wordt beschreven hoe u van de 3.x-versie van een eerdere Windows Mobile SDK naar de Windows 8.1 Universal App Store 4.x SDK voor Experience Cloud Solutions kunt migreren.
seo-title: Migreren naar de 4.x SDK's
solution: Experience Cloud,Analytics
title: Migreren naar de 4.x SDK's
topic-fix: Developer and implementation
uuid: e0fe3b7b-cda5-4a91-834c-2c7e17a501a3
exl-id: d6dc34f2-61b7-4026-a66a-19284e21e69c
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 0%

---

# Migreren naar de 4.x SDK&#39;s {#migrate-to-the-x-sdks}

In deze sectie wordt beschreven hoe u van de 3.x-versie van een eerdere Windows Mobile SDK naar de Windows 8.1 Universal App Store 4.x SDK voor Experience Cloud Solutions kunt migreren.

Met de overgang naar versie 4.x is alle functionaliteit nu toegankelijk via statische methoden, zodat u uw eigen objecten niet meer kunt bijhouden.

In de volgende secties vindt u een migratie van versie 3.x naar versie 4.x.

## Ongebruikte eigenschappen {#section_145222EAA20F4CC2977DD883FDDBBFC5} verwijderen

U hebt waarschijnlijk een nieuw `ADBMobileConfig.json`-bestand opgemerkt dat bij uw download is opgenomen. Dit bestand bevat toepassingsspecifieke, algemene instellingen en vervangt de meeste configuratievariabelen die in vorige versies werden gebruikt. Hier volgt een voorbeeld van een `ADBMobileConfig.json`-bestand:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
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

De volgende lijsten maken een lijst van de configuratievariabelen die u naar het configuratiedossier moet bewegen. Verplaats de waarde die voor de variabele in de eerste kolom wordt geplaatst naar de variabele in de tweede kolom, en verwijder dan de oude configuratievariabele uit uw code.

## Migreren vanaf 3.x

| Configuratievariabele/Methode | Variabele in het `ADBMobileConfig.json`-bestand. |
|--- |--- |
| offlineTrackingEnabled | &quot;offlineEnabled&quot; |
| reportSuiteIDs | &quot;sids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| setOfflineHitLimit | Verwijderen, niet meer gebruikt. |
| linkTrackVars | Verwijderen, niet meer gebruikt. |
| linkTrackEvents | Verwijderen, niet meer gebruikt. |

## Trackaanroepen en trackingvariabelen bijwerken {#section_96E7D9B3CDAC444789503B7E7F139AB9}

In plaats van de webgerichte `Track`- en `TrackLink`-aanroepen te gebruiken, gebruikt de versie 4-SDK twee methoden die in de mobiele wereld wat meer zin hebben:

* `TrackState` Frames zijn de weergaven die beschikbaar zijn in uw app, zoals &#39;thuisdashboard&#39;, &#39;app-instellingen&#39;, &#39;winkelwagentje&#39; enzovoort. Deze staten zijn vergelijkbaar met pagina&#39;s op een website en `trackState` roept de weergave van de verhogende pagina op.

* `TrackAction` Handelingen zijn de dingen die in uw app gebeuren en die u wilt meten, zoals &#39;logons&#39;, &#39;bannertiketten&#39;, &#39;feed-abonnementen&#39; en andere meetwaarden. Deze vraag verhoogt geen paginameningen.

De parameter `contextData` voor beide methoden bevat naam-waardeparen die als contextgegevens worden verzonden.

## Gebeurtenissen, Props, Vars

Als u [SDK methodes](/help/windows-appstore/c-configuration/methods.md) hebt bekeken, bent u waarschijnlijk benieuwd waar te om gebeurtenissen, steunen, steunen, erfgenamen, en lijsten te plaatsen. In versie 4 kunt u deze typen variabelen niet meer rechtstreeks in uw app toewijzen. In plaats daarvan gebruikt de SDK contextgegevens en verwerkingsregels om uw toepassingsgegevens toe te wijzen aan analytische variabelen voor rapportage.

De verwerkingsregels bieden u verschillende voordelen:

* U kunt de gegevenstoewijzing wijzigen zonder een update naar de App Store te verzenden.
* U kunt betekenisvolle namen voor gegevens gebruiken in plaats van het plaatsen van variabelen die voor een rapportreeks specifiek zijn.
* Het verzenden van extra gegevens heeft weinig effect. Deze waarden worden pas in rapporten weergegeven als ze met verwerkingsregels zijn toegewezen.

Zie *Verwerkingsregels* in [Analytics](/help/windows-appstore/analytics/analytics.md) voor meer informatie.

Waarden die u rechtstreeks toewijst aan variabelen, moeten worden toegevoegd aan contextgegevens. Dit betekent dat aanroepen naar `SetProp`, `SetEvar` en toewijzingen naar permanente contextgegevens allemaal moeten worden verwijderd en de waarden moeten worden toegevoegd aan contextgegevens.

**AppSection/Server, GeoZip, Transaction ID, Campaign en andere standaardvariabelen**

Alle andere gegevens die u instelde voor het meetobject, inclusief de hierboven vermelde variabelen, moeten in plaats daarvan worden toegevoegd aan contextgegevens.

Om het eenvoudig te zetten, de enige gegevens die met een `TrackState` of `TrackAction` vraag worden verzonden is de lading in de `data` parameter.

### Trackingaanroepen vervangen

Door uw code, vervang de volgende methodes met een vraag aan `trackState` of `trackAction`:

### Migreren vanaf 3.x

* `TrackAppState` (TrackState)
* `TrackEvents` (TrackAction)
* `Track` (TrackAction)
* `TrackLinkURL` (TrackAction)

## Aangepaste bezoeker-id {#section_2CF930C13BA64F04959846E578B608F3}

Vervang de `visitorID` variabele met een vraag aan `setUserIdentifier`.

## Offline bijhouden {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline bijhouden is ingeschakeld in het `ADBMobileConfig.json`-bestand. Alle andere off-line configuratie wordt gedaan automatisch.

Door uw code, verwijder vraag aan de volgende methodes:

### Migreren vanaf 3.x

* `SetOnline`
* `SetOffline`

## Variabele {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Aangezien de productvariabele niet beschikbaar is in verwerkingsregels, kunt u de volgende syntaxis gebruiken om `products` te plaatsen:

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

In dit voorbeeld is de waarde van `"&&products"` `";Cool Shoe`&quot; en moet deze de syntaxis van de producttekenreeks volgen voor het type gebeurtenis dat u bijhoudt.
