---
description: Informatie die u helpt bij het gebruik van het bestand ADBMobile JSON Config.
solution: Experience Cloud Services,Analytics
title: ADBMobileConfig.json config
topic-fix: Developer and implementation
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
exl-id: 57d50d30-651c-4943-835e-1cbce7467baf
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 1%

---

# ADBMobileConfig.json-configuratiebestand {#adbmobileconfig-json-config}

Informatie die u helpt bij het gebruik van het bestand ADBMobile JSON Config.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target en Audience Manager. Methoden worden vooraf bepaald volgens de oplossing. De methodes van de configuratie worden vooraf bepaald met &quot;Config.&quot;

* **Rsids**

   (**Vereist door Analytics**) Een of meer rapportsuites voor het ontvangen van analysegegevens. Meerdere rapportsuite-id&#39;s moeten worden gescheiden door komma&#39;s zonder tussenruimte.

   * Hier volgt de syntaxis voor deze methode:

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Vereist door Analytics en Audience Management**). Analytics or Audience Management Server, based on the parent node. Deze variabele moet worden gevuld met het serverdomein, zonder een `"https://"` of `"https://"` protocolvoorvoegsel. Het protocolvoorvoegsel wordt automatisch verwerkt door de bibliotheek op basis van de `ssl` variabele.

   Indien `ssl` is `true`, wordt een veilige verbinding gemaakt met deze server. Indien `ssl`is `false`Er wordt een niet-beveiligde verbinding gemaakt met deze server.

* **charset**

   Definieert de tekenset die u gebruikt voor de gegevens die naar Analytics worden verzonden. De charset wordt gebruikt om binnenkomende gegevens om te zetten in UTF-8 voor opslag en rapportage. Zie voor meer informatie de [charSet](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/charset.html) in de documentatie van Adobe Analytics.

* **ssl**

   Schakelt in (`true`) of schakelt uit (`false`) meetgegevens verzenden via SSL (`HTTPS`). De standaardwaarde is `false`.

* **offlineEnabled**

   Indien ingeschakeld (`true`), worden treffers een rij gevormd terwijl het apparaat offline is en later wordt verzonden wanneer het apparaat online is. Uw rapportsuite moet zijn ingeschakeld voor tijdstempels om offline tracering te kunnen gebruiken.

   Als tijdstempels zijn ingeschakeld in uw rapportsuite, kunt u `offlineEnabled` configuration, eigenschap *moet* zijn `true`. als de rapportsuite geen tijdstempel heeft, `offlineEnabled` configuration, eigenschap *moet* zijn `false`.

   Als dit niet correct wordt gevormd, zullen de gegevens worden verloren. Neem contact op met de klantenservice als u niet zeker weet of een rapportenpakket is ingeschakeld. Als u momenteel AppMeasurement-gegevens rapporteert aan een rapportsuite die ook gegevens uit JavaScript verzamelt, moet u mogelijk een aparte rapportsuite voor mobiele gegevens instellen of een aangepaste tijdstempel opnemen voor alle JavaScript-treffers met behulp van de optie `s.timestamp` variabele.

   De standaardwaarde is `false`.

* **lifecycleTimeout**

   Hiermee geeft u de tijdsduur in seconden op die moet verstrijken tussen het starten van de app voordat de start als een nieuwe sessie wordt beschouwd. Deze time-out is ook van toepassing wanneer uw toepassing naar de achtergrond wordt verzonden en opnieuw wordt geactiveerd. De tijd die uw toepassing op de achtergrond doorbrengt, wordt niet opgenomen in de sessieduur.

   De standaardwaarde is 300 seconden.

* **batchLimit**

   Tanden batchgewijs verzenden.

   Als u bijvoorbeeld instelt op `50`, worden de klappen een rij gevormd tot 50 wordt opgeslagen, dan worden alle een rij gevormde klappen verzonden. Vereisten `offlineEnabled=true`en de standaardwaarde is `0` (Geen batchverwerking).

* **privacyDefault**

   De opties zijn:

   * `optedin` - treffers worden onmiddellijk verzonden.
   * `optedout` - treffers worden genegeerd.
   * `optunknown` - Als uw rapportsuite is ingeschakeld voor tijdstempels, worden treffers opgeslagen totdat de status van de privacy verandert in aanmelden (resultaten worden verzonden) of Afmelden (resultaten worden verwijderd). Als uw rapportsuite niet is ingeschakeld voor tijdstempels, worden treffers genegeerd totdat de privacystatus verandert en u zich aanmeldt.

      Hiermee stelt u alleen de standaardwaarde in. Als deze waarde ooit in code wordt geplaatst of veranderd, dan wordt de waarde die door de code wordt geplaatst bewaard in lokale opslag en wordt gebruikt vooruit tot het wordt veranderd, of de app wordt verwijderd en dan opnieuw geïnstalleerd.

      De standaardwaarde is `optedin`.

* **poi**

   Elke POI-array bevat de POI-naam, breedte, lengte en straal (in meters) voor het gebied van het punt. De POI-naam kan elke tekenreeks zijn. Wanneer een `trackLocation` wordt de vraag verzonden, als de huidige coördinaten binnen een bepaalde POI zijn, wordt een variabele van contextgegevens bevolkt en verzonden met `trackLocation` vraag.

   * Hier is het codevoorbeeld voor deze variabele:

      ```js
       "poi" [ 
                ["san francisco",37.757144,-122.44812,7000], 
                ["santa cruz",36.972935,-122.01725,600] 
             ]
      ```

* **clientCode**

   (**Vereist door doel**) Uw toegewezen clientcode.

* **timeout**

   Hiermee bepaalt u hoe lang het doel wacht op een reactie.

Hieronder ziet u een voorbeeld van een `ADBMobileConfig.json` bestand:

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
  "timeout" : 1
 },
 "audienceManager" : {
  "server" : "myServer.demdex.com"
 }
}
```
