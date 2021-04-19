---
description: Klassen en methoden die worden geleverd door de Windows 8.1 Universal App Store-bibliotheek.
seo-description: Klassen en methoden die worden geleverd door de Windows 8.1 Universal App Store-bibliotheek.
seo-title: Methoden van SDK
solution: Experience Cloud,Analytics
title: Methoden van SDK
topic-fix: Developer and implementation
uuid: 0f558ff4-73d3-4439-9d51-62fbd74d2cea
exl-id: c328fd79-6e10-43b7-9d08-8da395098b60
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 21%

---

# Methoden van SDK {#sdk-methods}

Klassen en methoden die worden geleverd door de Windows 8.1 Universal App Store-bibliotheek.

>[!TIP]
>
>Wanneer u `winmd` methodes van winJS (JavaScript) gebruikt, hebben alle methodes automatisch hun eerste brief verminderd.

* **GetVersion (winJS: getVersion)**

   Retourneert de huidige versie van de Adobe Mobile-bibliotheek.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      varADB = ADBMobile;var libVersion = ADB.Config.getVersion(); 
      ```

* **GetPrivacyStatusAsync (winJS: getPrivacyStatusAsync)**

   Retourneert de opsomming van de privacystatus voor de huidige gebruiker.

   * `ADBMobilePrivacyStatusOptIn` - treffers worden onmiddellijk verzonden.
   * `ADBMobilePrivacyStatusOptOut` - treffers worden genegeerd.
   * `ADBMobilePrivacyStatusUnknown` - Als uw rapportsuite is ingeschakeld voor tijdstempels, worden treffers opgeslagen totdat de status van de privacy verandert in aanmelden (resultaten worden verzonden) of Afmelden (resultaten worden verwijderd). Als uw rapportsuite niet is ingeschakeld voor tijdstempels, worden treffers genegeerd totdat de privacystatus verandert en u zich aanmeldt.

      De standaardwaarde wordt ingesteld in het bestand [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/c.json.md).

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus> ^getPrivacyStatusAsync(); 
      ```

   * Hier volgen de codevoorbeelden voor deze methode:

      ```csharp
      public enum class ADBMobilePrivacyStatus : int  {
        ADBMobilePrivacyStatusOptIn = 1, 
        ADBMobilePrivacyStatusOptOut =  2,
        ADBMobilePrivacyStatusUnknown = 3
      };
      ```

      ```js
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
      status = privacyStatus;
      }); 
      ```

* **SetPrivacyStatus (winJS: setPrivacyStatus)**

   Stelt de privacystatus voor de huidige gebruiker in op `status`. Stel een van de volgende waarden in:

   * `ADBMobilePrivacyStatusOptIn` - treffers worden onmiddellijk verzonden.
   * `ADBMobilePrivacyStatusOptOut` - treffers worden genegeerd.
   * `ADBMobilePrivacyStatusUnknown` - Als uw rapportsuite is ingeschakeld voor tijdstempels, worden treffers opgeslagen totdat de status van de privacy verandert in aanmelden (resultaten worden verzonden) of Afmelden (resultaten worden verwijderd). Als uw rapportsuite niet is ingeschakeld voor tijdstempels, worden treffers genegeerd totdat de privacystatus verandert en u zich aanmeldt.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```csharp
      public enum class ADBMobilePrivacyStatus : int {
        ADBMobilePrivacyStatusOptIn = 1,
        ADBMobilePrivacyStatusOptOut = 2,
        ADBMobilePrivacyStatusUnknown = 3
        }; 
      ```

      ```js
      var ADB = ADBMobile;
      ADB.Config.setPrivacyStatus(ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn); 
      ```

* **GetLifetimeValue (winJS: getLifetimeValue)**

   Retourneert de levensduurwaarde van de huidige gebruiker. De standaardwaarde is 0.

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

   Retourneert de aangepaste gebruikers-id als er een aangepaste id is ingesteld. Retourneert null als er geen aangepaste id is ingesteld. De standaardwaarde is `null`.

   >[!TIP]
   >
   >Als uw app upgradet van de Experience Cloud 3.x naar 4.x-SDK, wordt de vorige id (aangepast of automatisch gegenereerd) opgehaald en opgeslagen als de aangepaste gebruikers-id. Op deze manier blijven bezoekersgegevens behouden tussen upgrades van de SDK. Voor nieuwe installaties op 4.x SDK, is het gebruikers herkenningsteken `null` tot reeks.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static Platform::String^GetUserIdentifier();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **SetUserIdentifier (winJS: setUserIdentifier)**

   Hiermee stelt u de gebruikersnaam in op `identifier`.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
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

      ```js
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging(); 
      ```

* **SetDebugLogging (winJS: setDebugLogging)**

   Stelt de voorkeur voor foutopsporing in op `debugLogging`. Debug registreren werkt slechts wanneer het gebruiken van zuivert versie van de bibliotheek, negeert de versieversie dit het plaatsen.

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

   Geeft aan de SDK aan dat levenscyclusgegevens moeten worden verzameld voor gebruik in alle oplossingen in de SDK. Zie [Levenscyclusmetriek](/help/windows-appstore/metrics.md) voor meer informatie.

   >[!TIP]
   >
   >Roep deze methode aan in de methode `onResume()` in elke Activiteit binnen van uw toepassing, zoals aangetoond in het volgende voorbeeld. Wij adviseren ook het overgaan van de Activiteit of de Dienst als contextvoorwerp in plaats van de globale context van de Toepassing.

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

   Geeft aan de SDK aan dat de app is gepauzeerd, zodat de levenscycluswaarden correct worden berekend. Bij pauzeren wordt bijvoorbeeld een tijdstempel verzameld om de duur van de vorige sessie te bepalen. Hierdoor wordt ook een vlag ingesteld zodat de levenscyclus correct weet dat de app niet vastloopt. Zie [Levenscyclusmetriek](/help/windows-appstore/metrics.md) voor meer informatie.

   >[!TIP]
   >
   >Roep deze methode aan in de `onPause()` methoden in elke activiteit binnen Uw toepassing, zoals in het voorbeeld wordt getoond. Wij adviseren ook het overgaan van de Activiteit of de Dienst als contextvoorwerp in plaats van de globale context van de Toepassing.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```
