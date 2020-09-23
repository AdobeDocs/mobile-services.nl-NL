---
description: Dit onderwerp verstrekt informatie over hoe te om kwesties problemen op te lossen u tijdens het testen van de Opname zou kunnen worden geconfronteerd.
keywords: android;library;mobile;sdk
seo-description: Dit onderwerp verstrekt informatie over hoe te om kwesties problemen op te lossen u tijdens het testen van de Opname zou kunnen worden geconfronteerd.
seo-title: Problemen met ophalen oplossen
solution: Experience Cloud,Analytics
title: Problemen met ophalen oplossen
topic: Developer and implementation
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---


# Problemen met ophalen oplossen {#troubleshoot-acquisition-testing}

Dit onderwerp verstrekt informatie over hoe te om kwesties problemen op te lossen u tijdens het testen van de Opname zou kunnen worden geconfronteerd.

* Tenzij anders aangegeven, moet het bestand ADBMobileConfig.json in de `assets` map worden geplaatst.

   De naam is hoofdlettergevoelig, dus gebruik geen hoofdletters of kleine letters.

* Zorg ervoor dat dit vanuit uw hoofdactiviteit `Config.setContext(this.getApplicationContext())` wordt aangeroepen.

   Voor meer informatie, zie de methodes [van de](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)Configuratie.

* Controleer of de vereiste machtigingen voor de mobiele SDK aanwezig zijn in het `AndroidManifest.xml` bestand:

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Als het bestand ADMobileConfig.json op 5 `referrerTimeout` is ingesteld, moet u de installatieintentie na de installatie en de introductie van de toepassing binnen een tijdsbestek van 5 seconden voor het eerst verzenden om te zien hoe de informatie over de referentie bij de installatietaak wordt gevoegd.

   Voor handmatige tests raden we u aan de waarde `referrerTimeout` tot 10-15 seconden te verhogen, zodat u voldoende tijd hebt om de informatie van de referentie te verzenden voordat de installatietaak wordt verwerkt.

* Voer alle stappen in het [Testen van de Aankoop](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) van de Verbinding van de Marketing uit en zorg ervoor dat u het `adb shell` bevel eerst en dan het volgende uitvoert:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Als u de verwijzende intent correct wilt verwerken, moet u deze twee opdrachten onafhankelijk uitvoeren. Anders `adb` zal de verwijzende informatie tweemaal ontsnappen en de gegevens die door de uitzendingsontvanger worden ontvangen zullen onvolledig zijn.

