---
description: Klassen en methoden die worden geleverd door de Universal Windows Platform-bibliotheek.
seo-description: Klassen en methoden die worden geleverd door de Universal Windows Platform-bibliotheek.
seo-title: Methoden van SDK
solution: Marketing Cloud,Analytics
title: Methoden van SDK
topic: Developer and implementation
uuid: e3aa41d6-7bc0-4208-a662-12907c209a77
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Methoden van SDK {#sdk-methods}

Klassen en methoden die worden geleverd door de Universal Windows Platform-bibliotheek.

>[!TIP]
>
>Wanneer u methoden van winJS (JavaScript) gebruikt, wordt de eerste letter van alle methoden automatisch verlaagd. `winmd`

* **GetVersion (winJS: getVersion)**

   Retourneert de huidige versie van de Adobe Mobile-bibliotheek.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile;var libVersion = ADB.Config.getVersion();
      ```

* **GetPrivacyStatusAsync (winJS: getPrivacyStatusAsync)**

   Retourneert de opsomming van de privacystatus voor de huidige gebruiker.

   * `ADBMobilePrivacyStatusOptIn` - De berichten worden onmiddellijk verzonden.
   * `ADBMobilePrivacyStatusOptOut` - Hits worden weggegooid.
   * `ADBMobilePrivacyStatusUnknown` - Als uw rapportsuite is ingeschakeld voor tijdstempels, worden treffers opgeslagen totdat de privacystatus verandert in aanmelden (hits worden verzonden) of Afmelden (hits worden verwijderd). Als uw rapportsuite niet is ingeschakeld voor tijdstempels, worden treffers genegeerd totdat de privacystatus verandert en u zich aanmeldt.

      De standaardwaarde wordt ingesteld in het `ADBMobileConfig.json` configuratiebestand. Zie het [configuratiebestand](/help/universal-windows/c-configuration/c.json.md)ADBMobileConfig.json voor meer informatie.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus>
      ^getPrivacyStatusAsync();
      ```

   * Hier volgen de codevoorbeelden voor deze methode:

      **C Sharp**

      ```csharp
      public enum class ADBMobilePrivacyStatus : int { ADBMobilePrivacyStatusOptIn = 1, 
      ADBMobilePrivacyStatusOptOut = 2, 
      ADBMobilePrivacyStatusUnknown = 3};
      ```

      **JavaScript**

      ```javascript
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
        status = privacyStatus;}
      );
      ```

* **SetPrivacyStatus (winJS: setPrivacyStatus)**

   Hiermee stelt u de privacystatus voor de huidige gebruiker in `status`. Stel een van de volgende waarden in:
   * `ADBMobilePrivacyStatusOptIn` - treffers worden onmiddellijk verzonden.
   * `ADBMobilePrivacyStatusOptOut` - treffers worden genegeerd.
   * `DBMobilePrivacyStatusUnknown` - Als uw rapportsuite is ingeschakeld voor tijdstempels, worden treffers opgeslagen totdat de privacystatus verandert in aanmelden (hits worden verzonden) of Afmelden (hits worden verwijderd). Als uw rapportsuite niet is ingeschakeld voor tijdstempels, worden treffers genegeerd totdat de privacystatus verandert en u zich aanmeldt.

      * Hier volgt de syntaxis voor deze methode:

         ```csharp
         static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
         ```

      * Hier volgen de codevoorbeelden voor deze methode:

         **C-scherp**

         ```csharp
         public enum class ADBMobilePrivacyStatus : int { 
           ADBMobilePrivacyStatusOptIn = 1, 
           ADBMobilePrivacyStatusOptOut = 2
           ADBMobilePrivacyStatusUnknown = 3
         };
         ```

         **JavaScript**

         ```js
         var ADB = ADBMobile;
         ADB.Config.setPrivacyStatus (ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn
         );
         ```

* **GetLifetimeValue (winJS: getLifetimeValue)**

   Retourneert de levensduurwaarde van de huidige gebruiker. De standaardwaarde is `0`.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static float GetLifetimeValue(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile;
      var ltv = ADB.Config.getLifetimeValue();
      ```

* **GetUserIdentifier (winJS: getUserIdentifier)**

   Retourneert de aangepaste gebruikers-id als er een aangepaste id is ingesteld. Retourneert `null` of er geen aangepaste id is ingesteld.
De standaardwaarde is `null`.

   >[!IMPORTANT]
   >
   >Als uw app upgradet van de Experience Cloud 3.x naar 4.x SDK, wordt de vorige id-service (aangepast of automatisch gegenereerd) opgehaald en opgeslagen als de aangepaste gebruikers-id. Op deze manier blijven bezoekersgegevens behouden tussen upgrades van de SDK. Voor nieuwe installaties op 4.x SDK, is het gebruikersherkenningsteken `null` tot reeks.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static Platform::String ^GetUserIdentifier(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```csharp
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **SetUserIdentifier (winJS: setUserIdentifier)**

   Hiermee stelt u de gebruikers-id in op `identifier`.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId");
      ```

* **GetDebugLogging (winJS: getDebugLogging)**

   Retourneert de huidige voorkeur voor foutopsporing. De standaardwaarde is `false`.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static bool GetDebugLogging();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```javascript
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging();
      ```

* **SetDebugLogging (winJS: setDebugLogging)**

   Hiermee stelt u de voorkeur voor foutopsporing in op `debugLogging`. Debug registreren werkt slechts wanneer het gebruiken van zuivert versie van de bibliotheek, negeert de versieversie dit het plaatsen.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void SetDebugLogging(bool debugLogging);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true);
      ```

* **CollectLifecycleData (winJS: collectionLifecycleData)**

   Geeft aan de SDK aan dat levenscyclusgegevens moeten worden verzameld voor gebruik in alle oplossingen in de SDK. Zie [Levenscyclusmetriek](/help/universal-windows/metrics.md)voor meer informatie.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void CollectLifecycleData();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData();
      ```

* **PauseCollecting &#x200B; LifecycleData (winJS: pauseCollecting &#x200B; LifecycleData)**

   Geeft aan de SDK aan dat de app is gepauzeerd, zodat de levenscycluswaarden correct worden berekend. Bij pauzeren wordt bijvoorbeeld een tijdstempel verzameld om de duur van de vorige sessie te bepalen. Hierdoor wordt ook een vlag ingesteld zodat de levenscyclus correct weet dat de app niet vastloopt. Zie [Levenscyclusstatistieken](/help/universal-windows/metrics.md)voor meer informatie.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData(); 
      ```