---
description: Gebruik de Android-SDK om het bijhouden van diepgaande koppelingen die door derden zijn uitgesteld, te implementeren.
title: Het volgen van derde Uitgestelde Diepe Verbindingen
uuid: 4c798e47-7988-4a06-a191-6c4d05f6ee61
exl-id: d8cbc679-a512-44db-8c30-6a029ff738ae
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# Uitgestelde diepe koppelingen van derden bijhouden{#tracking-third-party-deferred-deep-links}

Gebruik de Android-SDK om het bijhouden van diepgaande koppelingen die door derden zijn uitgesteld, te implementeren.

## Diepe koppeling van de klassieke Adobe Mobile SDK {#section_D114FA1EB9664EAA82E036A990694B26}

De SDK van Adobe Mobile ondersteunt momenteel diepe koppelingen, waarbij de ontwikkelaar van de app naar verwachting de SDK-API van `collectLifecycleData` van de diep gekoppelde activiteit zal gebruiken. De SDK voegt de diepe verbindingsgegevens van de diepe verbindingsURL parameters toe. Zie [Diepe koppelingen bijhouden](/help/android/acquisition-main/tracking-deep-links/tracking-deep-links.md) voor meer informatie over hoe diep koppelen werkt in de Adobe Mobile SDK.

## Facebook deep linking {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

Een maker van een advertentie kan een advertentie op Facebook maken als een diepe koppeling. Wanneer gebruikers op de advertentie klikken, gaat deze rechtstreeks naar de informatie waarin ze geïnteresseerd zijn in de app. De diepe verbinding, is **not** een vingerprinter URL. Tijdens de configuratie van de advertentie is er echter een optie om een diepe koppeling-URL van derden op te geven. Een app-ontwikkelaar die de Adobe Mobile SDK&#39;s en services gebruikt, moet de door de Adobe Mobile Service geconfigureerde vingerprinter-URL in dit veld invoeren. Als alles correct is ingesteld, geeft de Facebook SDK deze URL door aan de toepassing wanneer de app wordt geïnstalleerd of gestart.

## SDK&#39;s instellen {#section_834CD3109175432B8173ECB6EA7DE315}

Als u Facebook deep linking-ondersteuning wilt toevoegen aan de SDK van Adobe Mobile, voert de ontwikkelaar van de app de volgende taken uit:

* Aan de slag met de Android-SDK

   Zie [Aan de slag met Android-SDK](https://developers.facebook.com/docs/android/getting-started) voor meer informatie.

* Diepkoppeling instellen

   Voor meer informatie, zie [Deep Linking Opstelling](https://developers.facebook.com/docs/app-ads/deep-linking#os).

Als de toepassing correct is ingesteld, moet de `trackAdobeDeepLink()`-API het mogelijk maken om de uitgebreide koppelingsgegevens van de Facebook-acquisitiecampagne te verzamelen en naar de Adobe Mobile Service te verzenden. Als de installatieronde bij de eerste keer dat de toepassing wordt gestart niet naar de Adobe Mobile-service is verzonden, wordt deze informatie toegevoegd aan de hit Lifecycle. Anders wordt de koppeling verzonden als een hit met een diepe Adobe-koppeling.

>[!TIP]
>
>Zorg ervoor dat de diepe verbinding URL een sleutel genoemd `a.deeplink.id` heeft. Als in de URL de parameter deep link ID ontbreekt, worden de URL-parameters niet aan de contextgegevens toegevoegd.

Als de koppeling aan een overname kan worden toegeschreven, slaat de SDK van Adobe Mobile de overnamegegevens op via de diepe koppeling van Facebook die is gebruikt om `trackAdobeDeepLink()` aan te roepen. Deze gegevens zijn in de toekomst beschikbaar voor de Adobe Mobile SDK. Als callback is geregistreerd, zal callback van Adobe ook worden gebruikt om de gegevens terug naar de cliënt te verzenden.

## deep linking inschakelen in een Android-toepassing {#section_64C15E269E89424B8E3D029F88094620}

1. Registreer de toepassing om diepe koppelingen te verwerken.

   Zie [Andere toepassingen toestaan om uw activiteit te starten](https://developer.android.com/training/basics/intents/filters.html) voor meer informatie.

1. Koppel de SDK&#39;s van Facebook.

   Voer de stappen in [Getting Started Android SDK](https://developers.facebook.com/docs/android/getting-started) uit om de Facebook-afhankelijkheid van de grijswaarden in de app toe te voegen.

1. Als u de SDK van Facebook wilt initialiseren, voert u de instructies in de sectie *Android Studio Setup* in.
1. Roep `trackAdobeDeepLink()` van de hoofdactiviteit aan.

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
