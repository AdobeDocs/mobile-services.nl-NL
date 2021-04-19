---
description: Met deze informatie kunt u migreren van de 3.x- of 2.x-versie van de Android-bibliotheek naar versie 4.x.
keywords: android;bibliotheek;mobile;sdk
seo-description: Met deze informatie kunt u migreren van de 3.x- of 2.x-versie van de Android-bibliotheek naar versie 4.x.
seo-title: Migreren naar de Android 4.x-bibliotheek
solution: Experience Cloud,Analytics
title: Migreren naar de Android 4.x-bibliotheek
topic-fix: Developer and implementation
uuid: 906e83bb-2faf-4aa2-ac9b-3fba6b833c7e
exl-id: 8061c1ab-aaaf-4d4c-9bd5-b2f80b6b06a3
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '884'
ht-degree: 2%

---

# Migreren naar de Android 4.x-bibliotheek {#migrating-to-the-android-x-library}

Met deze informatie kunt u migreren van de 3.x- of 2.x-versie van de Android-bibliotheek naar versie 4.x.

>[!IMPORTANT]
>
>De SDK gebruikt `SharedPreferences` om gegevens op te slaan die nodig zijn voor het berekenen van unieke gebruikers, levenscyclusmetriek en andere gegevens met betrekking tot de kernfunctionaliteit van SDK.  Als u de waarden in `SharedPreferences` wijzigt of verwijdert die door SDK worden verwacht, kan onverwacht gedrag in de vorm van gegevensinconsistenties resulteren.

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
>Waarden die u rechtstreeks aan variabelen hebt toegewezen, moeten worden toegevoegd aan de `data` HashMap.

## Ongebruikte eigenschappen {#section_145222EAA20F4CC2977DD883FDDBBFC5} verwijderen

Het nieuwe `ADBMobileConfig.json` dossier bevat toepassing-specifieke, globale montages, en vervangt de meeste configuratievariabelen die in vorige versies werden gebruikt. Hier volgt een voorbeeld van een `ADBMobileConfig.json`-bestand:

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

Om van versie 3.x aan 4 te migreren, verplaats de configuratievariabele/methodewaarde aan `ADBMobileConfig.json` variabele.

| Configuratievariabele of -methode | Variabele in het `ADBMobileConfig.json`-bestand |
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

| Configuratievariabele | Variabele in het `ADBMobileConfig.json`-bestand |
| --- |--- |
| trackOffline | &quot;offlineEnabled&quot; |
| offlineLimit | &quot;batchLimit&quot; |
| account | &quot;sids&quot; |
| trackingServer | &quot;server&quot;, verwijdert u het voorvoegsel `"https://"`. Het protocolvoorvoegsel wordt automatisch toegevoegd op basis van de instelling &quot;ssl&quot;. |
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
| useBestPractices alle aanroepen naar churn measurement ( getChurnInstance) | Verwijderen, vervangen door Levenscyclusstatistieken. |

## Trackaanroepen en trackingvariabelen bijwerken {#section_96E7D9B3CDAC444789503B7E7F139AB9}

In plaats van de web-focused `track` en `trackLink` vraag te gebruiken, gebruikt versie 4 SDK de volgende methodes:

* `trackState`, dit zijn de weergaven die beschikbaar zijn in uw app, zoals  `home dashboard`,  `app settings`,  `cart`enzovoort.

   Deze staten zijn vergelijkbaar met pagina&#39;s op een website en `trackState` roept de weergave van de verhogende pagina op.

* `trackAction` acties, zoals  `logons`,  `banner taps`,  `feed subscriptions`enzovoort, die in uw app voorkomen en die u wilt meten.

De parameter `contextData` voor beide methoden is een `HashMap<String, Object>`, die de naam-waardeparen bevat die als contextgegevens worden verzonden.

## Gebeurtenissen, profielen en eVars

In versie 4 kunt u niet langer rechtstreeks in uw app variabelen zoals gebeurtenissen, eVars, props, haren en lijsten toewijzen. De SDK gebruikt nu contextgegevens en verwerkingsregels om uw toepassingsgegevens toe te wijzen aan analytische variabelen voor rapportage.

De verwerkingsregels bieden de volgende voordelen:

* U kunt de gegevenstoewijzing wijzigen zonder een update naar de App Store te verzenden.
* U kunt betekenisvolle namen voor gegevens gebruiken in plaats van het plaatsen van variabelen die voor een rapportreeks specifiek zijn.
* Het verzenden van extra gegevens heeft weinig effect.

   Deze waarden worden pas in rapporten weergegeven als ze met verwerkingsregels zijn toegewezen. Zie [Regels en contextgegevens verwerken](/help/android/getting-started/proc-rules.md) voor meer informatie.

Waarden die u rechtstreeks toewijst aan variabelen, moeten worden toegevoegd aan de `data` HashMap. Dit betekent dat aanroepen naar `setProp`, `setEvar` en toewijzingen naar permanente contextgegevens moeten worden verwijderd en dat de waarden moeten worden toegevoegd aan de parameter `data`.

## AppSection/server, GeoZip, transactie-id, Campaign en andere standaardvariabelen

De gegevens die u op het metingsvoorwerp, met inbegrip van de hierboven vermelde variabelen plaatste, zouden aan `data` HashMap moeten worden toegevoegd. De enige gegevens die met een `trackState` of `trackAction` vraag worden verzonden is de lading in de `data` parameter.

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

Vervang de `visitorID` variabele met een vraag aan `setUserIdentifier`.

## Offline bijhouden {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline bijhouden is ingeschakeld in het `ADBMobileConfig.json`-bestand en alle andere offlineconfiguratie wordt automatisch uitgevoerd.

Verwijder vraag aan de volgende methodes:

**Versie 3.x**

* `setOnline`
* `setOffline`

**Versie 2.x**

* `forceOffline`
* `forceOnline`

## Variabele {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Voor meer informatie over de productvariabele, zie [Variabele van Producten](/help/android/analytics-main/products/products.md).
