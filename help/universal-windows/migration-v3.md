---
description: In deze sectie wordt beschreven hoe u van de 3.x-versie van een vorige Windows Mobile SDK naar de Universal Windows Platform 4.x SDK voor Experience Cloud Solutions kunt migreren.
solution: Experience Cloud Services,Analytics
title: Migreren naar 4.x
topic-fix: Developer and implementation
uuid: bdd6c5cd-3892-4e99-b69e-77105ad66e25
exl-id: 68de505b-dcff-4a78-9f01-b1d103846281
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---

# Migreren naar de 4.x SDK&#39;s{#migrate-to-x}

In deze sectie wordt beschreven hoe u van de 3.x-versie van de Windows Mobile SDK naar de Universal Windows Platform 4.x SDK voor Experience Cloud Solutions kunt migreren.

Met de overgang naar versie 4.x is alle functionaliteit nu toegankelijk via statische methoden. U hoeft uw eigen objecten niet meer bij te houden.

In de volgende secties vindt u een migratie van versie 3.x naar versie 4.x.

## Ongebruikte eigenschappen verwijderen {#section_145222EAA20F4CC2977DD883FDDBBFC5}

U hebt waarschijnlijk een nieuwe `ADBMobileConfig.json` bestand bij uw download. Dit bestand bevat toepassingsspecifieke, algemene instellingen en vervangt de meeste configuratievariabelen die in vorige versies werden gebruikt.

Hier is een voorbeeld van een `ADBMobileConfig.json` bestand:

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

### Migreren vanaf 3.x

De volgende tabel bevat een lijst met variabelen in de 3.x SDK&#39;s en de nieuwe naam in de 4.x SDK&#39;s:

| Configuratievariabele/Methode | Variabele in het dialoogvenster `ADBMobileConfig.json` bestand. |
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

In plaats van de webfocus te gebruiken `Track` en `TrackLink` De vraag, versie 4 SDK gebruikt twee methodes die een beetje zinzamer in de mobiele wereld maken:

* `TrackState` Frames zijn de weergaven die beschikbaar zijn in uw app, zoals &#39;thuisdashboard&#39;, &#39;app-instellingen&#39;, &#39;winkelwagentje&#39; enzovoort. Deze statussen lijken op pagina&#39;s op een website, en `trackState` roept stijgende paginameningen.

* `TrackAction` Handelingen zijn de dingen die in uw app gebeuren en die u wilt meten, zoals &#39;logons&#39;, &#39;bannertiketten&#39;, &#39;feed-abonnementen&#39; en andere meetwaarden. Deze vraag verhoogt geen paginameningen.

De `contextData` parameter voor beide methoden bevat naam-waardeparen die als contextgegevens worden verzonden.

### Gebeurtenissen, profielen, variabelen

Als je naar de [Methoden van SDK](/help/universal-windows/c-configuration/methods.md)U vraagt zich waarschijnlijk af waar u gebeurtenissen, eVars, profielen, erfgenamen en lijsten wilt instellen. In versie 4 kunt u deze typen variabelen niet meer rechtstreeks in uw app toewijzen. In plaats daarvan gebruikt de SDK contextgegevens en verwerkingsregels om uw toepassingsgegevens toe te wijzen aan analytische variabelen voor rapportage.

De verwerkingsregels bieden de volgende voordelen:

* U kunt de gegevenstoewijzing wijzigen zonder een update naar de App Store te verzenden.
* U kunt betekenisvolle namen voor gegevens gebruiken in plaats van het plaatsen van variabelen die voor een rapportreeks specifiek zijn.
* Het verzenden van extra gegevens heeft weinig effect. Deze waarden worden pas in rapporten weergegeven als ze met verwerkingsregels zijn toegewezen.

Zie voor meer informatie de *Verwerkingsregels* sectie in [Overzicht van analysemogelijkheden](/help/universal-windows/analytics/analytics.md).

Waarden die u rechtstreeks toewijst aan variabelen, moeten worden toegevoegd aan contextgegevens. Dit betekent dat `SetProp`, `SetEvar`en toewijzingen aan permanente contextgegevens moeten allemaal worden verwijderd en de waarden moeten aan contextgegevens worden toegevoegd.

### AppSection/Server, GeoZip, transactie-id, Campaign en andere standaardvariabelen

In plaats daarvan moeten alle andere gegevens die u instelde voor het meetobject, inclusief de hierboven vermelde variabelen, worden toegevoegd aan de contextgegevens. De enige gegevens die worden verzonden met een `TrackState` of `TrackAction` de vraag is de lading in `data` parameter.

**Trackingaanroepen vervangen**

Door uw code, vervang de volgende methodes met een vraag aan `trackState` of `trackAction`:

**Migreren vanaf 3.x:**

* TrackAppState (TrackState)
* TrackEvents (TrackAction)
* Track (TrackAction)
* TrackLinkURL (TrackAction)

## Aangepaste id-service {#section_2CF930C13BA64F04959846E578B608F3}

Vervang de `visitorID` variabele met een aanroep van `setUserIdentifier`.

## Offline bijhouden {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline bijhouden is ingeschakeld in het dialoogvenster `ADBMobileConfig.json` bestand. Alle andere off-line configuratie wordt gedaan automatisch.

Door uw code, verwijder vraag aan de volgende methodes:

**Migreren vanaf 3.x:**

* SetOnline
* SetOffline

## Variabele voor producten {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Aangezien de productvariabele niet beschikbaar is in verwerkingsregels, kunt u de volgende syntaxis gebruiken om `products`:

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

De waarde van `"&&products"` (in dit voorbeeld is de waarde `";Cool Shoe`&quot;) moet de syntaxis van de producttekenreeks volgen voor het type gebeurtenis dat u bijhoudt.
