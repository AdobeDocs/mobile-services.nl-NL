---
description: Hier volgt een lijst met TVJS-methoden die door de tvOS-bibliotheek worden aangeboden.
seo-description: Hier volgt een lijst met TVJS-methoden die door de tvOS-bibliotheek worden aangeboden.
seo-title: TVJS-methoden
solution: Marketing Cloud,Analytics
title: TVJS-methoden
topic: Developer and implementation
uuid: a7bfa85a-0d6e-4f51-9a9e-70429c2a9806
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# TVJS-methoden {#tvjs-methods}

Hier volgt een lijst met TVJS-methoden die door de tvOS-bibliotheek worden aangeboden.

## Configuratiemethoden {#section_5F82FD2F6A0546B3B4E80DF832E11634}

* **versie**

   Retourneert de huidige versie van de Adobe Mobile-bibliotheek.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      version()
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var sdkVersion = ADBMobile.version();
      ```

   * Retourneert: `String`

* **privacyStatus**

   Retourneert de NSUInteger-representatie van de privacy status enum voor de huidige gebruiker.

   Hier volgen de opties:

   * `ADBMobilePrivacyStatusOptIn`: De berichten worden onmiddellijk verzonden.
   * `ADBMobilePrivacyStatusOptOut`: Hits worden weggegooid.
   * `ADBMobilePrivacyStatusUnknown`: Als offline bijhouden is ingeschakeld, worden treffers opgeslagen totdat de privacystatus wordt gewijzigd in opt-in (hits worden verzonden) of opt-out (treffers worden verwijderd).

      Als offline bijhouden niet is ingeschakeld, worden treffers genegeerd totdat de privacystatus verandert in aanmelden. De standaardwaarde wordt ingesteld in het `ADBMobileConfig.json` bestand.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      privacyStatus()
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var privacyStatus = ADBMobile.privacyStatus();
      ```

   * Retourneert: `Number`

* **setPrivacyStatus**

   Stelt de privacystatus voor de huidige gebruiker in op een van de volgende waarden:

   * `ADBMobilePrivacyStatusOptIn`: De berichten worden onmiddellijk verzonden.
   * `ADBMobilePrivacyStatusOptOut`: Hits worden weggegooid.
   * `ADBMobilePrivacyStatusUnknown`: Als offline bijhouden is ingeschakeld, worden treffers opgeslagen totdat de privacystatus wordt gewijzigd in de optie voor aanmelding (treffers worden verzonden) of de optie voor niet-deelname (treffers worden verwijderd).
   Als offline bijhouden niet is ingeschakeld, worden treffers genegeerd totdat de privacystatus verandert in aanmelden.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      setPrivacyStatus(privacyStatus)
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```


* **lifeValue**

   Retourneert de levensduurwaarde van de huidige gebruiker. De standaardwaarde is `0`.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      lifetimeValue()
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var ltv = ADBMobile.lifetimeValue();
      ```

   * Retourneert: `Number`

* **userIdentifier**

   Retourneert de gebruikers-id als er een aangepaste id is ingesteld. Retourneert nul als er geen aangepaste id is ingesteld. De standaardwaarde is `nil`.

   >[!IMPORTANT]
   >
   >Als uw app upgradet van de Experience Cloud 3.x naar 4.x SDK, wordt de vorige aangepaste of automatisch gegenereerde bezoeker-id opgehaald en opgeslagen als de aangepaste gebruikers-id. Op deze manier blijven bezoekersgegevens behouden tussen SDK-upgrades. Voor nieuwe installaties op 4.x SDK, is gebruikersidentificatie nihil tot reeks.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      userIdentifier()
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var uid = ADBMobile.userIdentifier();
      ```

   * Retourneert: `String`

* **setUserIdentifier**

   Hiermee stelt u de gebruikers-id in.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      setUserIdentifier(userId)
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.setUserIdentifier(‘myUserId’);
      ```

   * Retourneert: N.v.t.

   * Parameter:  `userID`

      * Type: String
      * Nieuwe id voor deze gebruiker.

* **setAdvertisingIdentifier**

   Stelt de IDFA in de SDK in en als deze is ingesteld in de SDK, wordt de IDFA verzonden in de levenscyclus. IDFA kan ook in Signals (Postbacks) worden betreden.

   >[!IMPORTANT]
   >
   >Haal de IDFA alleen op van Apple API&#39;s als u een advertentieservice gebruikt. Als u IDFA ophaalt en deze niet correct gebruikt, wordt uw app mogelijk afgewezen.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      setAdvertisingIdentifier(idfa)
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.setAdvertisingIdentifier(‘myIdfa’);
      ```

   * Retourneert: N.v.t.
   * Parameter: `idfa`
      * Type: `String`
      * IDFA opgehaald van Apple API.

* **setDebugLogging**

   Hiermee stelt u de voorkeur voor foutopsporing in.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      setDebugLogging(logging)
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      `ADBMobile.setDebugLogging(true);
      ```

   * Retourneert: N.v.t.
   * Parameters: `logging`
      * Type: `Bool`
      * Waarde die aangeeft of de Adobe SDK zich moet aanmelden bij de foutopsporingsconsole.


## Analysemethoden {#section_F3DB9BE225F84F86BE5F8D15164C0379}

* **trackStateData**

   Traceert een toepassingsstatus met optionele contextgegevens. Frames zijn de weergaven die beschikbaar zijn in uw app, zoals het thuisdashboard, de app-instellingen, winkelwagentje enzovoort. Deze staten zijn gelijkaardig aan pagina&#39;s op een website, en trackState roept verhogende paginameningen.

   Als de status leeg is, wordt deze weergegeven als toepassingsversie (build) voor de toepassingsnaam in rapporten. Als u deze waarde in rapporten ziet, zorg ervoor u de staat in elke trackState vraag plaatst.

   >[!TIP]
   >
   >Dit is de enige volgende vraag die de paginameningen verhoogt.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      trackStateData(stateName [, contextData])
      ```

      * Retourneert: N.v.t.
      * Parameter: `stateName`
         * Type: `String`
         * Naam van paginatestand
      * Parameter: `contextData`
         * Type: Object
         * Aanvullende contextgegevens voor deze hit.
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.trackStateData(‘homepage’, {‘userid’:12345});
      ```




* **trackActionData**

   Tracks an action in your app. Handelingen zijn de dingen die in uw app gebeuren en die u wilt meten, zoals logons, bannertiketten, feedabonnementen en andere maatstaven.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      trackActionData(actionName [, contextData])
      ```

      * Retourneert: N.v.t.
      * Parameters: `actionName`
         * Type: String
         * Naam van de handeling die wordt bijgehouden.
      * Parameter: `contextData`
         * Type: Object
         * Aanvullende contextgegevens voor deze hit.
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.trackActionData(‘likeClicked’, {‘imageName’:’funnyKitty’});
      ```



* **trackLocationWithLatLonData**

   Verzendt de huidige breedte- en lengtecoördinaten.

   Gebruikt ook punten van belang (POI) die in het `ADBMobileConfig.json` dossier worden bepaald om te bepalen of de plaats die u als parameter inging in om het even welk van uw POIs is. Als de huidige coördinaten zich in een bepaalde POI bevinden, wordt een variabele van contextgegevens gevuld en met de `trackLocation` vraag verzonden.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      trackLocationWithLatLonData(lat, lon [, contextData]);
      ```

      * Retourneert: N.v.t.
      * Parameter: `lat`
         * Type: Getal
         * Breedtegraad van de locatie.
      * Parameter: `lon`
         * Type: Getal
         * Lengte van de locatie.
      * Parameter: `contextData`
         * Type: Object
         * Aanvullende contextgegevens voor deze hit.
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.trackLocationWithLatLonData(43.36, -116.12, null);
      ```




* **trackLifetimeValueIncreaseJsData**

   Hiermee voegt u een bedrag toe aan de levensduurwaarde van de gebruiker.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      trackLifetimeValueIncreaseJsData(increaseAmount)
      ```

      * Retourneert: N.v.t.
      * Parameter: `increaseAmount`
         * Type: Getal
         * Bedrag dat moet worden toegevoegd aan de huidige levensduur van de gebruiker.
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.trackLifetimeValueIncreaseJsData(5);
      ```


* **trackTimedActionStartData**

   Een getimede actie starten met een naamactie. Als u deze methode aanroept voor een actie die al is gestart, wordt de vorige getimede actie overschreven.

   >[!TIP]
   >
   >Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      trackTimedActionStartData(name [, contextData])
      ```

      * Retourneert: N.v.t.
      * Parameter: `name`
         * Type: String
         * Naam van de getimede actie die wordt begonnen.
      * Parameter: `contextData`
         * Type: Object
         * Aanvullende contextgegevens voor deze hit.
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.trackTimedActionStartData(‘level1’, {‘userId’:42423});
      ```


* **trackTimedActionUpdateData**

   Geef gegevens door om de contextgegevens bij te werken die aan de opgegeven actie zijn gekoppeld.

   De gegevens die worden doorgegeven, worden toegevoegd aan de bestaande gegevens voor de opgegeven actie en als dezelfde toets al is gedefinieerd voor de actie, worden de gegevens overschreven.

   >[!TIP]
   >
   >Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      trackTimedActionUpdateData(name [, contextData])
      ```

      * Retourneert: N.v.t.
      * Parameter: `name`
         * Type: String
         * Naam van de getimede actie die wordt bijgewerkt.
      * Parameter: `contextData`
         * Type: Object
         * Aanvullende contextgegevens voor deze hit.
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.trackTimedActionUpdateData(‘level1’);
      ```



* **trackTimedActionEndJsLogic**

   Een getimede actie beëindigen.

   Als u een callback functie verstrekt, kunt u tot de definitieve tijdwaarden toegang hebben. Als er geen callback is opgegeven of als de callback true retourneert, verzendt de Adobe SDK automatisch een hit. Wanneer een vals van callback is teruggekeerd, wordt de getimede actiereactie onderdrukt.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      trackTimedActionEndJsLogic(name [, callback])
      ```

      * Retourneert: N.v.t.
      * Parameters: `name`
         * Type: String
         * Naam van de getimede actie die wordt gebeëindigd
      * Parameter: `callback`
         * Type: `function(inAppDuration, totalDuration, data)`
         * Callback-methode met `inAppDuration` (getal), `totalDuration` (getal) en `data` (contextgegevensobject) in de parameters.

            U kunt de definitieve slag van wordt verzonden door SDK onderdrukken door `false` in uw callback functie terug te keren.
      * Hier volgt het codevoorbeeld voor deze methode:

         ```objective-c
         ADBMobile.trackTimedActionEndJsLogic(‘level1’, 
         function(inAppDuration, totalDuration, data) {
             // do something with final values
             return true;
             });
         ```



* **trackingTimedActionExistsJs**

   Retourneert of een getimede actie wordt uitgevoerd.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      trackingTimedActionExistsJs(name)
      ```

      * Retourneert: Bool
      * Parameter: `name`
         * Type: `String`
         * Naam van de getimede actie waarvoor u bestaan moet controleren.
   * Hier volgt het codevoorbeeld voor deze methode:


      ```objective-c
      var actionExists = ADBMobile.trackTimedActionExistsJs(‘level1’);
      ```


* **trackingIdentifier**

   Retourneert de automatisch gegenereerde bezoeker-id.

   Dit is een app-specifieke unieke bezoeker-id die wordt gegenereerd door de servers van Adobe. Als de servers van Adobe niet kunnen worden bereikt op het moment van de generatie, wordt de id gegenereerd met behulp van de CFUUID van Apple. De waarde wordt gegenereerd bij de eerste keer starten en wordt vanaf dat punt opgeslagen en gebruikt. Deze id blijft behouden tussen upgrades van apps, wordt opgeslagen en hersteld tijdens het back-upproces van de standaardtoepassing en wordt verwijderd wanneer de app wordt verwijderd.

   >[!TIP]
   >
   >Als uw app upgradet van de Experience Cloud 3.x naar 4.x SDK, wordt de vorige aangepaste of automatisch gegenereerde bezoeker-id opgehaald en opgeslagen als de aangepaste gebruikers-id. Op deze manier blijven bezoekersgegevens behouden tussen SDK-upgrades. Voor nieuwe installaties op 4.x SDK, is het gebruikersherkenningsteken `nil`, en het volgen herkenningsteken wordt gebruikt. Zie de rij userIdentifier hieronder voor meer informatie.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      trackingIdentifier()
      ```

      * Retourneert: `String`
      * Parameters: Geen
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var trackingId = ADBMobile.trackingIdentifier();
      ```


* **trackingSendQueuedHits**

   Hiermee dwingt u de bibliotheek alle treffers in de offline wachtrij te verzenden, ongeacht het aantal dat momenteel in de wachtrij staat.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      trackingSendQueuedHits()
      ```

      * Retourneert: N.v.t.
      * Parameters: Geen
   * Hier volgt het codevoorbeeld voor deze methode:


      ```objective-c
      ADBMobile.trackingSendQueuedHits();
      ```


* **trackingClearQueue**

   Wist alle treffers van de off-line rij.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      trackingClearQueue()
      ```

      * Retourneert: N.v.t.
      * Parameters: Geen
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.trackingClearQueue();
      ```


* **trackingGetQueueSize**

   Hiermee wordt het aantal treffers opgehaald dat momenteel in de offline wachtrij staat.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      trackingGetQueueSize()
      ```

      * Retourneert: Getal
      * Parameters: Geen
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var queueSize = ADBMobile.trackingGetQueueSize();
      ```


## Methoden van Audience Manager {#section_0155C4DF04644EDAAF6159C420A158DE}

* **publiekVisitorProfile**

   Retourneert het bezoekersprofiel dat het laatst is verkregen.

   Retourneert null als er nog geen signaal is verzonden. Het bezoekersprofiel wordt opgeslagen in `NSUserDefaults` zodat u eenvoudig toegang hebt tot meerdere startpagina&#39;s van uw app.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      audienceVisitorProfile()
      ```

      * Retourneert: Object
      * Parameters: Geen
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var profile = ADBMobile.audienceVisitorProfile();
      ```


* **publiekDpid**

   Retourneert de huidige DPID.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      audienceDpid()
      ```

      * Retourneert: String
      * Parameters: Geen
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var dpid = ADBMobile.audienceDpid();
      ```


* **publiekDpuuid**

   Retourneert de huidige DPUUID.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      audienceDpuuid()
      ```

      * Retourneert: `String`
      * Parameters: Geen
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var dpuuid = ADBMobile.audienceDpuuid();
      ```


* **publiekSetDpidDpuuid**

   Stelt dpid en dpuuid in en als deze zijn ingesteld, worden ze samen met elk signaal verzonden.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      audienceSetDpidDpuuid(dpid, dpuuid)
      ```

      * Retourneert: N.v.t.
      * Parameter: `dpid`
         * Type: `String`
         * ID van de gegevensaanbieder van Audience Manager.
      * Parameter: `dpuuid`
         * Type: `String`
         * Identifier voor de combinatie van gebruiker en gegevensaanbieder.
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.audienceSetDpidDpuuid(‘myDpid’, ‘userDpuuid’);
      ```


* **publiekSignalWithDataJsCallback**

   Verzendt de Manager van de Publiek een signaal met eigenschappen en krijgt de passende segmenten die in een callback functie zijn teruggekeerd.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      audienceSignalWithDataJsCallback(traits [, callback])
      ```

      * Parameter: `traits`
         * Type: Object
         * Traits dictionary for this user.
      * Parameter: `callback`
         * Type: function(profile)
         * Het profiel dat door de Manager van het Publiek in de parameter voor de callback functie is teruggekeerd.
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.audienceSignalWithDataJsCallback({‘trait’:’something’}, 
      function(profile) {
          //do something with the user’s segments found in profile
           });
      ```



* **publiekReset**

   Hiermee wordt de UUID van Audience Manager opnieuw ingesteld en wordt het huidige bezoekersprofiel gewist.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      audienceReset()
      ```

      * Retourneert: N.v.t.
      * Parameter: Geen
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.audienceReset();
      ```


## ID-servicemethoden {#section_BEB6DA612EA4423FB354B65ECC941335}

* **bezoekerMarketingCloudID**

   Haalt de Experience Cloud ID op van de ID-service.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      visitorMarketingCloudID()
      ```

      * Retourneert: String
      * Parameters: Geen
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var mcid = ADBMobile.visitorMarketingCloudID();
      ```


* **bezoekerSyncIdentifiers**

   Naast de Experience Cloud-id kunt u aanvullende klant-id&#39;s instellen die aan elke bezoeker moeten worden gekoppeld. De bezoeker-API accepteert meerdere Customer ID&#39;s voor dezelfde bezoeker, met een id voor het klanttype om het bereik van de verschillende klant-id&#39;s te scheiden. Deze methode komt overeen met setCustomerIDs in de JavaScript-bibliotheek.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      visitorSyncIdentifiers(identifiers)
      ```

      * Retourneert: N.v.t.
      * Parameter: `identifiers`

         * Type: `Object`
         * Id&#39;s die moeten worden gesynchroniseerd met de id-service voor deze gebruiker.
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.visitorSyncIdentifiers({‘idType’:’idValue’});
      ```


* **bezoekerSyncIdentifiersAuthenticationState**

   Synchroniseert de verstrekte herkenningstekens aan de dienst van identiteitskaart

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      visitorSyncIdentifiersAuthenticationState(identifiers, authState)
      ```

      * Retourneert: N.v.t.
      * Parameters: `identifiers`
         * Type: `Object`
         * Id&#39;s die moeten worden gesynchroniseerd met de id-service voor deze gebruiker.
      * Parameter: `authState`
         * Type: ADBMobileVisitorAuthenticationState
         * De verificatiestatus van de gebruiker en mogelijke waarden zijn:
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.visitorSyncIdentifiersAuthenticationState({'myIdType':'valueForUser'}, ADBMobileVisitorAuthenticationStateLoggedOut)
      ```



* **bezoekerSyncIdentifierWithTypeIdentifierAuthenticationState**

   Hiermee synchroniseert u het opgegeven id-type en de opgegeven waarde met de id-service.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      visitorSyncIdentifierWithTypeIdentifierAuthenticationState(idType, identifier, authState)
      ```

      * Retourneren: N.v.t.
      * Parameter: `idType`
         * Type: `String`
         * Type id dat u synchroniseert.
      * Parameter: `identifier`
         * Type: `String`
         * Waarde van de id die u synchroniseert.
      * Parameter: `authState`
         * Type: ADBMobileVisitorAuthenticationStateAuthentication-status van de gebruiker. Mogelijke waarden zijn:
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBMobile.visitorSyncIdentifierWithTypeIdentifierAuthenticationState('myIdType', 'valueForUser', 
      ADBMobileVisitorAuthenticationStateAuthenticated);
      ```


* **bezoekerGetIDsJs**

   Haalt een array van alleen-lezen ADBVisitorID-objecten op. Het volgende codevoorbeeld is een voorbeeld van een object VisitorID:

   ```js
   {
       idType: "abc",
       authenticationState: 1, 
       identifier: "123"
   }
   ```

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      visitorGetIDsJs()
      ```

      * Retourneert: `Array [Object]`

      * Parameters: Geen
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var myVisitorIds = ADBMobile.visitorGetIDsJs();
      ```


## Doelmethoden {#section_F9F7EC2B9B7C41AFBCA2458F9F138634}

* **targetThirdPartyID**

   Retourneert de id van de derde.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      targetThirdPartyID()
      ```

      * Retourneert: `String`
      * Parameters: Geen
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var thirdPartyID = ADBMobile.targetThirdPartyID();
      ```


* **targetSetThirdPartyID**

   Hiermee stelt u de id van een derde in.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      targetSetThirdPartyID(thirdPartyID)
      ```

      * Retourneert: N.v.t.
      * Parameters: `thirdPartyID`
         * Type: `String`
         * Identiteitskaart van de derde voor doelverzoeken te gebruiken.
   * Hier volgt het codevoorbeeld voor deze methode:

   ```objective-c
   ADBMobile.targetSetThirdPartyID(‘thirdPartyID’);
   ```

* **targetPcID**

   Retourneert de PcID.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      targetPcID()
      ```

      * Retourneert: `String`
      * Parameters: Geen
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var pcID = ADBMobile.targetPcID();
      ```


* **targetSessionID**

   Retourneert de sessie-id.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      targetSessionID()
      ```

      * Retourneert: `String`
      * Parameters: Geen
   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      var sessionID = ADBMobile.targetSessionID();
      ```
