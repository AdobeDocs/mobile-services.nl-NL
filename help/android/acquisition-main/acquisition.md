---
description: Verwervingskoppelingen met unieke volgcodes kunnen worden gegenereerd in Adobe Mobile-services. Wanneer een gebruiker een app downloadt en uitvoert vanuit de App Store nadat hij op de gegenereerde koppeling heeft geklikt, verzamelt de SDK automatisch de overnamegegevens en stuurt deze naar Adobe Mobile-services.
keywords: android;library;mobile;sdk
seo-description: Verwervingskoppelingen met unieke volgcodes kunnen worden gegenereerd in Adobe Mobile-services. Wanneer een gebruiker een app downloadt en uitvoert vanuit de App Store nadat hij op de gegenereerde koppeling heeft geklikt, verzamelt de SDK automatisch de overnamegegevens en stuurt deze naar Adobe Mobile-services.
seo-title: Mobiele app-acquisitie
solution: Experience Cloud,Analytics
title: Mobiele app-acquisitie
topic: Developer and implementation
uuid: 4d32eae9-e856-4e40-8a29-2b5bccd106e0
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 1%

---


# Mobile app acquisition {#mobile-app-acquisition}

Verwervingskoppelingen met unieke volgcodes kunnen worden gegenereerd in Adobe Mobile-services. Wanneer een gebruiker een app downloadt en uitvoert vanuit de App Store nadat hij op de gegenereerde koppeling heeft geklikt, verzamelt de SDK automatisch de overnamegegevens en stuurt deze naar Adobe Mobile-services.

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar Adobe Experience Platform Launch om aan de slag te gaan.
* Ga naar [Github om te zien wat er in de SDK-opslagruimten van het Experience Platform staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
>Als u Acquisition wilt gebruiken, **moet** u SDK versie 4.1 of hoger hebben.

Verwervingsverbindingen moeten in de Mobiele diensten van Adobe worden gecreeerd. Zie [Overname](/help/using/acquisition-main/acquisition-main.md)voor meer informatie.

**In SDK-versies 4.18.0 en hoger**:

Vanaf 1 maart 2020 wordt het uitzendmechanisme van de install_reference intent door Google vervangen. Voor meer informatie, zie [nog het Gebruiken van InstallBroadcast? Schakel tegen 1 maart 2020 over naar de Play Reference API](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html). Als u informatie over de installatieverwijzing wilt blijven verzamelen in de Google Play-winkel, moet u uw toepassing bijwerken naar SDK versie 4.18.0 of hoger.

Met de afgekeurde toepassing moet u in plaats van een `BroadcastReceiver`installatieverwijzing de URL van de installatieverwijzing verzamelen via een nieuwe Google API en de resulterende URL doorgeven aan de SDK.

1. Voeg het Google Play-pakket met installatieverwijzing toe aan de afhankelijkheden van het onbewerkte bestand:

   `implementation 'com.android.installreferrer:installreferrer:1.1'`

1. Als u de URL van de referentie wilt ophalen van de installatiereferor-API, voert u de stappen uit om de [installatiereferator](https://developer.android.com/google/play/installreferrer/library#install-referrer)op te halen.

1. Geef de referentie-URL door aan de SDK:

   `Analytics.processGooglePlayInstallReferrerUrl(referrerUrl);`

>[!IMPORTANT]
>
>Om onnodige API-aanroepen in uw app te voorkomen, raadt Google u aan de API slechts één keer onmiddellijk na de installatie aan te roepen.

Raadpleeg de documentatie van Google voor informatie over de beste manier om de Google Play-API&#39;s van de installatieverwijzing in uw app te gebruiken. Hier ziet u een voorbeeld van het gebruik van de SDK van Adobe met de Google Play-API&#39;s voor installatiebestanden:

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

Als u de verwervingskoppelingen niet kunt gebruiken die zijn gemaakt in Adobe Mobile Services, kunnen de overnamegegevens nog steeds worden verzameld en verzonden door de SDK met behulp van Google Play Acquisition.

Verzamel verzamelgegevens van een standaard Google Play-acquisitiecampagne:

* Gebruik de standaardmethode voor het aanschaffen van Google Play Store.

   Aangepaste verwervingsgegevens kunnen worden gebruikt met de standaard waardeparen van de overnamesleutel van Google Play.

* Wanneer de gebruiker een app downloadt en uitvoert als gevolg van een Google Play Store-aankoop, worden de gegevens van de referentie verzameld en naar Adobe Mobile Services verzonden.

   * De gegevens worden opgeslagen en beschikbaar in de `AdobeDataCallback` instantie die eerder bij de SDK is geregistreerd.

      Voor meer informatie, zie de Methoden [van de](/help/android/configuration/methods.md)Configuratie.

   * Het `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` gebeurtenistype of het `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` gebeurtenistype wordt gebruikt.

   * Aangepaste sleutels die deel uitmaakten van de aanschafgegevens van Google Play, krijgen een naamruimte met &quot; `a.acquisition.custom.`&quot;

Als u de Verbindingsverbindingen gebruikt die op de Mobiele Diensten van Adobe werden gecreeerd, voeg douanegegevens aan de verwervingsverbinding toe door de volgende taken te voltooien:

1. Voorvoegsel een verwervingsvariabele met &quot; `adb`&quot;.

   Wanneer de SDK de aanschafgegevens van Adobe Mobile Services ontvangt bij de eerste keer dat deze wordt gestart, worden de gegevens opgeslagen en zijn deze beschikbaar in de `AdobeDataCallback` instantie die eerder bij de SDK is geregistreerd. Voor meer informatie, zie de Methoden [van de](/help/android/configuration/methods.md)Configuratie.

1. Het `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` gebeurtenistype of het `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` gebeurtenistype wordt gebruikt.

1. De aangepaste gegevenssleutels hebben de voorvoegsel &quot;`a.acquisition.custom.`&quot;

>[!TIP]
>
>Als u gegevens naar meerdere rapportenreeksen verzendt, gebruikt u de aankoopgegevens van de app die is gekoppeld aan de eerste rapportsuite in uw lijst met id&#39;s van rapportsuite.

Met de updates in deze sectie kan de SDK acquisitiegegevens verzenden via een acquisitie-koppeling.

## Mobiele acquisitie volgen {#section_CEA30C652AC8470784B8054E299B80FA}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Voor meer informatie, zie *Voeg het Dossier SDK en Config aan uw IDEA IntelliJ of Project* Eclipse in de implementatie en de levenscyclus [van de](/help/android/getting-started/dev-qs.md)Kern toe.

1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. Voer het `BroadcastReceiver` voor de verwijzende uit:

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

1. Update `AndroidManifest.xml` om het `BroadcastReceiver` bestand in te schakelen dat in de vorige stap is gemaakt:

   ```xml
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
    <intent-filter>
     <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
   </receiver>
   ```

1. Controleer of het `ADBMobileConfig.json` bestand de vereiste acquisitie-instellingen bevat:

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

   De `acquisition` instellingen worden gegenereerd door Adobe Mobile-services en mogen niet worden gewijzigd. Voor meer informatie over hoe te om een aangepast `ADBMobileConfig.json` dossier met de vooraf gevormde montages te downloaden, zie `acquisition` alvorens u begint [](/help/android/getting-started/requirements.md).

Nadat deze instellingen zijn ingeschakeld, worden aanschafgegevens na de eerste keer dat de app wordt gestart automatisch verzonden met de eerste levenscyclusaanroep.

>[!CAUTION]
>
>`referrerTimeout` moet een waarde hoger dan 0 zijn om het aanschaffen van apps mogelijk te maken.
