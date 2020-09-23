---
description: Met de volgende informatie kunt u problemen met het testen van overnames oplossen.
keywords: android;Acquisition;testing
seo-description: Met de volgende informatie kunt u problemen met het testen van overnames oplossen.
seo-title: Problemen met ophalen testen
solution: Experience Cloud,Analytics
title: Problemen met ophalen testen
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---


# Problemen met ophalen testen {#aquistion-testing-troubleshooting}

Hier volgen enkele problemen die u kunt tegenkomen bij het testen van overname en enkele mogelijke oplossingen:

* Tenzij anders aangegeven, moet het bestand ADBMobileConfig.json in de map assets worden geplaatst.

* De naam is hoofdlettergevoelig, dus geef geen naam op in kleine letters.

   U moet ervoor zorgen dat dit van de belangrijkste activiteit `Config.setContext(this.getApplicationContext())` wordt geroepen. Voor meer informatie, zie de methodes [van de](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)Configuratie.

* Er ontbreken enkele gebruikersmachtigingen in het opgegeven bestand AndroidManifest.xml. Deze machtigingen zijn vereist voor het verzenden van gegevens en het vastleggen van offline opvolgende aanroepen:

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Als in uw configuratie de time-out van de referentie is ingesteld `referrerTimeout: 5`, betekent dit dat u de installatieintentie binnen een periode van 5 seconden na de installatie van de toepassing voor de eerste keer moet verzenden om de referentie-informatie bij de installatietaak te zien.

   Verhoog de waarde `referrerTimeout` tot 10-15 seconden voor handmatige tests, zodat er voldoende tijd is om de informatie over de referenties te verzenden voordat de installatietaak wordt verwerkt.

* Het is belangrijk om alle stappen in het [Testen van de Aankoop](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) van de Verbinding van de Marketing in werking te stellen en ervoor te zorgen u shell `adb` en dan het volgende uitvoert:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>U moet deze twee opdrachten afzonderlijk uitvoeren om de verwijzende intent correct te verwerken.  Anders, `adb` dubbel ontsnapt aan de verwijzingsinformatie, en de gegevens die door de uitzendingsontvanger worden ontvangen zullen onvolledig zijn.
