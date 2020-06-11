---
description: Met deze informatie kunt u het configuratiebestand ADBMobile.json gebruiken.
seo-description: Met deze informatie kunt u het configuratiebestand ADBMobile.json gebruiken.
seo-title: ADBMobile JSON Config
solution: Marketing Cloud,Analytics
title: ADBMobile JSON Config
topic: Developer and implementation
uuid: 1decf605-7bc3-4e73-ad52-1ecd5821599e
translation-type: tm+mt
source-git-commit: 86ba045b44bf6553e80727c0d61ccdd9a552d16c
workflow-type: tm+mt
source-wordcount: '1678'
ht-degree: 4%

---


# ADBMobile JSON-configuratiebestand {#adbmobile-json-config}

Deze informatie helpt u de variabelen in het ADBMobile.json config- dossier begrijpen.

## `ADBMobileConfig.json` configuratiebestandsverwijzing {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

Hetzelfde configuratiebestand kan op meerdere platforms voor uw toepassing worden gebruikt:

>[!TIP]
>
>In **Android** moet het `ADBMobileConfig.json` bestand in de `assets` map worden geplaatst.

Hier volgt een lijst met de variabelen in het JSON-bestand en de minimale SDK-versie die u nodig hebt voor elke variabele:

* **verwerving**
   * Minimale SDK-versie: 4.1
   * Hiermee schakelt u aanschaf van mobiele apps in.
      * `server`Dit is de overnameserver die bij de eerste introductie voor een overnameverwijzing wordt gecontroleerd.
      * `appid`, dit is de gegenereerde id die deze toepassing op de overnameserver op unieke wijze identificeert.
   Als deze sectie ontbreekt, schakelt u de aanschaf van een mobiele toepassing in en downloadt u het configuratiebestand van de SDK opnieuw. Zie *referenceTimeout* in deze lijst met variabelen voor meer informatie.

* **analyticsForwardingEnabled**
   * De minimale SDK-versie is 4.8.0.
   * De standaardwaarde is `false`.

      De eigenschap in het `audienceManager` object. Als de Manager van het Publiek wordt gevormd, en `analyticsForwardingEnabled` wordt geplaatst aan `true`, door:sturen al verkeer Analytics ook aan de Manager van het Publiek.

* **backdateSessionInfo**
   * Minimale SDK-versie: 4.6.
   * Hiermee schakelt u de mogelijkheid voor de Adobe SDK in of uit om sessieinfo-hits te herstellen.

      Sessieinfo-hits bestaan momenteel uit crashes en sessielengte en kunnen worden in- of uitgeschakeld.

      **Het toelaten van of het onbruikbaar maken van Hits**

      * Als u de waarde instelt op `false`, worden de treffers **uitgeschakeld**. De SDK keert terug naar zijn gedrag van vóór 4.1 van het samenvatten van de zittingsinformatie voor de vorige zitting met de eerste slag van de verdere zitting. De SDK van Adobe voegt de sessiegegevens ook toe aan de huidige levenscyclus, waardoor het maken van een opgeblazen bezoek wordt voorkomen. Omdat er geen opgeblazen bezoeken meer ontstaan, neemt het aantal bezoeken onmiddellijk af.

      * Als u geen waarde opgeeft, wordt de standaardwaarde gebruikt `true`en worden treffers **ingeschakeld**. Wanneer de treffers worden toegelaten, backdates de SDK van Adobe de zittingsinfo aan 1 seconde na de definitieve slag in de vorige zitting. Dit betekent dat de neerstorting en zittingsgegevens met de correcte datum zullen correleren waarop zij voorkwamen. Eén bijwerking is dat de SDK een bezoek kan maken voor een melding met terugwerkende kracht. Bij elke nieuwe start van de toepassing wordt een hit hersteld.

         >[!IMPORTANT]
         >
         >De informatie van de zittingtreffer wordt van de achtergrond verzonden in een de servervraag van zittingsinfo en de extra servervraag zou kunnen van toepassing zijn.

* **batchLimit**
   * Minimale SDK-versie: 4.1
   * Drempel voor het aantal treffers dat in opeenvolgende vraag moet worden verzonden.

      Als de waarde bijvoorbeeld op 10 `batchLimit` is ingesteld, wordt elke hit vóór de tiende hit opgeslagen in de wachtrij. Wanneer de 10e hit binnenkomt, worden alle 10 treffers achtereenvolgens verzonden.

      De volgende informatie onthouden:

      * De standaardwaarde is `0`, wat betekent dat batchverwerking niet is ingeschakeld.
      * Vereist `offlineEnabled = true`.

* **charset**
   * Minimale SDK-versie: 4.0
   * Hiermee definieert u de tekenset die u gebruikt voor de gegevens die naar Analytics worden verzonden.

      De charset wordt gebruikt om binnenkomende gegevens om te zetten in UTF-8 voor opslag en rapportage.

* **clientCode**
   * Minimale SDK-versie: 4.0
   * Uw toegewezen clientcode.

      >[!IMPORTANT]
      >
      >Deze variabele wordt vereist door Doel.

* **coopUnsafe**
   * Minimale SDK-versie: 4.16.1
   * De Booleaanse eigenschap van het `marketingCloud` object dat, wanneer ingesteld op `true`, ervoor zorgt dat het apparaat wordt uitgeschakeld voor de codering apparaat van de Experience Cloud.
   * De standaardwaarde is `false`.
   * Deze instelling wordt **alleen** gebruikt voor klanten die via Device Co-op zijn ingericht.
   Voor leden van Coop van het Apparaat die deze waarde aan `true`vereisen, moet u met het team van Coop samenwerken om een blocklist vlag op uw Co-op rekening van het Apparaat te verzoeken. Er is geen zelfbedieningspad om deze markeringen in te schakelen.

   De volgende informatie onthouden:

   * Wanneer `coopUnsafe` is ingesteld op `true`, `coop_unsafe=1` worden deze altijd toegevoegd aan Audience Manager- en Bezoekersidentiteitscontroles.
   * Als u het door:sturen van de server-kant van de Analyse aan de Manager van het Publiek toelaat, zult u ook de `coop_unsafe=1` Bezoekingen van Analytics zien.


* **environmentId**
   * Minimale SDK-versie: 4.14
   * De id van de omgeving die u wilt gebruiken.

      U kunt een geldige id (`environmentId=8`) opgeven en als deze `environmentId` niet is opgenomen, wordt de standaardproductieomgeving gebruikt.

* **lifecycleTimeout**
   * Minimale SDK-versie: 4.0
   * De standaardwaarde is 300 seconden.

      Hiermee geeft u de tijdsduur in seconden op die moet verstrijken tussen het moment dat de app wordt gestart, maar voordat de toepassing als een nieuwe sessie wordt beschouwd. Deze time-out is ook van toepassing wanneer uw toepassing naar de achtergrond wordt verzonden en opnieuw wordt geactiveerd.

      De tijd die uw toepassing op de achtergrond doorbrengt, wordt niet opgenomen in de sessieduur.

* **berichten**

   * Minimale SDK-versie: 4.2
   * Deze optie wordt automatisch gegenereerd door Adobe Mobile-services en definieert de instellingen voor berichten in apps. Zie de onderstaande sectie *Berichtenbeschrijving* voor meer informatie.

* **offlineEnabled**

   * Minimale SDK-versie: 4.0
   * Indien ingeschakeld, worden treffers in een wachtrij geplaatst terwijl het apparaat offline is en later wordt verzonden wanneer het apparaat online is.

      Uw rapportsuite moet zijn ingeschakeld voor tijdstempels om offline tracering te kunnen gebruiken.

      De standaardwaarde is `false`.

      >[!IMPORTANT]
      >
      >Als tijdstempels op uw rapportreeks worden toegelaten, `offlineEnabled` moet **uw** configuratiebezit waar zijn. als uw rapportreeks niet timestamp toegelaten is, `offlineEnabled` moet **uw** configuratiebezit vals zijn.
      >
      >Als dit niet correct wordt gevormd, zullen de gegevens worden verloren. Als u niet zeker weet of een rapportsuite met tijdstempel is ingeschakeld, neemt u contact op met de klantenservice of downloadt u het configuratiebestand van Adobe Mobile-services.

      Als u momenteel AppMeasurement-gegevens rapporteert aan een rapportsuite die ook gegevens uit JavaScript verzamelt, moet u mogelijk een aparte rapportsuite voor mobiele gegevens instellen of een aangepaste tijdstempel opnemen in alle JavaScript-resultaten die de `s.timestamp` variabele gebruiken.

* **org**

   * Minimale SDK-versie: 4.3
   * Hiermee geeft u de Cloud-org-id voor de id-service op.

* **poi**
   * Minimale SDK-versie: 4.0
   * Elke POI-array (point of interest) bevat de POI-naam, breedte, lengte en straal in meters voor het gebied van het punt.

      De POI-naam kan elke tekenreeks zijn. Wanneer een `trackLocation` vraag wordt verzonden, als de huidige coördinaten binnen bepaalde POI zijn, wordt een variabele van contextgegevens bevolkt en verzonden met de `trackLocation` vraag.

      ```javascript
      "poi": [
                 ["san francisco",37.757144,-122.44812,7000]
                 ["santa cruz",36.972935,-122.01725,600]
             ]
      ```

      Vanaf versie 4.2 worden POI&#39;s gedefinieerd in de Adobe Mobile-interface en dynamisch gesynchroniseerd met het configuratiebestand van de toepassing. Voor deze synchronisatie is de `analytics.poi` instelling vereist:

      ```javascript
      “analytics.poi“: `https://assets.adobedtm.com/`
      …/yourfile.json”`,
      ```

      Als deze instelling niet is geconfigureerd, moet het `ADBMobile.json` bestand worden bijgewerkt om deze regel op te nemen. Zie [Voor u begint](/help/android/getting-started/requirements.md).

* **postback**
   * Minimale SDK-versie: 4.6
   * Hier is de definitie voor het &quot;callback&quot;berichtmalplaatje:

      ```javascript
      "payload":{
        "templateurl":"", //required will be token-expanded prior to being sent
        "templatebody":"", //optional - if this length > 0 POST will be used as transport method. This is a base64 encoded blob, which will be decoded and token-expanded prior to being sent.
        "contenttype": "", // optional - if this is length > 0 and POST type is selected this will be set as the Content-Type header.  if this is not supplied for a POST request, the default will be "application/x-www-form-urlencoded"
        "timeout": 0 // optional - number of seconds to wait before timing out.  Default is 2.}
      ```

      Het `payload` object in de code is een voorbeeldlading voor een berichtdefinitie die in het `ADBMobileConfig.json` bestand wordt weergegeven. Zie [Postbacks](/help/android/analytics-main/postbacks/postbacks.md)voor meer informatie.

* **privacyDefault**
   * Minimale SDK-versie: 4.0
   * De standaardwaarde is `optedin`.
      * De treffers `optedin`worden bijvoorbeeld direct verzonden.
      * De treffers `optedout`worden bijvoorbeeld genegeerd.
      * Als uw rapportsuite bijvoorbeeld is ingeschakeld voor tijdstempels, worden treffers opgeslagen totdat de privacystatus verandert in aanmelden (hits worden verzonden) of Afmelden (hits worden verwijderd). `optunknown`
      Als de tijdstempel-toegelaten rapportreeks niet is, worden de klappen verworpen tot de privacystatus aan verandert. `optedin` Hiermee wordt alleen de beginwaarde ingesteld. Als deze waarde is ingesteld of gewijzigd in code, wordt de nieuwe waarde gebruikt totdat deze opnieuw wordt gewijzigd of wanneer de app wordt verwijderd en opnieuw wordt geïnstalleerd.


* **referenceTimeout**
   * Minimale SDK-versie: 4.1
   * Aantal seconden dat de SDK wacht op gegevens van de verwervingsreferentie bij de eerste introductie voordat de time-out optreedt. Als u acquisitie gebruikt, raden we een time-out van 5 seconden aan.

      >[!IMPORTANT]
      >
      >Deze variabele wordt vereist door Opname. Als de variabele is ingesteld op `0` of niet is opgenomen, wacht de SDK niet op verwervingsgegevens en worden verwervingsgegevens niet bijgehouden.

* **remotes**
   * Minimale SDK-versie: 4.2
   * Deze optie wordt automatisch geconfigureerd en definieert de door Adobe gehoste eindpunten voor dynamische configuratiebestanden.

      De laatste updatetijd van elk configuratiedossier wordt gecontroleerd tegen de huidige versie bij elke lancering, en de updates worden gedownload en bewaard.
      * `analytics.poi` is het eindpunt voor ontvangen POI configuratie.
      * `messages` is het eindpunt voor ontvangen in-app berichtconfiguratie.

* **Rsids**
   * Minimale SDK-versie: 4.0
   * Een of meer rapportsuites voor het ontvangen van analysegegevens. Meerdere rapportsuite-id&#39;s moeten worden gescheiden door komma&#39;s zonder tussenruimte.

      ```javascript
        "rsids" "rsid"
      ```

      ```javascript
        "rsids" "rsid1,rsid2"
      ```

      >[!IMPORTANT]
      >
      >Deze variabele wordt vereist door Analytics.

* **server**
   * Minimale SDK-versie: 4.0
   * De Analytics- of Audience Management-server, gebaseerd op het bovenliggende knooppunt. Deze variabele zou met het serverdomein, zonder een `https://` of `https://` protocolprefix moeten worden bevolkt. Dit voorvoegsel wordt automatisch verwerkt door de bibliotheek en is gebaseerd op de `ssl` variabele. Als `ssl` `true`dit het geval is, wordt een veilige verbinding gemaakt met deze server. Als `ssl` `false`dit het geval is, wordt een niet-veilige verbinding gemaakt met deze server.

* **ssl**
   * Minimale SDK-versie: 4.0
   * De standaardwaarde is `false`.

      Schakelt de mogelijkheid in (`true`) of uit (`false`) om meetgegevens te verzenden met behulp van SSL (HTTPS).

      De definitie voor het &quot;callback&quot;berichtmalplaatje wordt hieronder getoond:

      ```javascript
      "payload": {
          "templateurl":"",//required-will be token-expanded prior to being sent 
          "templatebody": "", //optional - if this length >  0 POST will be used& as transport method. This is a base64 encoded blob, which will be  decoded and token-expanded prior to being sent.
          "contenttype": "" // optional - if this is length > 0 POST type is selected this will be set as the Content-Type header. if this is not supplied for a POST request, the default will be "application/x-www-form-urlencoded"
          "timeout": 0 // optional - number of seconds to wait before timing& out. Default is 2.}
      ```

* **timeout**
   * Minimale SDK-versie: 4.0
   * Hiermee bepaalt u hoe lang Doel wacht op een reactie.


## Voorbeeldbestand `ADBMobileConfig.json` {#section_4655EF79744649E5A5AE19E3224C472C}

Here is a sample `ADBMobileConfig.json` file:

```js
 { 
    "version": "2014-08-05T19:18:28.169Z", 
    "marketingCloud" : { 
        "org": "016D5C175213CCA80A490D05@AdobeOrg", 
        "coopUnsafe": false 
    }, 
    "target": { 
        "clientCode": "", 
        "timeout": 5, 
        "environmentId": 8 
    }, 
    "audienceManager": { 
        "server": "", 
        "analyticsForwardingEnabled": false 
    }, 
    "acquisition": { 
        "server": "c00.adobe.com", 
        "appid": "10a77a60192fbb628376e1b1daeeb65debf934e2c807e067ceb2963a41b165ee" 
    }, 
    "analytics": { 
        "rsids": "coolApp", 
        "server": "my.CoolApp.com", 
        "ssl": true, 
        "offlineEnabled": true, 
        "charset": "UTF-8", 
        "lifecycleTimeout": 300, 
        "privacyDefault": "optedin", 
        "batchLimit": 0, 
        "referrerTimeout": 5, 
        "poi": [ 
            ["san francisco",37.757144,-122.44812,7000],  
            ["santa cruz",36.972935,-122.01725,600] 
        ] 
    }, 
    "messages": [ 
        { 
            "messageId": "cb426565-a563-497a-a889-9dbeb451f8ae", 
            "template": "fullscreen", 
            "payload": { 
                 "html": "<!DOCTYPE html><html><head><meta charset=\"utf-8\" /><title></title><style></style></head><body><iframe src=\"https://www.adobe.com/\" frameborder=\"0\"></iframe></body></html>" 
            }, 
            "showOffline": false, 
            "showRule": "always", 
            "endDate": 2524730400, 
            "startDate": 0, 
            "audiences": [], 
            "triggers": [ 
                { 
                    "key": "pev2", 
                    "matches": "eq", 
                    "values": [ 
                        "AMACTION:custom" 
                    ] 
                } 
            ] 
        } 
    ], 
    "remotes": { 
        "analytics.poi": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0faadc2f9ed92bc00003b.json", 
        "messages": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0f9e2c2f9ed92bc000032.json" 
    } 
}
```

## Berichtenbeschrijving {#section_B97D654BA92149CE91F525268D7AD71F}

Het knooppunt Berichten wordt automatisch gegenereerd door Adobe Mobile-services en hoeft gewoonlijk niet handmatig te worden gewijzigd. De volgende beschrijving wordt gegeven voor het oplossen van problemendoeleinden:

* &quot;messageId&quot;
* Gegenereerde id, vereist
* &quot;template&quot;
   * &quot;alert&quot;, &quot;fullscreen&quot; of &quot;local&quot;
   * vereist

* &quot;showOffline&quot;
   * true of false
   * default is false

* &quot;showRule&quot;
   * &quot;always&quot;, &quot;once&quot; of &quot;UntilClick&quot;
   * vereist

* &quot;endDate&quot;
   * aantal seconden sinds 1 januari 1970
   * default is 2524730400

* &quot;startDate&quot;
   * aantal seconden sinds 1 januari 1970
   * default is 0

* &quot;payload&quot;
   * &quot;html&quot;
      * alleen fullScreen-sjabloon, vereist
      * html die het bericht bepaalt
   * &quot;afbeelding&quot;
      * alleen volledig scherm, optioneel
      * URL naar de afbeelding die moet worden gebruikt voor een afbeelding op volledig scherm
   * &quot;altImage&quot;
      * alleen volledig scherm, optioneel
      * naam van de gebundelde afbeelding die moet worden gebruikt als de URL is opgegeven in
         * afbeelding
         * is onbereikbaar
   * &quot;title&quot;
      * volledig scherm en waarschuwing, vereist
      * titeltekst voor een volledig scherm of waarschuwingsbericht
   * &quot;content&quot;
      * waarschuwing en lokale melding vereist
      * subtekst voor een waarschuwingsbericht of meldingstekst voor een lokaal meldingsbericht
   * &quot;confirm&quot;
      * waarschuwing, optioneel
      * tekst gebruikt in de bevestigingsknop
   * &quot;cancel&quot;
      * waarschuwing, vereist
      * tekst gebruikt in de knop Annuleren
   * &quot;url&quot;
      * waarschuwing, optioneel
      * url-actie die moet worden geladen als op de bevestigingsknop wordt geklikt
   * &quot;wait&quot;
      * lokale melding, vereist
      * hoeveelheid tijd die moet worden gewacht (in seconden) om het lokale bericht te plaatsen nadat aan de criteria is voldaan



* &quot;audiences&quot;
   * array met objecten die bepaalt hoe het bericht moet worden weergegeven
   * &quot;key&quot;
      * variabelenaam die moet worden gezocht in de hit, vereist
* &quot;matches&quot;
   * type matcher gebruikt bij de vergelijking
   * eq = gelijk aan
   * ne = is niet gelijk aan
   * co = contains
   * nc = bevat niet
   * sw = begint met
   * new = eindigt met
   * ex = bestaat
   * nx = bestaat niet
   * lt = minder dan
   * le = kleiner dan of gelijk aan
   * gt = groter dan
   * ge = groter dan of gelijk aan
* &quot;values&quot;
   * een array van waarden die worden gebruikt om overeen te komen met de waarde van de variabele die in
      * key
      * met het matchingentype in
      * matches
* &quot;triggers&quot;
   * hetzelfde als het publiek, maar dit is de actie in plaats van het publiek
   * &quot;key&quot;
   * &quot;matches&quot;
   * &quot;values&quot;
