---
description: Gebruik de Android-SDK om het bijhouden van diepgaande koppelingen die door derden zijn uitgesteld, te implementeren.
seo-description: Gebruik de Android-SDK om het bijhouden van diepgaande koppelingen die door derden zijn uitgesteld, te implementeren.
seo-title: Het volgen van derde Uitgestelde Diepe Verbindingen
title: Het volgen van derde Uitgestelde Diepe Verbindingen
uuid: 4c798e47-7988-4a06-a191-6c4d05f6ee61
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Uitgestelde diepe koppelingen van derden bijhouden{#tracking-third-party-deferred-deep-links}

Gebruik de Android-SDK om het bijhouden van diepgaande koppelingen die door derden zijn uitgesteld, te implementeren.

## Klassieke Adobe Mobile SDK, diep koppelen {#section_D114FA1EB9664EAA82E036A990694B26}

De SDK van Adobe Mobile ondersteunt momenteel diepe koppelingen, waarbij de ontwikkelaar van de app naar verwachting de `collectLifecycleData` SDK-API van de nauw gekoppelde activiteit zal gebruiken. De SDK voegt de diepe verbindingsgegevens van de diepe verbindingsURL parameters toe. Zie Diepe koppelingen [](/help/android/acquisition-main/tracking-deep-links/tracking-deep-links.md)bijhouden voor meer informatie over hoe diep koppelingen werken in de SDK van Adobe Mobile.

## Facebook deep linking {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

Een maker van een advertentie kan een advertentie op Facebook maken als een diepe koppeling. Wanneer gebruikers op de advertentie klikken, gaat deze rechtstreeks naar de informatie waarin ze geïnteresseerd zijn in de app. De diepe koppeling is **geen** vingerprinter-URL. Tijdens de configuratie van de advertentie is er echter een optie om een diepe koppeling-URL van derden op te geven. Een toepassingsontwikkelaar die de Adobe Mobile SDK&#39;s en services gebruikt, moet de door Adobe Mobile Service geconfigureerde vingerprinter-URL in dit veld invoeren. Als alles correct is ingesteld, geeft de SDK van Facebook deze URL door aan de toepassing wanneer de app wordt geïnstalleerd of gestart.

## SDK&#39;s instellen {#section_834CD3109175432B8173ECB6EA7DE315}

Als de ontwikkelaar van de app voorbereidingen wil treffen om ondersteuning voor uitgebreide koppelingen naar Facebook toe te voegen met de SDK van Adobe Mobile, voert hij de volgende taken uit:

* Aan de slag met de Android-SDK

   Zie Aan de [slag met Android SDK](https://developers.facebook.com/docs/android/getting-started) voor meer informatie.

* Diepkoppeling instellen

   Voor meer informatie, zie [Deep Linking Opstelling](https://developers.facebook.com/docs/app-ads/deep-linking#os).

Als de toepassing op de juiste wijze is ingesteld, moet de `trackAdobeDeepLink()` API het mogelijk maken om de uitgebreide koppelingsgegevens van de aanschafcampagne op Facebook te verzamelen en naar Adobe Mobile Service te verzenden. Als de melding bij de installatie niet naar Adobe Mobile Service is verzonden bij de eerste keer dat de toepassing wordt gestart, wordt deze informatie toegevoegd aan de hit Levenscyclus. Anders wordt de koppeling verzonden als een hit met een diepe koppeling van Adobe.

>[!TIP]
>
>Zorg ervoor dat de diepe verbinding URL een sleutel genoemd heeft `a.deeplink.id`. Als in de URL de parameter deep link ID ontbreekt, worden de URL-parameters niet aan de contextgegevens toegevoegd.

Als de koppeling kan worden toegeschreven aan een overname, slaat de SDK van Adobe Mobile de aanschafgegevens op via de diepe koppeling op Facebook die werd gebruikt om te bellen `trackAdobeDeepLink()`. Deze gegevens zijn in de toekomst beschikbaar voor de Adobe Mobile SDK. Als een callback is geregistreerd, wordt de callback van Adobe ook gebruikt om de gegevens terug naar de cliënt te verzenden.

## deep linking inschakelen in een Android-toepassing {#section_64C15E269E89424B8E3D029F88094620}

1. Registreer de toepassing om diepe koppelingen te verwerken.

   Zie [Andere apps toestaan om uw activiteit](https://developer.android.com/training/basics/intents/filters.html)te starten voor meer informatie.

1. Koppel de SDK&#39;s van Facebook.

   Voer de stappen in de [Aan de slag-Android-SDK](https://developers.facebook.com/docs/android/getting-started)uit om de Facebook-afhankelijkheid van de greep in de app toe te voegen.

1. Als u de SDK van Facebook wilt initialiseren, voert u de instructies in de sectie *Android Studio Setup* in.
1. Bellen `trackAdobeDeepLink()` vanuit de hoofdactiviteit.

   ```java
   @Override 
   protected void onResume() { 
      super.onResume(); 
      AppEventsLogger.activateApp(this); 
      /* 
       * Adobe Tracking - Config 
       * 
       * call collectLifecycleData() to begin collecting lifecycle data 
       * must be in the onResume() of every activity in your app 
       */ 
      Config.collectLifecycleData(this);
   
      AppLinkData.fetchDeferredAppLinkData(this, 
            new AppLinkData.CompletionHandler() { 
               @Override 
               public void onDeferredAppLinkDataFetched(AppLinkData appLinkData) { 
                  // Process app link data 
                  if (appLinkData != null) { 
                     Config.trackAdobeDeepLink(appLinkData.getTargetUri()); 
                  } 
               } 
            } 
      ); 
   }
   ```

