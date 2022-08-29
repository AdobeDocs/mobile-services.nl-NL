---
audience: end-user
user-guide-title: iOS-handleiding voor mobiele services
breadcrumb-title: iOS Guide
source-git-commit: 78b7a623a7811cf0ede789c74b3ca7a80372c9f4
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 3%

---


# iOS-handleiding voor mobiele services {#ios}

+ [iOS SDK 4.x voor Experience Cloud Solutions](overview.md)
+ [Aanvullende informatie](rel-notes.md)
+ Aan de slag {#getting-started-ios}
   + [Aan de slag - overzicht](getting-started/getting-started.md)
   + [Voordat u begint](getting-started/requirements.md)
   + [Kernimplementatie en levenscyclus](getting-started/dev-qs.md)
   + [Verwerkingsregels en contextgegevens](getting-started/proc-rules.md)
   + [Swift-integratie](getting-started/swift-integration.md)
   + [Migreren naar de 4.x iOS-bibliotheek](getting-started/migration-v3.md)
+ Configuratie {#config-ios}
   + [Overzicht van configuratie](configuration/configuration.md)
   + [ADBMobile JSON config](configuration/json-config/json-config.md)
   + [Het JSON-configuratiepad voor ADBMobile overschrijven](configuration/json-config/json-config-remote.md)
   + [Batch](configuration/hit-batching.md)
   + [Configuratiemethoden](configuration/sdk-methods.md)
   + [Beveiliging van toepassingsvervoer](configuration/app-transport-security.md)
+ [Levenscycluswaarden](metrics.md)
+ Analytics {#analytics-ios}
   + [Overzicht van analysemogelijkheden](analytics-main/analytics-main.md)
   + [Toepassingsstaten bijhouden](analytics-main/states.md)
   + [Toepassingsacties bijhouden](analytics-main/actions.md)
   + [Toepassingscrashes bijhouden](analytics-main/crashes.md)
   + [Gedetailleerde acties](analytics-main/timed-actions.md)
   + [Levenswaarde bezoeker](analytics-main/lifetime-value.md)
   + Variabele voor producten {#products-variable}
      + [Variabele voor producten](analytics-main/products/products.md)
      + [Variabele voor producten met verkoopbare variabelen en productspecifieke gebeurtenissen](analytics-main/products/products-variable-evars-events.md)
   + [Gebeurtenisserialisatie](analytics-main/event-serialization.md)
   + [Video Analytics](analytics-main/video-qs.md)
   + Postbacks {#postbacks}
      + [Overzicht van postbacks](analytics-main/postback/postback.md)
      + [Voorbeeld van terugzending](analytics-main/postback/postback-example.md)
      + [PII-postbacks](analytics-main/postback/c-pii-postbacks.md)
   + [Analysemethoden](analytics-main/analytics-methods.md)
+ Acquisitie {#acquisition-ios}
   + [Overzicht van overname](acquisition-main/acquisition-main.md)
   + [Aanschaf van mobiele apps](acquisition-main/acquisition.md)
   + [Verwervingsmethoden](acquisition-main/c-acquisition-methods.md)
   + Diepkoppelingen bijhouden {#tracking-deep-links}
      + [Diepkoppelingen bijhouden](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Uitgestelde diepe koppelingen van derden bijhouden](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [Verwerving marketinglink testen](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [V3-overname testen](acquisition-main/t-testing-version-3-acquisition.md)
   + [Verouderde overname testen](acquisition-main/t-testing-acquisition.md)
   + [Zoeken in Apple-advertenties](acquisition-main/c-apple-search-ads.md)
+ Berichten {#messaging-ios}
   + [Overzicht van berichten](messaging-main/messaging-main.md)
   + In-app berichten {#in-app-messaging}
      + [In-app berichten](messaging-main/messaging/messaging.md)
      + [Problemen met in-app messaging oplossen](messaging-main/messaging/in-apps-ts.md)
   + Push messaging {#push-messaging}
      + [Push messaging](messaging-main/push-messaging/push-messaging.md)
      + [Push messaging implementeren met deep linking](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [Rich push-berichten ontvangen](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [Probleemoplossing voor pushberichten](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Locatie {#location-ios}
   + [Overzicht van locatie](location/location.md)
   + [Geolocatie en aandachtspunten](location/geo-poi.md)
   + [Beacon tracking](location/ibeacon.md)
+ Target {#target-ios}
   + [Doeloverzicht](target-main/target-main.md)
   + [Doelmethoden](target-main/c-target-methods.md)
   + [Inhoud van voorkeursaanbieding in iOS](target-main/c-mob-target-prefetch-ios.md)
   + [Voorvertoning doel in iOS](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Overzicht van Experience Cloud](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud-id](marketing-cloud/mcvid.md)
   + [Methoden van Adobe Experience Platform Identity Service](marketing-cloud/mc-methods.md)
+ [Methoden van Audience Manager](amm/aam-methods.md)
+ Apple TV-implementatie met tvOS {#apple-tv-implementation-tvos-ios}
   + [Apple TV-implementatie met tvOS](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [Adobe Target voor TVML/TVJS](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [TVJS-methoden](apple-tv-implementation-tvos/tvjs-methods.md)
+ iOS-extensie-implementatie {#ios-ext}
   + [iOS-extensie-implementatie](ios-ext/ios-ext.md)
   + [Zelfstandige extensie-implementatie](ios-ext/c-stand-alone-extension-implementation.md)
+ [Apple Watch-implementatie met WatchOS 2](apple-watch-implementation-watchkit.md)
+ iOS SDK-referentie {#sdk-reference-ios}
   + [iOS SDK-referentie](reference/reference.md)
   + [Toepassings-id&#39;s](reference/app-ids.md)
   + [Bezoekerspatiëring tussen een app en een mobiel web](reference/hybrid-app.md)
   + [iOS-apparaatversies](reference/device-versions.md)
+ Privacy en algemene gegevensbeschermingsverordening{#privacy-gdpr-ios}
   + [Privacy en algemene gegevensbeschermingsverordening](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [Opgeslagen id&#39;s ophalen](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [De status van de gebruiker instellen](c-mob-privacy-gdpr-ios/privacy.md)
+ PhoneGap-plug-in {#phonegap-ios}
   + [PhoneGap-plug-in](phonegap/phonegap.md)
   + [Methoden van PhoneGap-plug-in](phonegap/phonegap-methods.md)
