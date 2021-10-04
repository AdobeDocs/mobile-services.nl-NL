---
description: Met de volgende informatie kunt u problemen met het testen van overnames oplossen.
keywords: android;Acquisitie;testen
solution: Experience Cloud,Analytics
title: Problemen met ophalen testen
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---


# Problemen met ophalen testen {#aquistion-testing-troubleshooting}

Hier volgen enkele problemen die u kunt tegenkomen bij het testen van overname en enkele mogelijke oplossingen:

* Tenzij anders aangegeven, moet het bestand ADBMobileConfig.json in de map assets worden geplaatst.

* De naam is hoofdlettergevoelig, dus geef geen naam op in kleine letters.

   U moet ervoor zorgen dat `Config.setContext(this.getApplicationContext())` van de belangrijkste activiteit wordt geroepen. Zie [Configuratiemethoden](../configuration/methods.md) voor meer informatie.

* Er ontbreken enkele gebruikersmachtigingen in het opgegeven bestand AndroidManifest.xml. Deze machtigingen zijn vereist voor het verzenden van gegevens en het vastleggen van offline opvolgende aanroepen:

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Als in uw configuratie de time-out voor de referentie is ingesteld op `referrerTimeout: 5`, betekent dit dat u de installatieintentie na de installatie en de eerste keer moet verzenden om de informatie voor de referentie bij de installatietaak te zien.

   Verhoog voor handmatige tests de `referrerTimeout` tot 10-15 seconden, zodat er voldoende tijd is om de informatie van de referentie te verzenden voordat de installatietaak wordt verwerkt.

* Het is belangrijk om alle stappen in [Testing Marketing Link acquisitie](t-t-testing-marketing-link-acquisition.md) in werking te stellen en ervoor te zorgen u `adb` shell en dan het volgende uitvoert:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>U moet deze twee opdrachten afzonderlijk uitvoeren om de verwijzende intent correct te verwerken.  Anders, `adb` dubbel ontsnapt aan de verwijzingsinformatie, en de gegevens die door de uitzendingsontvanger worden ontvangen zullen onvolledig zijn.
