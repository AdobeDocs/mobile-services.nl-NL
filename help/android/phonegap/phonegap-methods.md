---
description: U kunt de iOS PhoneGap-plug-inmethoden gebruiken om een groot aantal taken uit te voeren.
keywords: android;bibliotheek;mobile;sdk
seo-description: U kunt de iOS PhoneGap-plug-inmethoden gebruiken om een groot aantal taken uit te voeren.
seo-title: Methoden van PhoneGap-plug-in
solution: Experience Cloud,Analytics
title: Methoden van PhoneGap-plug-in
topic-fix: Developer and implementation
uuid: bc3db9ce-81b7-45ec-88aa-6020c1db5d9c
exl-id: 4e6cf200-c826-4b23-87cf-4b8e1e691981
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '1573'
ht-degree: 34%

---

# Methoden van de insteekmodule PhoneGap{#phonegap-plug-in-methods}

U kunt de plug-inmethoden van Android PhoneGap gebruiken om een groot aantal taken uit te voeren.

Voeg in `html` bestanden waar u tracking wilt gebruiken het volgende toe aan de tag `<head>`:

```js
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Configuratiemethoden {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   Retourneert de privacystatus voor de huidige gebruiker.

   Hier volgen de beschikbare statussen:

   * `ADB.optedIn`: De treffers worden onmiddellijk verzonden.
   * `ADB.optedOut`: De treffers worden genegeerd.
   * `ADB.optUnknown`: Als uw rapportsuite  **** is ingeschakeld voor tijdstempels, worden treffers opgeslagen totdat de privacystatus verandert in aanmelden (hits worden verzonden) of Afmelden (hits worden verwijderd). Als uw rapportsuite **niet** tijdstempel-ingeschakeld is, worden treffers verwijderd totdat de privacystatus verandert in aanmelden.

      De standaardwaarde wordt ingesteld in het `ADBMobileConfig.json`-bestand.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      getPrivacyStatus(function (value) { myTempVal = value; }, function () {myTempVal = null;}); 
      ```

* **setPrivacyStatus**

   Stelt de privacystatus voor de huidige gebruiker in op `status`.

   U kunt een van de volgende statussen instellen:

   * `ADB.optedIn`: De treffers worden onmiddellijk verzonden.
   * `ADB.optedOut`: De treffers worden genegeerd.
   * `ADB.optUnknown`: Als uw rapportsuite  **** is ingeschakeld voor tijdstempels, worden treffers opgeslagen totdat de privacystatus verandert in aanmelden (hits worden verzonden) of Afmelden (hits worden verwijderd). Als uw rapportsuite **niet** tijdstempel-ingeschakeld is, worden treffers verwijderd totdat de privacystatus verandert in aanmelden.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.setPrivacyStatus('ADB.optedIn');
      ```

* **getLifetimeValue**

   Retourneert de levensduurwaarde van de huidige gebruiker. De standaardwaarde is 0.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.getLifetimeValue(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

* **setDebugLogging**

   Schakelt (`true`) in of schakelt (`false`) het bekijken zuivert informatie uit. Deze variabele is standaard `false`.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   Hiermee wordt de bibliotheekversie opgehaald.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.getVersion(function (value) { versionNum = value }, function () { versionNum = 1.0;});
      ```

* **trackingIdentifier**

   Retourneert de automatisch gegenereerde bezoeker-id.

   Dit is een app-specifieke, unieke bezoeker-id die wordt gegenereerd wanneer de app voor de eerste keer wordt gestart en die vanaf dat punt wordt opgeslagen en gebruikt. Deze id blijft behouden tussen upgrades van apps en wordt verwijderd wanneer de app wordt verwijderd.

   >[!TIP]
   >
   >Als uw app upgradet van de SDK van Experience Cloud 3.x naar 4.x, wordt de vorige bezoeker-id (aangepast of automatisch gegenereerd) opgehaald en opgeslagen als de aangepaste gebruikers-id. Zie `getUserIdentifier` hieronder voor meer informatie. Met deze id blijven bezoekersgegevens behouden tussen SDK-upgrades.

   Voor nieuwe installaties op 4.x SDK, is het gebruikersherkenningsteken `null` en het volgen herkenningsteken wordt gebruikt.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.trackingIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

* **getUserIdentifier**

   Als een gebruikersidentificatie van de klant is ingesteld, retourneert deze id; als de id niet is ingesteld, wordt `null` geretourneerd. De standaardwaarde is `null`.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      getUserIdentifier(function(value) { myTempVal = value; }, function () { myTempVal = null; });
      ```

* **setUserIdentifier**

   Hiermee stelt u de gebruikersnaam in op `identifier`.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   Hiermee stelt u het apparaattoken voor pushberichten in.

   ```java
   getUserIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; });
   ```

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.setPushIdentifier(pushIdentifier, success, fail);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.setPushIdentifier('test_push_identifier',function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **keepLifecycleSessionAlive**

   Hiermee stelt u de voorkeur in voor een levenscyclussessie.

   >[!IMPORTANT]
   >
   >Door `keepLifecycleSessionAlive` aan te roepen, voorkomt u dat uw app een nieuwe sessie start wanneer deze de volgende keer vanaf de achtergrond wordt hervat. Gebruik deze methode alleen als uw app zich registreert voor meldingen op de achtergrond.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      ADB.keepLifecycleSessionAlive(); 
      ```

* **trackingSendQueuedHits**

   Hiermee dwingt u de bibliotheek alle in de wachtrij geplaatste hits te verzenden, ongeacht de huidige batchopties.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   Haalt of plaatst het aantal opgeslagen het volgen vraag in de off-line rij op.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      ADB.trackingGetQueueSize(function (value) { myTempVal = value;}, function () { myTempVal = null;}); 
      ```

* **trackingClearQueue**

   Verwijdert alle opgeslagen het volgen vraag van de off-line rij.

   >[!WARNING]
   >
   >Wees voorzichtig wanneer u de wachtrij handmatig wist, omdat deze niet kan worden teruggedraaid.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      ADB.trackingClearQueue(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

## PII-methoden {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectionPII**

   Verzendt een PII inzamelingsverzoek.

   * Hier volgt de syntaxis voor deze methode:

   ```javascript
   ADB.collectPII(piiData,success, fail);
   ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success') },function (value) { alert('fail') ;});
      ```


## Methoden {#section_7946BB753A4446FE8A3ED728AEF97D04} bijhouden

* **trackAdobeDeepLink**

   Volgt een Deep Verbinding van de Adobe doorklikken-door.

   >[!TIP]
   >
   >Als de Levenscyclusvraag een lanceringsgebeurtenis is, zullen de gegevens van de Verbinding van de Adobe worden toegevoegd, anders zal een extra vraag worden verzonden.

   * Hier volgt de syntaxis voor deze methode:

      ```js
      ADB.trackAdobeDeepLink(deeplinkURL, success, fail); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function (value) { alert('success'); },function (value) { alert('fail') }); 
      ```

* **trackState**

   Traceert een toepassingsstatus met optionele contextgegevens. Frames zijn de weergaven die beschikbaar zijn in uw app, zoals `home dashboard`, `app settings`, `cart` enzovoort. Deze staten zijn vergelijkbaar met pagina&#39;s op een website en `trackState` roept de weergave van de verhogende pagina op.

   `cData`: JSON-object met sleutel-waardeparen die in contextgegevens moeten worden verzonden.

   * Hier volgt de syntaxis voor deze methode:

      ```js
      ADB.trackState(string stateName[,JSON cData]);
      ```

   * Hier volgen codevoorbeelden voor deze methode:

      ```js
        ADB.trackState("login&amp;nbsp;page"); 
      ```

      ```js
        ADB.trackState("login page", {"user":"john","remember":"true"});
      ```

* **trackAction**

   Tracks an action in your app. Tot de handelingen behoren `logins`, `banner taps`, `feed subscriptions` en andere metriek die in uw app voorkomen en die u wilt meten.

   * Hier volgt de syntaxis voor deze methode:

      ```js
      ADB.trackAction(string action[,JSON cData]); 
      ```

   * Hier volgen de codevoorbeelden voor deze methode:

      ```js
        ADB.trackAction("login");
      ```

      ```js
        ADB.trackAction("login", {"user":"john","remember":"true"}); 
      ```

* **trackLocation**

   Verzendt de huidige x y-coördinaten. Gebruikt ook aandachtspunten die in het `ADBMobileConfig.json` dossier worden bepaald of de plaats die als parameter wordt verstrekt binnen om het even welk van uw POI is. Als de huidige coördinaten binnen een bepaalde POI zijn, wordt een variabele van contextgegevens bevolkt en verzonden met `trackLocation` vraag.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.trackLocation(x, y[,JSON cData]); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.trackLocation('40.431596', '-111.893713'); 
      ```

* **trackLifetime &#x200B; ValueIncrease**

   Voegt `amount` aan de levenwaarde van de gebruiker toe.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSON cData]); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.trackLifetimeValueIncrease('10.01'); 
      ```

* **trackTimed &#x200B; ActionStart**

   Start een getimede actie met de naam `action`.

   Als u deze methode aanroept voor een actie die al is gestart, wordt de vorige getimede actie overschreven.

   >[!TIP]
   >
   >Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.trackTimedActionStart(action[,JSON cData]);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimed &#x200B; ActionUpdate**

   Geef `cData` door om de contextgegevens bij te werken die aan `action` worden geassocieerd.

   `cData` die wordt overgegaan wordt toegevoegd aan de bestaande gegevens voor de actie en, als de zelfde sleutel reeds voor `action` wordt bepaald, beschrijft de gegevens.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.trackTimedActionUpdate(String action[,JSON cData]);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.trackTimedActionUpdate("cartToCheckout",{'SampleContextDataKey3':'SampleContextDataVal3','SampleContextDataKey4':'SampleContextDataVal4'});
      ```

* **trackTimed &#x200B; ActionEnd**

   Een getimede actie beëindigen.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.trackTimedActionEnd("cartToCheckout"); 
      ```

* **trackingTimedActionExists**

   Retourneert of een getimede actie wordt uitgevoerd.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.trackingTimedActionExists(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

## Bebakenmethoden {#section_F9500D6BD95348E08E283C02B657019D}

* **trackBeacon**

   Tracks wanneer een gebruiker de nabijheid van een baken ingaat.

   * Hier volgt de syntaxis voor deze methode:

      ```js
      ADB.trackBeacon(uuid, major, minor, proximity, cData) 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      ADB.trackBeacon('2F234454-CF6D-4A0F-ADF2-F4911BA9FFA6', 1, 2, 
      ADB.beaconUnknown, {'hp':'hp_val','hp.company':'adobe'}
      ```

* **clearCurrentBeacon**

   Wist de bakengegevens nadat een gebruiker de nabijheid van het baken verlaat.

   * Hier volgt de syntaxis voor deze methode:

      ```js
      ADB.clearCurrentBeacon(success, fail)
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      ADB.clearCurrentBeacon(); 
      ```

## Doelmethoden {#section_8670140C5A3F455E887830AFFDF91D59}

* **targetLoadRequest**

   Verzendt een verzoek naar uw geconfigureerde `Target`-server en retourneert de tekenreekswaarde van de aanbieding.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.targetLoadRequest(success, fail, name, defaultContent, parameters);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.targetLoadRequest(function&nbsp;(value)
      {myTempVal = value }, function () { myTempVal = null;},'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   Verzendt een verzoek naar uw geconfigureerde `Target`-server.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.targetLoadOrderConfirmRequest(success, fail name orderId, orderTotal, productPurchaseId, parameters); 
      ```

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.targetLoadRequest(function (value) { myTempVal = value }
      , function ()
      { myTempVal = null; } 
      , 'name' 'orderId' 'total', 'purchaseId',
      {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   Wist de `Target`cookies van gedeelde cookie-opslag.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.targetClearCookies(); 
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   Verwerkt een `Target` de dienstverzoek.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(
        success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters requestLocationParameters
        ); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters  (function () { alert('success'); }, function () { alert('fail'); }, ;'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}, {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'});
      ```

* **targetLoadRequestWithName**

   Verwerkt een `Target` de dienstverzoek.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.targetLoadRequestWithRequestName(success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.targetLoadRequestWithName(
      function (value){ // handle target success} ,
      function() { // handle target failure }, 
      "mboxName",
      "defaultContent",
      {"profileParameters":"profileParametervalues"}
      {"orderId" : "32FGJ4XK" , "orderTotal" : "123.33" , "purchasedProductIds":"[46,34]" }
      {"mboxParameters":"mboxParametersvalues"}
      );
      ```

* **targetSessionID**

   Hiermee wordt de waarde opgehaald van het cookie `SessionID` dat door de doelserver voor deze bezoeker is geretourneerd.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.targetSessionID (success, fail); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.targetSessionID(function (value) { alert(value) },function (value){ alert('fail'); });  
      ```

* **targetPcID**

   Hiermee wordt de waarde opgehaald van het `PcID`-cookie dat door de `Target`-server voor deze bezoeker wordt geretourneerd.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.targetPcID (success, fail); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.targetPcID(function  (value) { alert(value) },function (value) { alert('fail'); });
      ```

* **targetSetThirdPartyID**

   Hiermee stelt u de aangepaste bezoeker-id voor Doel in.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID, success, fail); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id' function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **targetThirdPartyID**

   Hiermee wordt de aangepaste bezoeker-id voor Doel opgehaald.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.targetThirdPartyID(success, fail);
      ```

   * Hier volgt een codevoorbeeld voor deze methode:

      ```java
       ADB.targetThirdPartyID(function (value) { alert(value); },function (value) { alert('fail')__;});
      ```

## Verwervingsmethoden {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   Verzendt een verzoek naar uw gevormde server van het Doel en keert de koordwaarde van de aanbieding terug.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.acquisitionCampaignStartForApp(appId, data, success, fail); 
      ```

   * Hier volgen de codevoorbeelden voor deze methode:

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’});  
      ```

## Reclame-id {#section_194607D101B047A19C51B19E176E1500}

In de hoofdactiviteit die door Cordova wordt geproduceerd, roep `Config.submitAdvertisingIdentifierTask()` in `onResume()` methode. Zie [Configuratiemethoden](/help/android/configuration/methods.md) voor meer informatie.

## Methoden van Audience Manager {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **publiekGetVisitorProfile**

   Hiermee wordt het profiel van de bezoeker opgehaald.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.audienceGetVisitorProfile(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.audienceGetVisitorProfile(function(value) { profile = value;}, function() { profile = null; }); 
      ```

* **publiekGetDpuuid**

   Retourneert de DPUUID.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.audienceGetDpuuid(success fail);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.audienceGetDpuuid(function(value) { dpuuid = value;}, function(){dpuuid = null; }); 
      ```

* **publiekGetDpid**

   Retourneert de DPID.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.audienceGetDpid(success, fail);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;}, function() {dpid =  null;}); 
      ```

* **publiekSetDpidAndDpuuid**

   Hiermee stelt u de DPID en DPUUID in.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid, dpuuid, success, fail); 
      ```

   * Hier volgen de codevoorbeelden voor deze methode:

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’, function() {…}, function(){…};
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’); 
      ```

* **publiekSignalWithData**

   Verwerkt een de dienstverzoek van de Audience Manager.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.audienceSignalWithData(success, fail, data);
      ```

   * Hier volgen de codevoorbeelden voor deze methode:

      ```java
       ADB.audienceSignalWithData(function() {}, function() {} {‘key1’: ’value1’ ‘key2’: ‘value2’}); 
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’: ’value1’, ‘key2’:‘value2’}); 
      ```

* **publiekReset**

   Audience Manager-UUID en leegt het huidige bezoekersprofiel.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.audienceReset();
      ```

## ID-servicemethoden {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **bezoekerGetMarketingCloudId**

   Retourneert de Experience Cloud-id van de ID-service.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.visitorGetMarketingCloudId(success, fail); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.visitorGetMarketingCloudId(function (value) { mcid = value;},function (){ mcid = null;});
      ```

* **bezoekerSyncIdentifiers**

   Synchroniseert de verstrekte herkenningstekens met de Dienst van identiteitskaart.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.visitorSyncIdentifiers(identifiers, success, fail); 
      ```

   * Hier volgen de codevoorbeelden voor deze methode:

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’: ‘value_id_1’});  
      ```

* **bezoekerSyncIdentifiersWithAuthenticationState**

   Synchroniseert de verstrekte herkenningstekens aan de Dienst van identiteitskaart.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState
      (identifiers, authenticationState, success, fail); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'}, ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **bezoekerSyncIdentifierWithType**

   Synchronizes the provided identifier to the ID Service.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType, identifier authenticationState, success, fail); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type', 'test-identifier', ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success') },function (value) { alert('fail'); }); 
      ```

* **bezoekerAppendToURL**

   Hiermee voegt u bezoekersidentificatoren toe aan de opgegeven URL.

   * Hier volgt de syntaxis voor deze methode:

      ```java
       ADB.visitorAppendToURL(urlToAppend, success, fail); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.visitorAppendToURL('test_visitor_url', function (value) alert(value);},'');
      ```

* **bezoekerGetIDs**

   Retourneert alle `visitorID`s die zijn gesynchroniseerd.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.visitorGetIDs (success, fail);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.visitorGetIDs(function (value) { alert(value); },function (value) { alert('fail') ;}); 
      ```
