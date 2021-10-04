---
description: Met de iOS PhoneGap-plug-inmethoden kunt u een groot aantal taken uitvoeren.
keywords: fonegap
solution: Experience Cloud,Analytics
title: Methoden van PhoneGap-plug-in
topic-fix: Developer and implementation
uuid: bd830fe5-804a-4d0a-bbb6-99a6d8da6a03
exl-id: 7ffdf008-1605-471f-93fb-f9c6b38a3bcb
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '1715'
ht-degree: 33%

---

# Methoden van PhoneGap-plug-in {#phonegap-plug-in-methods}

U kunt de iOS PhoneGap-plug-inmethoden gebruiken om een groot aantal taken uit te voeren.

Voeg in `html` bestanden waar u tracking wilt gebruiken het volgende toe aan de tag `<head>`:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Configuratiemethoden {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   Retourneert de privacystatus voor de huidige gebruiker. Hier volgen de beschikbare statussen:

   * `ADB.optedIn`, waarbij treffers direct worden verzonden.
   * `ADB.optedOut`, waar treffers worden genegeerd.
   * `ADB.optUnknown`Als uw rapportsuite  **** is ingeschakeld voor tijdstempels, worden treffers opgeslagen totdat de privacystatus verandert in aanmelden (hits worden verzonden) of Afmelden (hits worden verwijderd). Als uw rapportsuite **niet** tijdstempel-ingeschakeld is, worden treffers verwijderd totdat de privacystatus verandert in aanmelden.\
      De standaardwaarde wordt ingesteld in het `ADBMobileConfig.json`-bestand.

      * Hier volgt het codevoorbeeld voor deze methode:

         ```javascript
         getPrivacyStatus(function (value){myTempVal = value;},function(){myTempVal = null;});
         ```

* **setPrivacyStatus**

   Stelt de privacystatus voor de huidige gebruiker in op `status`. U kunt een van de volgende statussen instellen:
   * `ADB.optedIn`, waarbij treffers direct worden verzonden.
   * `ADB.optedOut`, waar treffers worden genegeerd.
   * `ADB.optUnknown` - Als de  **** optie voor tijdstempels in uw rapportsuite is ingeschakeld, worden treffers opgeslagen totdat de privacystatus verandert in een aanmeldingsnaam (treffers worden verzonden) of de optie om te weigeren (treffers worden verwijderd).

      Als uw rapportsuite **niet** tijdstempel-ingeschakeld is, worden treffers verwijderd totdat de privacystatus verandert in aanmelden.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
        ADB.setPrivacyStatus('ADB.optedIn'); 
      ```

* **getLifetimeValue**

   Retourneert de levensduurwaarde van de huidige gebruiker. De standaardwaarde is 0.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      ADB.getLifetimeValue(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```

* **setDebugLogging**

   Schakelt (`true`) in of schakelt (`false`) het bekijken zuivert informatie uit. Deze variabele is standaard `false`.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   Hiermee wordt de bibliotheekversie opgehaald.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      ADB.getVersion(function(value){versionNum = value;},function(){versionNum=1.0;}); 
      ```

* **trackingIdentifier**

   Retourneert de automatisch gegenereerde bezoeker-id. Dit is een unieke bezoeker-id die specifiek is voor de app en die wordt gegenereerd wanneer de app voor de eerste keer wordt gestart en die vanaf dat moment wordt opgeslagen en gebruikt. Deze id blijft behouden tussen upgrades van apps en wordt verwijderd wanneer de app wordt verwijderd.

   >[!TIP]
   >
   >Als uw app upgradet van de SDK van Experience Cloud 3.x naar 4.x, wordt de vorige bezoeker-id (aangepast of automatisch gegenereerd) opgehaald en opgeslagen als de aangepaste gebruikers-id (zie `getUserIdentifier` hieronder). Op deze manier blijven bezoekersgegevens behouden tussen upgrades van de SDK. Voor nieuwe installaties op 4.x SDK, is het gebruikersherkenningsteken `null`, en het volgen herkenningsteken wordt gebruikt.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
       ADB.trackingIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **getUserIdentifier**

   Retourneert de aangepaste gebruikers-id als een aangepaste id is ingesteld en retourneert `null` als er geen aangepaste id is ingesteld. De standaardwaarde is `null`.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      getUserIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **setUserIdentifier**

   Hiermee stelt u de gebruikersnaam in op `identifier`.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   Hiermee stelt u het apparaattoken voor pushberichten in.

   * Hier volgt de syntaxis voor deze methode:

      ```javascript
      ADB.setPushIdentifier(pushIdentifier,success,fail);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      ADB.setPushIdentifier('test_push_identifier',function(value){alert('success');},function(value){alert('fail');
      ```

* **keepLifecycleSessionAlive**

   Hiermee stelt u de voorkeur in voor een levenscyclussessie.

   >[!IMPORTANT]
   >
   >Door `keepLifecycleSessionAlive` aan te roepen, voorkomt u dat uw app een nieuwe sessie start wanneer deze de volgende keer vanaf de achtergrond wordt hervat. Gebruik deze methode alleen als uw app zich registreert voor meldingen op de achtergrond.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **trackingSendQueuedHits**

   Hiermee dwingt u de bibliotheek alle in de wachtrij geplaatste hits te verzenden, ongeacht de huidige batchopties.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   Haalt of plaatst het aantal opgeslagen het volgen vraag in de off-line rij op.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      ADB.trackingGetQueueSize(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **trackingClearQueue**

   Verwijdert alle opgeslagen het volgen vraag van de off-line rij.

   >[!CAUTION]
   >
   >Wees voorzichtig wanneer u de wachtrij handmatig wist, omdat deze niet kan worden teruggedraaid.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      ADB.trackingClearQueue(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **keepLifecycleSessionAlive**

   Wijst aan SDK erop dat uw volgende hervat van achtergrond geen nieuwe zitting, ongeacht de waarde van de tijd van de levenscycluszitting in uw configuratiedossier zou moeten beginnen.

   >[!IMPORTANT]
   >
   >Belangrijk:  deze methode is bedoeld voor toepassingen die zich registreren voor meldingen op de achtergrond en mag alleen worden aangeroepen vanuit uw code die wordt uitgevoerd terwijl de toepassing op de achtergrond wordt uitgevoerd.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **collectionLifecycleData**

   Geeft aan de SDK aan dat levenscyclusgegevens moeten worden verzameld voor gebruik in alle oplossingen in de SDK. Zie [Metriek van levenscyclus](/help/ios/metrics.md) voor meer informatie.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      ADB.collectLifecycleData(); 
      ```


## PII-methoden {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectionPII**

   Verzendt een PII inzamelingsverzoek.

   * Hier volgt de syntaxis voor deze methode:

      ```javascript
      ADB.collectPII(piiData,success,fail); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success'); },function (value) { alert('fail'); });
      ```

## Traceringsmethoden {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   Volgt een Deep Verbinding van de Adobe doorklikken-door.

   >[!TIP]
   >
   >Als de Levenscyclusvraag een lanceringsgebeurtenis is, zullen de gegevens van de Verbinding van de Adobe worden toegevoegd, anders zal een extra vraag worden verzonden.

   * Hier volgt de syntaxis voor deze methode:

      ```javascript
      ADB.trackAdobeDeepLink(deeplinkURL,success,fail);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackPushMessageClickthrough**

   Tracks a push message click-through.

   * Hier volgt de syntaxis voor deze methode:

      ```javascrpt
      ADB.trackPushMessageClickthrough(userInfo,success,fail); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      ADB.trackPushMessageClickthrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackLocalNotificationClickThrough**

   Tracks a local notification message click-through.

   * Hier volgt de syntaxis voor deze methode:

      ```javascript
      ADB.trackLocalNotificationClickThrough(userInfo,success,fail); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      ADB.trackLocalNotificationClickThrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackState**

   Traceert een toepassingsstatus met optionele contextgegevens. Frames zijn de weergaven die beschikbaar zijn in uw app, zoals `home dashboard`, `app settings`, `cart` enzovoort. Deze staten zijn vergelijkbaar met pagina&#39;s op een website en `trackState` roept de weergave van de verhogende pagina op. cData is een JSON-object met sleutel-waardeparen die in contextgegevens moeten worden verzonden.

   * Hier volgt de syntaxis voor deze methode:

      ```javascript
      ADB.trackState(stringstateName[,JSONcData]); 
      ```

   * Hier volgen de codevoorbeelden voor deze methode:

      ```javascript
      ADB.trackState("loginpage");
      ```

      ```javascript
        ADB.trackState("loginpage",{"user":"john","remember":"true"});
      ```

* **trackAction**

   Tracks an action in your app. Handelingen zijn de dingen die in uw app voorkomen en die u wilt meten, zoals `logins`, `banner taps`, `feed subscriptions` en andere metriek.

   * Hier volgt de syntaxis voor deze methode:

      ```javascript
      ADB.trackAction(stringaction[,JSONcData]);
      ```

   * Hier volgen de codevoorbeelden voor deze methode:

      ```javascript
      ADB.trackAction("login");
      ```

      ```javascript
      ADB.trackAction("login",{"user":"john","remember":"true"})
      ```

* **trackActionFromBackground**

   Tracks an action that occurred in the background. Dit onderdrukt levenscyclusgebeurtenissen van het vuren in bepaalde scenario&#39;s.

   * Hier volgt de syntaxis voor deze methode:

      ```javascript
      ADB.trackActionFromBackground(stringaction[,JSONcData]); 
      ```

   * Hier volgen de codevoorbeelden voor deze methode:

      ```javascript
      ADB.trackActionFromBackground("login");
      ```

      ```javascript
      ADB.trackActionFromBackground("login",{"user":"john","remember":"true"});
      ```

* **trackLocation**

   Verzendt de huidige x- en y-coördinaten. Gebruikt ook de aandachtspunten die in het `ADBMobileConfig.json` dossier werden bepaald om te bepalen als de plaats die als parameter wordt verstrekt binnen om het even welk van uw POIs is. Als de huidige coördinaten binnen een bepaalde POI zijn, wordt een variabele van contextgegevens bevolkt en verzonden met `trackLocation` vraag.

   * Hier volgt de syntaxis voor deze methode:

      ```javascript
       ADB.trackLocation(x,y[,JSONcData]);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      ADB.trackLocation('40.431596','-111.893713');
      ```

* **trackLifetime &#x200B; ValueIncrease**

   Voegt `amount` aan de levenwaarde van de gebruiker toe.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSONcData]);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.trackLifetimeValueIncrease('10.01');
      ```

* **trackTimed &#x200B; ActionStart**

   Start een getimede actie met de naam `action`. Als u deze methode aanroept voor een actie die al is gestart, wordt de vorige getimede actie overschreven.

   >[!TIP]
   >
   >Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.trackTimedActionStart(action[,JSONcData]);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimed &#x200B; ActionUpdate**

   Geef `cData` door om de contextgegevens bij te werken die aan gegeven `action` worden geassocieerd. De `cData` die wordt doorgegeven, wordt toegevoegd aan de bestaande gegevens voor de opgegeven handeling en overschrijft de gegevens als dezelfde sleutel al is gedefinieerd voor `action`.

   >[!TIP]
   >
   >Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.trackTimedActionUpdate(Stringaction[,JSONcData]);
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
      ADB.trackingTimedActionExists(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```


## Doelmethoden {#section_C45D2FE54AE04EB5BD24D3508F8A3212}

* **targetLoadRequest**

   Verzendt verzoek naar uw geconfigureerde `Target`-server en retourneert de tekenreekswaarde van de aanbieding.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.targetLoadRequest(success,fail,name,defaultContent,parameters); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.targetLoadRequest(function (value)
      {myTempVal = value;},function() {myTempVal = null;},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   Verzendt een verzoek naar uw geconfigureerde doelserver.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.targetLoadOrderConfirmRequest(success,fail,name,orderId,orderTotal,productPurchaseId,parameters); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.targetLoadRequest(function(value){myTempVal=value;}
      ,function()
      {myTempVal = null; }
      ,'name','orderId','total','purchaseId'
      ,{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   Wist de doelcookies van gedeelde cookie-opslag.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.targetClearCookies();
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   Verwerkt een de dienstverzoek van het Doel.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(success,fail,name,defaultContent,profileParameters,orderParameters,mboxParameters,requestLocationParameters
      ); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(function(){alert('success');},function(){alert('fail');},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadRequestWithName**

   Verwerkt een de dienstverzoek van het Doel.

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
      ADB.targetSessionID(success,fail); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
        ADB.targetSessionID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

* **targetPcID**

   Hiermee wordt de waarde opgehaald van het cookie `PcID` dat door de doelserver voor deze bezoeker is geretourneerd.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.targetPcID(success,fail);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.targetPcID(function(value){alert(value);},function(value){alert('fail');});
      ```

* **targetSetThirdPartyID**

   Hiermee stelt u de aangepaste bezoeker-id voor Doel in.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID,success,fail); 
      ```

   * Hier is het codevoorbeeld voor deze groep:

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **targetThirdPartyID**

   Hiermee wordt de aangepaste bezoeker-id voor Doel opgehaald.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.targetThirdPartyID(success,fail); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.targetThirdPartyID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

## Verwervingsmethoden {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   Hiermee kunnen ontwikkelaars een campagne voor het aanschaffen van apps starten alsof de gebruiker op een koppeling had geklikt. Dit is handig voor het maken van handmatige aanschafkoppelingen en het omleiden van de app store zelf (bijvoorbeeld met een `SKStoreView`).

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.acquisitionCampaignStartForApp(appId,data,success,fail); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.acquisitionCampaignStartForApp('0652024f-adcd-49f9-9bd7-2552a4564d2f',{'extraDataKey':'extraDataValue'},success,fail); 
      ```


## Reclameaanduiding {#section_194607D101B047A19C51B19E176E1500}

In `AppDelegate` die door Cordova wordt geproduceerd, roep `[ADBMobile setAdvertisingIdentifier:]` in `application:didFinishLaunchingWithOptions:` afgevaardigde methode. Zie [Configuratiemethoden](/help/ios/configuration/sdk-methods.md) voor meer informatie.

## Methoden van Audience Manager {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **publiekGetVisitorProfile**

   Hiermee wordt het profiel van de bezoeker opgehaald.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.audienceGetVisitorProfile();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.audienceGetVisitorProfile(function(value){profile = value;},function(){profile = null;}); 
      ```

* **publiekGetDpuuid**

   Retourneert de DPUUID.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.audienceGetDpuuid(success,fail);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
       ADB.audienceGetDpuuid(function(value){dpuuid=value;},function(){dpuuid=null;}); 
      ```

* **publiekGetDpid**

   Retourneert de DPID.

   * Hier volgt de syntaxis voor deze methode:

      ```java
       ADB.audienceGetDpid(success,fail);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;},function(){dpid = null;}); 
      ```

* **publiekSetDpidAndDpuuid**

   Hiermee stelt u de DPID en DPUUID in.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid,dpuuid,success,fail);
      ```

   * Hier volgen de codevoorbeelden voor deze methode:

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’,function(){…},function(){…});
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’);
      ```

* **publiekSignalWithData**

   Verwerkt een de dienstverzoek van de Audience Manager.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.audienceSignalWithData(success,fail,data);
      ```

   * Hier volgen de codevoorbeelden voor deze methode:

      ```java
      ADB.audienceSignalWithData(function(){},function(){},{‘key1’:’value1’,‘key2’:‘value2’});
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’:’value1’,‘key2’:‘value2’}); 
      ```

* **publiekReset**

   Hiermee wordt de UUID van publieksmanager opnieuw ingesteld en wordt het huidige bezoekersprofiel leeggemaakt.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.audienceReset(); 
      ```

## ID-servicemethoden {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **bezoekerGetMarketingCloudId**

   Retourneert de Experience Cloud-id van de id-service.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.visitorGetMarketingCloudId(success,fail);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.visitorGetMarketingCloudId(function(value){mcid=value;},function(){mcid=null;}); 
      ```

* **bezoekerSyncIdentifiers**

   Synchroniseert de verstrekte herkenningstekens met de dienst van identiteitskaart.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.visitorSyncIdentifiers(identifiers,success,fail);
      ```

   * Hier volgen de codevoorbeelden voor deze methode:

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’},function(){…},function(){…})) 
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:‘value_id_1’});
      ```

* **bezoekerSyncIdentifiersWithAuthenticationState**

   Hiermee synchroniseert u de opgegeven id&#39;s met de service bezoekersidentiteitskaart.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState(identifiers,authenticationState,success,fail); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'},ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');});
      ```

* **bezoekerSyncIdentifierWithType**

   Synchroniseert de opgegeven id met de service bezoekersidentiteitskaart.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType,identifier,authenticationState,success,fail); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type','test-identifier',ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **bezoekerAppendToURL**

   Hiermee voegt u bezoekersidentificatoren toe aan de opgegeven URL.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.visitorAppendToURL(urlToAppend,success,fail);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.visitorAppendToURL('test_visitor_url',function(value){alert(value);},'');
      ```

* **bezoekerGetIDs**

   Retourneert alle `visitorIDs` die zijn gesynchroniseerd.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      ADB.visitorGetIDs(success,fail)
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ADB.visitorGetIDs(function(value){alert(value);},function(value){alert('fail');}); 
      ```
