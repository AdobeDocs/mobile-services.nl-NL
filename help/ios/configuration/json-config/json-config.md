---
description: Met deze informatie kunt u het configuratiebestand ADBMobile.json gebruiken.
seo-description: Met deze informatie kunt u het configuratiebestand ADBMobile.json gebruiken.
seo-title: ADBMobile JSON config
solution: Experience Cloud,Analytics
title: ADBMobile JSON config
topic-fix: Developer and implementation
uuid: d9708d59-e30a-4f6c-ab1b-d9499855d0c2
exl-id: e3515de3-3aec-4dd0-996d-9c561ad1b1de
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '1715'
ht-degree: 8%

---

# ADBMobile JSON config {#adbmobile-json-config}

Deze informatie helpt u het `ADBMobile.json` configuratiedossier gebruiken.

## Referentie ADBMobileConfig.json-configuratiebestand {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

Hetzelfde configuratiebestand kan op meerdere platforms voor uw toepassing worden gebruikt:

>[!TIP]
>
>Op **iOS** kan het `ADBMobileConfig.json`-bestand worden geplaatst op een willekeurige locatie die toegankelijk is in de bundel.

* **verwerving**

   Hiermee schakelt u aanschaf van mobiele apps in.

   Als deze sectie ontbreekt, schakelt u de aanschaf van een mobiele toepassing in en downloadt u het configuratiebestand van de SDK opnieuw. Zie *referenceTimeout* hieronder voor meer informatie.

   * `server` - Verwervingsserver die bij de eerste introductie wordt gecontroleerd op een overnameverwijzing.
   * `appid` - Gegenereerde id die deze toepassing op de acquisitieserver op unieke wijze identificeert.
   * Minimale SDK-versie: 4.1

* **analyticsForwardingEnabled**

   De eigenschap in het object `audienceManager`. Als `Audience Manager` wordt gevormd en `analyticsForwardingEnabled` wordt geplaatst aan `true`, door:sturen al verkeer Analytics ook aan Audience Manager. De standaardwaarde is `false`.

   * Minimale SDK-versie: 4.8.0

* **backdateSessionInfo**

   Hiermee schakelt u de mogelijkheid voor de Adobe SDK in of uit om sessieinfo-hits te herstellen.

   Sessieinfo-hits bestaan momenteel uit crashes en sessielengte en kunnen worden in- of uitgeschakeld.

   * Als u de waarde instelt op `false`, zijn de treffers **disabled**.

      De SDK keert terug naar zijn gedrag van vóór 4.1 van het samenvatten van de zittingsinformatie voor de vorige zitting met de eerste slag van de verdere zitting. De Adobe SDK voegt de sessiegegevens ook toe aan de huidige levenscyclus, waardoor het maken van een opgepompt bezoek wordt voorkomen. Omdat er geen opgeblazen bezoeken meer ontstaan, neemt het aantal bezoeken onmiddellijk af.

   * Als u geen waarde opgeeft, is de standaardwaarde `true` en worden treffers **enabled**.

      Wanneer de treffers worden toegelaten, backdates de Adobe SDK de zittingsinfo aan 1 seconde na de definitieve slag in de vorige zitting. Dit betekent dat de neerstorting en zittingsgegevens met de correcte datum zullen correleren waarop zij voorkwamen. Eén bijwerking is dat de SDK een bezoek kan maken voor een melding met terugwerkende kracht. Bij elke nieuwe start van de toepassing wordt een hit hersteld.

   * Minimale SDK-versie: 4.6
   >[!IMPORTANT]
   >
   >De informatie van de zittingtreffer wordt van de achtergrond verzonden in een de servervraag van zittingsinfo, en de extra servervraag zou kunnen van toepassing zijn.


* **batchLimit**

   Drempel voor het aantal treffers dat in opeenvolgende vraag moet worden verzonden. Als `batchLimit` bijvoorbeeld is ingesteld op 10, wordt elke hit vóór de tiende hit opgeslagen in de wachtrij. Zodra de 10e hit binnenkomt, worden alle 10 treffers achtereenvolgens verzonden.

   * De standaardwaarde is `0`, wat betekent dat batchverwerking niet is ingeschakeld.
   * `offlineEnabled = true` vereist.
   * Minimale SDK-versie: 4.1

* **charset**

   Hiermee definieert u de tekenset die u gebruikt voor de gegevens die naar Analytics worden verzonden. De charset wordt gebruikt om binnenkomende gegevens om te zetten in UTF-8 voor opslag en rapportage. Zie [s.charSet](https://docs.adobe.com/content/help/en/analytics/implementation/vars/config-vars/charset.html) voor meer informatie.

   * Minimale SDK-versie: 4.0

* **clientCode**

   Uw toegewezen clientcode.

   >[!IMPORTANT]
   >
   >Deze variabele wordt vereist door Doel.

   * Minimale SDK-versie: 4.0

* **coopUnsafe**

   Voor leden van Coop van het Apparaat die deze waarde vereisen worden geplaatst aan `true`, moet u met het team van Coop werken om een vlag van de lijst van gewezen personen op uw rekening van de Co-op van het Apparaat te verzoeken. Er is geen zelfbedieningspad om deze markeringen in te schakelen.

   De volgende informatie onthouden:

   * Als `coopUnsafe` is ingesteld op `true`, wordt `coop_unsafe=1` altijd toegevoegd aan Audience Manager- en bezoekersidentiteitscontroles.
   * Als u het door:sturen van de server-kant van Analytics aan Audience Manager toelaat, zult u `coop_unsafe=1` op de treffers van Analytics ook zien.

   Hieronder vindt u aanvullende informatie:

   * Minimale SDK-versie: 4.16.1
   * De eigenschap Boolean van het object `marketingCloud` dat, wanneer ingesteld op `true`, ervoor zorgt dat het apparaat wordt uitgeschakeld in Apparaat Co-Op.
   * De standaardwaarde is `false`.
   * Deze instelling wordt alleen gebruikt **alleen** voor klanten met apparaatco-op-provisioning.



* **environmentId**

   De id van de omgeving die u wilt gebruiken. U kunt een geldige id (`environmentId=8`) specificeren, en als `environmentId` niet inbegrepen is, wordt de standaardmilieu van de Productie gebruikt.

   * Minimale SDK-versie: 4.14

* **lifecycleTimeout**

   De standaardwaarde is 300 seconden.

   Hiermee geeft u de tijdsduur in seconden op die moet verstrijken tussen het moment dat de app wordt gestart, maar voordat de toepassing als een nieuwe sessie wordt beschouwd. Deze time-out is ook van toepassing wanneer uw toepassing naar de achtergrond wordt verzonden en opnieuw wordt geactiveerd. De tijd die uw toepassing op de achtergrond doorbrengt, wordt niet opgenomen in de sessieduur.

   * Minimale SDK-versie: 4.0

* **berichten**

   Deze optie wordt automatisch gegenereerd door Adobe Mobile-services en definieert de instellingen voor in-app berichten. Zie de sectie *Beschrijving van berichten* hieronder voor meer informatie.

   * Minimale SDK-versie: 4.2

* **offlineEnabled**

   Indien ingeschakeld, worden treffers in een wachtrij geplaatst terwijl het apparaat offline is en later wordt verzonden wanneer het apparaat online is. Uw rapportsuite moet zijn ingeschakeld voor tijdstempels om offline tracering te kunnen gebruiken. De standaardwaarde is `false`.

   Hier volgt een aantal belangrijke informatie:

   * Als timestamps op uw rapportreeks worden toegelaten, `offlineEnabled` configuratiebezit *must* is waar.
   * Als uw rapportreeks niet timestamp toegelaten is, `offlineEnabled` configuratiebezit *moet* vals zijn.

      Als dit niet correct wordt gevormd, zullen de gegevens worden verloren. Als u niet zeker weet of een rapportsuite met tijdstempel is ingeschakeld, neemt u contact op met de klantenservice of downloadt u het configuratiebestand van de Adobe Mobile-services. Als u momenteel AppMeasurement-gegevens rapporteert aan een rapportsuite die ook gegevens uit JavaScript verzamelt, moet u mogelijk een aparte rapportsuite voor mobiele gegevens instellen of een aangepaste tijdstempel opnemen in alle JavaScript-resultaten die de variabele `s.timestamp` gebruiken.

   * Minimale SDK-versie: 4.0

* **org**

   Hiermee geeft u de Experience Cloud org-id voor de Adobe Experience Platform Identity Service op.

   * Minimale SDK-versie: 4.3

* **poi**

   Elke POI-array bevat de POI-naam, breedte, lengte en straal (in meters) voor het gebied van het punt. De POI-naam kan elke tekenreeks zijn. Wanneer een `trackLocation` vraag wordt verzonden, als de huidige coördinaten in bepaalde POI zijn, wordt een variabele van contextgegevens bevolkt en verzonden met `trackLocation` vraag.

   * Minimale SDK-versie: 4.0

   ```js
   "poi" [ 
           ["sanfrancisco",37.757144,-122.44812,7000]
           ["santacruz",36.972935,-122.01725,600]
         ] 
   ```

   >[!TIP]
   >
   >Vanaf versie 4.2 worden POI&#39;s gedefinieerd in de Adobe Mobile-interface en dynamisch gesynchroniseerd met het configuratiebestand van de app. Voor deze synchronisatie is de instelling `analytics.poi` vereist:

   ```js
   “analytics.poi”: “`https://assets.adobedtm.com/…/yourfile.json`”,
   ```

   Als deze instelling niet is geconfigureerd, moet het `ADBMobile.json`-bestand worden bijgewerkt om deze regel op te nemen. Als u een bijgewerkt configuratiebestand wilt downloaden, raadpleegt u [Voordat u ](/help/ios/getting-started/requirements.md) start.

* **postback**

   De definitie voor het &quot;callback&quot;berichtmalplaatje wordt hieronder getoond:

   ```js
   "payload":{
       "templateurl":"",//required- will be token-expanded prior to being sent
       "templatebody":"", //optional-if this length > 0 POST will be used as transport method. This is a base-64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"", //optional-if this is length > 0 and POST type is selected, this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout": 0 //optional-number of seconds to wait before timingout.Defaultis2.}
   ```

   Het `payload` voorwerp in de code is een voorbeeldlading voor een berichtdefinitie die in `ADBMobileConfig.json` dossier zou gaan. Zie [Postbacks](/help/ios/analytics-main/postback/postback.md) voor meer informatie.

   * Minimale SDK-versie: 4.6

* **privacyDefault**

   * Voor `optedin` worden de treffers onmiddellijk verzonden.
   * Bij `optedout` worden de treffers genegeerd.
   * Als voor `optunknown` de rapportsuite is ingeschakeld voor tijdstempels, worden treffers opgeslagen totdat de privacystatus verandert in opt-in (hits worden verzonden) of opt-out (hits worden genegeerd).

      Als uw rapportsuite niet is ingeschakeld voor tijdstempels, worden treffers genegeerd totdat de privacystatus verandert en u zich aanmeldt.

      Hiermee wordt alleen de beginwaarde ingesteld. Als deze waarde is ingesteld of gewijzigd in code, wordt de nieuwe waarde gebruikt totdat deze opnieuw wordt gewijzigd of wanneer de app wordt verwijderd en opnieuw wordt geïnstalleerd. De standaardwaarde is `optedin`.

   * Minimale SDK-versie: 4.0

* **referenceTimeout**

   Aantal seconden dat de SDK wacht op gegevens van de verwervingsreferentie bij de eerste introductie voordat de time-out optreedt. Als u acquisitie gebruikt, raden we een time-out van 5 seconden aan.

   >[!IMPORTANT]
   >
   >Deze variabele wordt vereist door Opname. Als de variabele is ingesteld op `0` of niet is opgenomen, wacht de SDK niet op aanschafgegevens en worden de aanschafwaarden niet bijgehouden.

   * Minimale SDK-versie: 4.1

* **remotes**

   Deze optie wordt automatisch geconfigureerd en definieert de door Adobe gehoste eindpunten voor dynamische configuratiebestanden. De laatste updatetijd van elk configuratiedossier wordt gecontroleerd tegen de huidige versie bij elke lancering, en de updates worden gedownload en bewaard.

   * `analytics.poi` is het eindpunt voor ontvangen POI configuratie.

   * `messages` is het eindpunt voor ontvangen in-app berichtconfiguratie.

   * Minimale SDK-versie: 4.2

* **Rsids**

   Een of meer rapportsuites voor het ontvangen van analysegegevens. Meerdere rapportsuite-id&#39;s moeten worden gescheiden door komma&#39;s zonder tussenruimte.

   ```js
   "rsids": "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2" 
   ```

   >[!IMPORTANT]
   >
   >Deze variabele wordt vereist door Analytics.

   * Minimale SDK-versie: 4.0

* **server**

   De Analytics- of Audience Management-server, gebaseerd op het bovenliggende knooppunt.

   Deze variabele moet worden gevuld met het serverdomein, zonder het protocolvoorvoegsel `https://` of `https://`. Dit voorvoegsel wordt automatisch verwerkt door de bibliotheek en is gebaseerd op de variabele `ssl`.

   Als `ssl` `true` is, wordt een veilige verbinding gemaakt met deze server. Als `ssl` `false` is, wordt een onveilige verbinding gemaakt met deze server.

   >[!IMPORTANT]
   >
   >Deze variabele wordt vereist door Analytics en/of Audience Management.

   * Minimale SDK-versie: 4.0

* **ssl**

   >[!IMPORTANT]
   >
   > Vanaf versie 4.10.0 staat SSL standaard op true als de markering niet is ingesteld.

   Hiermee schakelt u (`true`) of schakelt u de mogelijkheid uit om meetgegevens te verzenden met behulp van SSL (HTTPS).`false`

   De definitie voor het &quot;callback&quot;berichtmalplaatje wordt hieronder getoond:

   ```js
   "payload":{
       "templateurl":"",//required-will be token-expanded prior to being sent
       "templatebody":"",//optional-if this length > 0, POST will be used as transport method. This is a base64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"",//optional-if this is length > 0 and POST type is selected this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout":0//optional-numberofsecondstowaitbeforetimingout.Defaultis2.} 
   ```

   Het `payload` voorwerp in de code is een steekproeflading voor een berichtdefinitie die in het `ADBMobileConfig.json` dossier gaat. Zie [Postbacks](/help/ios/analytics-main/postback/postback.md) voor meer informatie.

   * Minimale SDK-versie: 4.0

* **timeout**

   Hiermee bepaalt u hoe lang Doel wacht op een reactie.

   * Minimale SDK-versie: 4.0


## Voorbeeld `ADBMobileConfig.json` bestand {#section_52FA7C71A99147AFA9BE08D2177D8DA7}

Hier volgt een voorbeeld van een `ADBMobileConfig.json`-bestand:

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

## Beschrijving van berichten {#section_B97D654BA92149CE91F525268D7AD71F}

Het berichtenknooppunt wordt automatisch gegenereerd door Adobe Mobile-services en hoeft gewoonlijk niet handmatig te worden gewijzigd. De volgende beschrijving wordt gegeven voor het oplossen van problemendoeleinden:

* &quot;messageId&quot;

   * Gegenereerde id, vereist

* &quot;template&quot;

   * &quot;alert&quot;, &quot;fullscreen&quot; of &quot;local&quot;
   * vereist

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
         `image` is onbereikbaar
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









* &quot;showOffline&quot;

   * true of false
   * default is false

* &quot;showRule&quot;

   * &quot;always&quot;, &quot;once&quot; of &quot;UntilClick&quot;
   * vereist

* &quot;endDate&quot;

   * aantal seconden sinds 1 januari 1970
   * standaard is dit 2524730400

* &quot;startDate&quot;

   * aantal seconden sinds 1 januari 1970
   * standaard is dit 0

* &quot;audiences&quot;

   Een reeks objecten die definieert hoe het bericht moet worden weergegeven:

   * &quot;key&quot;

      Naam van variabele waarnaar moet worden gezocht in de treffer. Deze naam is vereist.

   * &quot;matches&quot;

      Het type matcher dat bij de vergelijking wordt gebruikt:

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

      Een reeks waarden die wordt gebruikt om te vergelijken met de waarde van de variabele die in het volgende wordt genoemd:

      * key
      * met het matchingentype in
      * matches


* &quot;triggers&quot;

   Hetzelfde als audiences, maar hier worden de acties weergegeven in plaats van het audience:

   * &quot;key&quot;
   * &quot;match&quot;
   * &quot;values&quot;
