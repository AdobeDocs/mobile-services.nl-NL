---
description: Dit onderwerp verstrekt informatie over hoe te om kwesties problemen op te lossen u tijdens het testen van de Opname zou kunnen worden geconfronteerd.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Problemen met ophalen oplossen
topic-fix: Developer and implementation
exl-id: 1ed2ad89-4e89-43da-aa21-f688b4d1c0d1
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# Problemen met ophalen oplossen {#troubleshoot-acquisition-testing}

Dit onderwerp verstrekt informatie over hoe te om kwesties problemen op te lossen u tijdens het testen van de Opname zou kunnen worden geconfronteerd.

* Indien niet anders opgegeven, moet het bestand ADBMobileConfig.json in het `assets` map.

   De naam is hoofdlettergevoelig, dus gebruik geen hoofdletters of kleine letters.

* Zorg ervoor dat `Config.setContext(this.getApplicationContext())` wordt aangeroepen vanuit uw hoofdactiviteit.

   Zie voor meer informatie [Configuratiemethoden](../configuration/methods.md).

* Zorg ervoor dat de vereiste machtigingen voor de Mobile SDK aanwezig zijn in het dialoogvenster `AndroidManifest.xml` bestand:

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Als de `referrerTimeout` is ingesteld op 5 in het bestand ADMobileConfig.json, moet u de installatieintentie binnen 5 seconden nadat de toepassing is geïnstalleerd en voor de eerste keer gestart verzenden om de referentie-informatie bij de installatietaak te zien.

   Voor handmatige tests raden we u aan de `referrerTimeout` tot 10-15 seconden, zodat u voldoende tijd hebt om de verwijzende informatie te verzenden alvorens de installatiereshit wordt verwerkt.

* Voer alle stappen uit in [Verwerving marketinglink testen](t-testing-marketing-link-acquisition.md) en zorg ervoor dat u de `adb shell` eerst en daarna het volgende gebruiken:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Als u de verwijzende intent correct wilt verwerken, moet u deze twee opdrachten onafhankelijk uitvoeren. Anders `adb` de referentie-informatie wordt dubbel verwijderd en de door de ontvanger ontvangen gegevens zijn onvolledig.
