---
description: Dit onderwerp verstrekt informatie over hoe te om kwesties problemen op te lossen u tijdens het testen van de Opname zou kunnen worden geconfronteerd.
keywords: android;bibliotheek;mobile;sdk
seo-description: Dit onderwerp verstrekt informatie over hoe te om kwesties problemen op te lossen u tijdens het testen van de Opname zou kunnen worden geconfronteerd.
seo-title: Problemen met ophalen oplossen
solution: Experience Cloud,Analytics
title: Problemen met ophalen oplossen
topic-fix: Developer and implementation
exl-id: 1ed2ad89-4e89-43da-aa21-f688b4d1c0d1
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Problemen met ophalen oplossen {#troubleshoot-acquisition-testing}

Dit onderwerp verstrekt informatie over hoe te om kwesties problemen op te lossen u tijdens het testen van de Opname zou kunnen worden geconfronteerd.

* Tenzij anders vermeld, zou het dossier ADBMobileConfig.json in `assets` omslag moeten worden geplaatst.

   De naam is hoofdlettergevoelig, dus gebruik geen hoofdletters of kleine letters.

* Zorg ervoor dat `Config.setContext(this.getApplicationContext())` van uw hoofdactiviteit wordt geroepen.

   Zie [Configuratiemethoden](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html) voor meer informatie.

* Controleer of de vereiste machtigingen voor de mobiele SDK aanwezig zijn in het `AndroidManifest.xml`-bestand:

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Als `referrerTimeout` in het ADMobileConfig.json- dossier aan 5 wordt geplaatst, moet u de installatieintent binnen 5 seconden na de toepassing verzenden en voor het eerst beginnen om de verwijzingsinformatie te zien toevoegde aan de installatiereactie.

   Voor handmatige tests raden we u aan de `referrerTimeout` te verhogen naar 10-15 seconden, zodat u voldoende tijd hebt om de informatie van de referentie te verzenden voordat de hit bij de installatie wordt verwerkt.

* Voer alle stappen in [Het Testen van de Aankoop van de Verbinding van de Marketing](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) in en zorg ervoor dat u `adb shell` bevel eerst en dan het volgende uitvoert:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Als u de verwijzende intent correct wilt verwerken, moet u deze twee opdrachten onafhankelijk uitvoeren. Anders zal `adb` dubbel ontsnappen aan de verwijzende informatie en de gegevens die door de uitzendingsontvanger worden ontvangen zullen onvolledig zijn.
