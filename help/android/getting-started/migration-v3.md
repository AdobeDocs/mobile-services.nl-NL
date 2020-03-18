---
description: Met deze informatie kunt u migreren van de 3.x- of 2.x-versie van de Android-bibliotheek naar versie 4.x.
keywords: android;library;mobile;sdk
seo-description: Met deze informatie kunt u migreren van de 3.x- of 2.x-versie van de Android-bibliotheek naar versie 4.x.
seo-title: Migreren naar de Android 4.x-bibliotheek
solution: Marketing Cloud,Analytics
title: Migreren naar de Android 4.x-bibliotheek
topic: Developer and implementation
uuid: 906e83bb-2faf-4aa2-ac9b-3fba6b833c7e
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migreren naar de Android 4.x-bibliotheek {#migrating-to-the-android-x-library}

Met deze informatie kunt u migreren van de 3.x- of 2.x-versie van de Android-bibliotheek naar versie 4.x.

>[!IMPORTANT]
>
>De SDK gebruikt `SharedPreferences` om gegevens op te slaan die nodig zijn voor het berekenen van unieke gebruikers, levenscyclusmetriek en andere gegevens met betrekking tot de belangrijkste SDK-functionaliteit.  Als u de waarden in de SDK wijzigt of verwijdert, kan onverwacht gedrag leiden tot inconsistenties in de gegevens. `SharedPreferences`

In de bibliotheek van versie 4.x, worden de openbare methodes geconsolideerd in één kopbal. Bovendien is alle functionaliteit nu toegankelijk via methoden op klasseniveau. U hoeft dus geen aanwijzingen, instanties of singletons bij te houden.

## Gebeurtenissen, profielen en eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

In versie 4 kunt u geen variabelen meer toewijzen, zoals gebeurtenissen, eVars, profielen, erfgenamen en lijsten in uw app. In plaats daarvan gebruikt de SDK contextgegevens en verwerkingsregels om uw toepassingsgegevens toe te wijzen aan analytische variabelen voor rapportage.

De verwerkingsregels bieden de volgende voordelen:

* U kunt de gegevenstoewijzing wijzigen zonder een update naar de App Store te verzenden.
* U kunt betekenisvolle namen voor gegevens gebruiken in plaats van het plaatsen van variabelen die voor een rapportreeks specifiek zijn.
* Het verzenden van extra gegevens heeft weinig effect.

   Deze waarden worden pas in rapporten weergegeven als ze met verwerkingsregels zijn toegewezen.

>[!TIP]
>
>De waarden die u rechtstreeks aan variabelen toewees zouden aan HashMap moeten worden toegevoegd. `data`

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

## Het configuratiebestand verplaatsen en migreren naar versie 4 {#section_0B844235E0B04DD4B36976A73DB28FB5}

De volgende lijsten maken een lijst van de configuratievariabelen die u naar het configuratiedossier moet bewegen.

### Het configuratiebestand verplaatsen

1. Verplaats de waarde die voor de variabele in de eerste kolom is ingesteld naar de variabele in de tweede kolom.
1. Verwijder de oude configuratievariabele uit uw code.

### Migreren van versie 3.x

Als u van versie 3.x naar 4 wilt migreren, verplaatst u de configuratievariabele/methodewaarde naar de `ADBMobileConfig.json` variabele.

| Configuratievariabele of -methode | Variabele in het `ADBMobileConfig.json` bestand |
|--- |--- |
| setOfflineTrackingEnabled | &quot;offlineEnabled&quot; |
| setOfflineHitLimit | &quot;batchLimit&quot; |
| reportSuiteIDs | &quot;sids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | Verwijderen, niet meer gebruikt. |
| linkTrackEvents | Verwijderen, niet meer gebruikt. |

### Migreren van versie 2.x

Als u van versie 2.x naar versie 4 wilt migreren, verplaatst u de waarde van de eerste kolom naar de variabele in de tweede kolom.

| Configuratievariabele | Variabele in het `ADBMobileConfig.json` bestand |
| --- |--- |
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
| tijdstempel | Verwijderen, niet meer configureerbaar. |
| dc | Verwijderen, niet meer gebruikt. |
| userAgent | Verwijderen, niet meer configureerbaar. |
| dynamicVariablePrefix | Verwijderen, niet meer gebruikt. |
| bezoekerNamespace | Verwijderen, niet meer gebruikt. |
| usePlugins | Verwijderen, niet meer gebruikt. |
| useBestPractices alle aanroepen naar churn measurement ( getChurnInstance) | Verwijderen, vervangen door Levenscyclusstatistieken. |

## Trackaanroepen en trackingvariabelen bijwerken {#section_96E7D9B3CDAC444789503B7E7F139AB9}

In plaats van de web-focused `track` en `trackLink` vraag te gebruiken, gebruikt versie 4 SDK de volgende methodes:

* `trackState`, dit zijn de weergaven die beschikbaar zijn in uw app, zoals `home dashboard`, `app settings`, `cart`enzovoort.

   Deze staten zijn vergelijkbaar met pagina&#39;s op een website en `trackState` roepen paginaweergaven met meer pagina&#39;s aan.

* `trackAction` acties, zoals `logons`, `banner taps`, `feed subscriptions`enzovoort, die in uw app voorkomen en die u wilt meten.

De `contextData` parameter voor beide methoden is een `HashMap<String, Object>`naam, die de naam-waardeparen bevat die als contextgegevens worden verzonden.

## Gebeurtenissen, profielen en eVars

In versie 4 kunt u niet langer rechtstreeks in uw app variabelen zoals gebeurtenissen, eVars, props, haren en lijsten toewijzen. De SDK gebruikt nu contextgegevens en verwerkingsregels om uw toepassingsgegevens toe te wijzen aan analytische variabelen voor rapportage.

De verwerkingsregels bieden de volgende voordelen:

* U kunt de gegevenstoewijzing wijzigen zonder een update naar de App Store te verzenden.
* U kunt betekenisvolle namen voor gegevens gebruiken in plaats van het plaatsen van variabelen die voor een rapportreeks specifiek zijn.
* Het verzenden van extra gegevens heeft weinig effect.

   Deze waarden worden pas in rapporten weergegeven als ze met verwerkingsregels zijn toegewezen. Voor meer informatie, zie de Regels en de Gegevens [van de](/help/android/getting-started/proc-rules.md)Verwerking.

Waarden die u rechtstreeks toewijst aan variabelen, moeten worden toegevoegd aan de `data` HashMap. Dit betekent dat aanroepen naar `setProp`, `setEvar`en toewijzingen aan permanente contextgegevens moeten worden verwijderd en dat de waarden aan de `data` parameter moeten worden toegevoegd.

## AppSection/server, GeoZip, transactie-id, Campaign en andere standaardvariabelen

De gegevens die u op het metingsvoorwerp, met inbegrip van de hierboven vermelde variabelen plaatste, zouden aan HashMap moeten worden toegevoegd. `data` De enige gegevens die met een `trackState` of een `trackAction` vraag worden verzonden zijn de lading in de `data` parameter.

### Trackingaanroepen vervangen

Vervang de volgende methoden door een aanroep van `trackState` of `trackAction`:

* **Migreren van versie 3.x**

   * `trackAppState (trackState)`
   * `trackEvents (trackAction)`
   * `track (trackAction)`
   * `trackLinkURL (trackAction)`

* **Migreren van versie 2.x**

   * `track (trackState)`
   * `trackLink (trackAction)`

## Aangepaste bezoeker-id {#section_2CF930C13BA64F04959846E578B608F3}

Vervang de `visitorID` variabele door een vraag aan `setUserIdentifier`.

## Offline bijhouden {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline bijhouden is ingeschakeld in het `ADBMobileConfig.json` bestand en alle andere offlineconfiguratie wordt automatisch uitgevoerd.

Verwijder vraag aan de volgende methodes:

**Versie 3.x**

* `setOnline`
* `setOffline`

**Versie 2.x**

* `forceOffline`
* `forceOnline`

## Variabele voor producten {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Voor meer informatie over de productvariabele, zie de variabele [van](/help/android/analytics-main/products/products.md)Producten.

