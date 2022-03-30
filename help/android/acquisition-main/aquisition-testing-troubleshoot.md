---
description: Met de volgende informatie kunt u problemen met het testen van overnames oplossen.
keywords: android;Acquisitie;testen
solution: Experience Cloud Services,Analytics
title: Problemen met ophalen testen
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---


# Problemen met ophalen testen {#aquistion-testing-troubleshooting}

Hier volgen enkele problemen die u kunt tegenkomen bij het testen van overname en enkele mogelijke oplossingen:

* Tenzij anders aangegeven, moet het bestand ADBMobileConfig.json in de map assets worden geplaatst.

* De naam is hoofdlettergevoelig, dus geef geen naam op in kleine letters.

   U moet ervoor zorgen dat `Config.setContext(this.getApplicationContext())` wordt aangeroepen vanuit de hoofdactiviteit. Zie voor meer informatie [Configuratiemethoden](../configuration/methods.md).

* Er ontbreken enkele gebruikersmachtigingen in het opgegeven bestand AndroidManifest.xml. Deze machtigingen zijn vereist voor het verzenden van gegevens en het vastleggen van offline opvolgende aanroepen:

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Als de time-out van de verwijzer in uw configuratie is ingesteld op `referrerTimeout: 5`Dit betekent dat u de installatieintentie na de installatie en de eerste keer moet verzenden binnen een periode van 5 seconden om te zien hoe de informatie over de referentie bij de installatietaak wordt gevoegd.

   Verhoog voor handmatige tests de `referrerTimeout` tot 10-15 seconden, zodat er genoeg tijd is om de verwijzende informatie te verzenden alvorens de installatierondst wordt verwerkt.

* Het is belangrijk alle stappen uit te voeren in [Verwerving marketinglink testen](t-t-testing-marketing-link-acquisition.md) in volgorde en zorg ervoor dat u uitvoert `adb` shell en dan het volgende:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>U moet deze twee opdrachten afzonderlijk uitvoeren om de verwijzende intent correct te verwerken.  Anders, `adb` dubbel ontsnapt aan de verwijzende informatie, en de gegevens die door de uitzendingsontvanger worden ontvangen zullen onvolledig zijn.
