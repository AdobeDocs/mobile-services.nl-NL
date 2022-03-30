---
description: Verwervingskoppelingen met unieke volgcodes kunnen worden gegenereerd in Adobe Mobile-services. Wanneer een gebruiker een app downloadt en uitvoert vanuit de App Store nadat hij op de gegenereerde koppeling heeft geklikt, verzamelt de SDK automatisch de overnamegegevens en stuurt deze naar Adobe Mobile-services.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Mobiele app-acquisitie
topic-fix: Developer and implementation
uuid: 4d32eae9-e856-4e40-8a29-2b5bccd106e0
exl-id: 266f0266-38f5-410b-ae14-92874fb0e7ce
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 0%

---

# Aanschaf Mobile-app {#mobile-app-acquisition}

Verwervingskoppelingen met unieke volgcodes kunnen worden gegenereerd in Adobe Mobile-services. Wanneer een gebruiker een app downloadt en uitvoert vanuit de App Store nadat hij op de gegenereerde koppeling heeft geklikt, verzamelt de SDK automatisch de overnamegegevens en stuurt deze naar Adobe Mobile-services.

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de SDK van Adobe Experience Platform Mobile? Klikken [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar Adobe Experience Platform Launch om aan de slag te gaan.
* Ga naar [Github: Adobe Experience Platform SDK&#39;s](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
>Om Acquisitie te gebruiken, **moet** hebben SDK versie 4.1 of hoger.

Verwervingskoppelingen moeten worden gemaakt in Adobe Mobile-services. Zie voor meer informatie [Verwerving](/help/using/acquisition-main/acquisition-main.md).

**In SDK-versies 4.18.0 en hoger**:

Vanaf 1 maart 2020 wordt het uitzendmechanisme van de install_reference intent door Google vervangen. Zie voor meer informatie [Wilt u InstallBroadcast nog steeds gebruiken? Schakel tegen 1 maart 2020 over naar de Play Reference API](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html). Als u informatie over de installatieverwijzing wilt blijven verzamelen in de Google Play Store, moet u uw toepassing bijwerken naar SDK versie 4.18.0 of hoger.

Met de afschrijving maakt u geen `BroadcastReceiver`, moet u de URL van de installatieverwijzing verzamelen via een nieuwe Google API en de resulterende URL doorgeven aan de SDK.

1. Voeg het Google Play-pakket met installatieverwijzing toe aan de afhankelijkheden van het onbewerkte bestand:

   `implementation 'com.android.installreferrer:installreferrer:1.1'`

1. Als u de URL van de referentie wilt ophalen van de installatiereferor-API, voert u de stappen in [De installatieverwijzing ophalen](https://developer.android.com/google/play/installreferrer/library#install-referrer).

1. Geef de referentie-URL door aan de SDK:

   `Analytics.processGooglePlayInstallReferrerUrl(referrerUrl);`

>[!IMPORTANT]
>
>Om onnodige API-aanroepen in uw app te voorkomen, raadt Google u aan de API slechts één keer onmiddellijk na de installatie aan te roepen.

Raadpleeg de documentatie bij Google voor informatie over de beste manier om de Google Play Install Referrer-API&#39;s in uw app te gebruiken. Hier volgt een voorbeeld van het gebruik van de Adobe SDK met de Google Play Install Referrer-API&#39;s:

```java
void handleGooglePlayReferrer() {
    // Google recommends only calling this API the first time you need it:
    // https://developer.android.com/google/play/installreferrer/library#install-referrer

    // Store a boolean in SharedPreferences to ensure we only call it once.
    final SharedPreferences prefs = getSharedPreferences("acquisition", 0);
    if (prefs != null) {
        if (prefs.getBoolean("referrerHasBeenProcessed", false)) {
            return;
        }
    }

    final InstallReferrerClient referrerClient = InstallReferrerClient.newBuilder(getApplicationContext()).build();
    referrerClient.startConnection(new InstallReferrerStateListener() {
        private boolean complete = false;

        @Override
        public void onInstallReferrerSetupFinished(int responseCode) {
            switch (responseCode) {
                case InstallReferrerClient.InstallReferrerResponse.OK:
                    // connection is established
                    complete();
                    try {
                        final ReferrerDetails details = referrerClient.getInstallReferrer();                        

                        // pass the install referrer url to the SDK
                        Analytics.processGooglePlayInstallReferrerUrl(details.getInstallReferrer());

                    } catch (final RemoteException ex) {
                        Log.w("Acquisition - RemoteException while retrieving referrer information (%s)", ex.getLocalizedMessage() == null ? "unknown" : ex.getLocalizedMessage());
                    } finally {
                        referrerClient.endConnection();
                    }
                    break;
                case InstallReferrerClient.InstallReferrerResponse.FEATURE_NOT_SUPPORTED:
                case InstallReferrerClient.InstallReferrerResponse.SERVICE_UNAVAILABLE:
                default:
                    // API not available in the Play Store app - nothing to do here
                    complete();
                    referrerClient.endConnection();
                    break;
            }
        }

        @Override
        public void onInstallReferrerServiceDisconnected() {
            if (!complete) {
                // something went wrong trying to get a connection, try again
                referrerClient.startConnection(this);
            }
        }

        void complete() {
            complete = true;
            SharedPreferences.Editor editor = getSharedPreferences("acquisition", 0).edit();
            editor.putBoolean("referrerHasBeenProcessed", true);
            editor.apply();
        }
    });
}
```

**In SDK-versies 4.13.1 en hoger**:

Als u de verwervingsverbindingen niet kunt gebruiken die in de Diensten van Adobe Mobile worden gecreeerd, kunnen de verwervingsgegevens nog door SDK worden verzameld en worden verzonden door Google Play Acquisition te gebruiken.

Verzamel verzamelgegevens van een standaard Google Play Acquisition-campagne:

* Gebruik de standaardmethode voor het aanschaffen van Google Play Store.

   Aangepaste acquisitiegegevens kunnen worden gebruikt met de standaard waardeparen van de Google Play Acquisition-sleutel.

* Wanneer de gebruiker een app downloadt en uitvoert als gevolg van een aankoop van een Google Play-winkel, worden de gegevens van de referentie verzameld en naar Adobe Mobile Services verzonden.

   * De gegevens worden opgeslagen en beschikbaar in het dialoogvenster `AdobeDataCallback` instantie die eerder bij de SDK is geregistreerd.

      Zie voor meer informatie [Configuratiemethoden](/help/android/configuration/methods.md).

   * De `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` of de `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` gebeurtenistype worden gebruikt.

   * Aangepaste sleutels die deel uitmaakten van de acquisitiegegevens van Google Play, krijgen een naamruimte met &quot; `a.acquisition.custom.`&quot;

Als u de Verbindingsverbindingen gebruikt die op de Diensten van Adobe Mobile werden gecreeerd, voeg douanegegevens aan de verwervingsverbinding toe door de volgende taken te voltooien:

1. Een verwervingsvariabele vooraf bepalen met &quot; `adb`&quot;.

   Wanneer de SDK de aanschafgegevens van Adobe Mobile Services ontvangt bij de eerste keer dat deze wordt gestart, worden de gegevens opgeslagen en beschikbaar in het dialoogvenster `AdobeDataCallback` instantie die eerder bij de SDK is geregistreerd. Zie voor meer informatie [Configuratiemethoden](/help/android/configuration/methods.md).

1. De `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` of de `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` gebeurtenistype wordt gebruikt.

1. De aangepaste gegevenssleutels worden vooraf ingesteld op &quot;`a.acquisition.custom.`&quot;

>[!TIP]
>
>Als u gegevens naar meerdere rapportenreeksen verzendt, gebruikt u de aankoopgegevens van de app die is gekoppeld aan de eerste rapportsuite in uw lijst met id&#39;s van rapportsuite.

Met de updates in deze sectie kan de SDK acquisitiegegevens verzenden via een acquisitie-koppeling.

## Mobiele acquisitie volgen {#section_CEA30C652AC8470784B8054E299B80FA}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie voor meer informatie *Voeg de SDK en het Dossier Config aan uw IDEA van IntelliJ of Project toe Eclipse* in [Kernimplementatie en levenscyclus](/help/android/getting-started/dev-qs.md).

1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. Implementeer de `BroadcastReceiver` voor de verwijzende partij:

   ```java
   package com.your.package.name;  // replace with your app package name
   
   import android.content.BroadcastReceiver;
   import android.content.Context;
   import android.content.Intent;
   
   public class GPBroadcastReceiver extends BroadcastReceiver {
     @Override
     public void onReceive(Context c, Intent i) {
      com.adobe.mobile.Analytics.processReferrer(c, i);
     }
   }
   ```

1. Bijwerken `AndroidManifest.xml` de `BroadcastReceiver` die is gemaakt in de vorige stap:

   ```xml
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
    <intent-filter>
     <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
   </receiver>
   ```

1. Controleer of de `ADBMobileConfig.json` bestand bevat de vereiste acquisitie-instellingen:

   ```xml
   "acquisition": {
      "server": "c00.adobe.com",
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f"
   },
   "analytics": {
     "referrerTimeout": 5,
     ...
   ```

   >[!IMPORTANT]
   >
   >Als u gegevens naar meerdere rapportenreeksen verzendt, gebruikt u de aankoopinstellingen (acquisitieserver en appid) van de app die is gekoppeld aan de eerste rapportsuite in uw lijst met id&#39;s van rapportsuite.

   De `acquisition` instellingen worden gegenereerd door Adobe Mobile-services en mogen niet worden gewijzigd. Voor meer informatie over het downloaden van aangepaste `ADBMobileConfig.json` met de `acquisition` vooraf geconfigureerde instellingen, zie [Voordat u begint](/help/android/getting-started/requirements.md).

Nadat deze instellingen zijn ingeschakeld, worden aanschafgegevens na de eerste keer dat de app wordt gestart automatisch verzonden met de eerste levenscyclusaanroep.

>[!CAUTION]
>
>`referrerTimeout` moet een waarde hoger dan 0 zijn om het aanschaffen van apps mogelijk te maken.
