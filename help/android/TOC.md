---
audience: end-user
user-guide-title: Android-handleiding voor mobiele services
breadcrumb-title: Android Guide
source-git-commit: 78b7a623a7811cf0ede789c74b3ca7a80372c9f4
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 6%

---


# Android-handleiding voor mobiele services{#android}

+ [Android SDK 4.x voor Experience Cloud-oplossingen](overview.md)
+ [Aanvullende informatie](rel-notes.md)
+ Aan de slag{#getting-started-android}
   + [Aan de slag](getting-started/getting-started.md)
   + [Voordat u begint](getting-started/requirements.md)
   + [Kernimplementatie en levenscyclus](getting-started/dev-qs.md)
   + [Verwerkingsregels en contextgegevens](getting-started/proc-rules.md)
   + [Migreren naar de Android 4.x-bibliotheek](getting-started/migration-v3.md)
+ Configuratie{#configuration-android}
   + [Overzicht van configuratie](configuration/configuration.md)
   + [ADBMobile JSON-configuratiebestand](configuration/json-config/json-config.md)
   + [Het JSON-configuratiepad voor ADBMobile overschrijven](configuration/json-config/json-config-remote.md)
   + [Batch](configuration/hit-batching.md)
   + [Configuratiemethoden](configuration/methods.md)
+ [Levenscycluswaarden](metrics.md)
+ Analytics{#analytics-android}
   + [Overzicht van analysemogelijkheden](analytics-main/analytics-main.md)
   + [Toepassingsstaten bijhouden](analytics-main/states.md)
   + [Toepassingsacties bijhouden](analytics-main/actions.md)
   + [Toepassingscrashes bijhouden](analytics-main/crashes.md)
   + [Gedetailleerde acties](analytics-main/timed-actions.md)
   + [Levenswaarde bezoeker](analytics-main/lifetime-value.md)
   + Variabele voor producten{#products-variable}
      + [Variabele voor producten](analytics-main/products/products.md)
      + [Variabele voor producten met verkoopbare variabelen en productspecifieke gebeurtenissen](analytics-main/products/products-variable-evars-events.md)
   + [Gebeurtenisserialisatie](analytics-main/event-serialization.md)
   + [Video Analytics](analytics-main/video-qs.md)
   + Postbacks{#postbacks}
      + [Overzicht van postbacks](analytics-main/postbacks/postbacks.md)
      + [Postbacks, voorbeeld](analytics-main/postbacks/postback-example.md)
      + [PII-postbacks](analytics-main/postbacks/c-pii-postbacks.md)
   + [Analysemethoden](analytics-main/analytics-methods.md)
+ Acquisitie{#acquisition-android}
   + [Overzicht van overname](acquisition-main/acquisition-main-android.md)
   + [Aanschaf van mobiele apps](acquisition-main/acquisition.md)
   + [Verwervingsmethoden](acquisition-main/acquisition-methods.md)
   + Diepkoppelingen bijhouden{#tracking-deep-links}
      + [Diepkoppelingen bijhouden](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Uitgestelde diepe koppelingen van derden bijhouden](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [Verwerving marketinglink testen](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [V3-overname testen](acquisition-main/t-testing-version-3-acquisition.md)
   + [Verouderde overname testen](acquisition-main/t-testing-acquisition.md)
   + [Problemen met ophalen oplossen](acquisition-main/troubleshoot-acquisition-testing.md)
+ Berichten{#messaging-android}
   + [Overzicht van berichten](messaging-main/messaging-main-android.md)
   + In-app berichten{#inapp-messaging}
      + [In-app berichten](messaging-main/messaging/messaging.md)
      + [In-app-berichten oplossen](messaging-main/messaging/in-apps-ts.md)
   + Push messaging{#push-messaging}
      + [Push messaging](messaging-main/push-messaging/push-messaging.md)
      + [Push messaging implementeren met deep linking](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [Rich push-berichten ontvangen](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [Pushberichten oplossen](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Locatie{#location}
   + [Overzicht van locatie](location/location.md)
   + [Geolocatie en aandachtspunten](location/geo-poi.md)
   + [Beacon bijhouden](location/beacon.md)
+ Target{#target-android}
   + [Doeloverzicht](target-main/target-main.md)
   + [Doelconfiguratie](target-main/target.md)
   + [Doelmethoden](target-main/c-target-methods.md)
   + [Inhoud van Prefetch-aanbieding in Android](target-main/c-mob-target-prefetch-android.md)
   + [Doelvoorvertoning op Android](target-main/c-mob-target-preview-android.md)
+ Experience Cloud{#experience-cloud-android}
   + [Overzicht van Experience Cloud](c-marketing-cloud/c-marketing-cloud.md)
   + [Experience Cloud ID-configuratie](c-marketing-cloud/mcvid.md)
   + [Methoden van Adobe Experience Platform Identity Service](c-marketing-cloud/mc-methods.md)
+ Audience Manager{#audience-manager-android}
   + [Overzicht van Audience Manager](audience-manager/audience-manager.md)
   + [Configuratie van Audience Manager](audience-manager/audiencemgmt.md)
   + [Methoden van Audience Manager](audience-manager/c-audience-manager-methods.md)
+ Woorden{#wearables-android}
   + [Overzicht van Wearables](wearables/wearables.md)
   + [Android-oormerken: aan de slag](wearables/android-wearable.md)
   + [Android-oormerken: aanvullende opmerkingen](wearables/c-android-wearables--additional-notes.md)
+ Android SDK-referentie{#sdk-reference-android}
   + [Overzicht van de Android SDK-naslaggids](/help/android/reference/reference.md)
   + [Toepassings-id&#39;s](/help/android/reference/app-ids.md)
   + [Bezoekerspatiëring tussen een app en een mobiel web](/help/android/reference/hybrid-app.md)
   + [Android-widgets](/help/android/reference/widgets.md)
+ Privacy en algemene gegevensbeschermingsverordening{#gdpr-privacy-android}
   + [Overzicht van privacy en GDPR](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [Opgeslagen id&#39;s ophalen](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [De status van de gebruiker instellen](c-mob-privacy-gdpr-android/privacy.md)
+ PhoneGap-plug-in{#phonegap-android}
   + [Overzicht van de PhoneGap-plug-in](phonegap/phonegap.md)
   + [Methoden van PhoneGap-plug-in](phonegap/phonegap-methods.md)
