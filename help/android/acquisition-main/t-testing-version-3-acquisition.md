---
description: Met deze informatie kunt u een koppeling naar de aanschafcampagne versie 3 op een Android-apparaat gebruiken om een campagne voor het aanschaffen van een versie 3 uit te voeren.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Testversie 3-overname
topic-fix: Developer and implementation
uuid: 5e38b43d-389e-4412-99e5-3e6223b6ad28
exl-id: 2ce78e2e-da51-4af8-a461-ec6c642a7854
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 1%

---

# V3-overname testen {#testing-version-acquisition}

Met deze informatie kunt u een koppeling naar de aanschafcampagne versie 3 op een Android-apparaat gebruiken om een campagne voor het aanschaffen van een versie 3 uit te voeren.

>[!IMPORTANT]
>
>Verwerving in V3 verwijst naar de verwervingsverbindingen die u met de Bouwer van de Verwerving in de Adobe Mobile Services UI creeert. Als u deze functie wilt gebruiken, moet u een upgrade uitvoeren naar Android SDK 4.x voor Experience Cloud Solutions 4.6.0 of hoger.

Als de mobiele app zich nog niet in Google Play bevindt, kunt u bij het maken van de koppeling naar de campagne elke mobiele app als bestemming selecteren. Dit is alleen van invloed op de app waarnaar de verwervingsserver u omleidt nadat u op de verwervingskoppeling hebt geklikt, maar heeft geen invloed op de mogelijkheid om de koppeling te testen. Parameters van de queryreeks worden doorgegeven aan de Google Play-winkel. Deze worden tijdens de installatie doorgegeven aan de app als onderdeel van een campagneuitzending. Voor het testen van het aanschaffen van mobiele apps voor Roundtrip is de simulatie van dit type uitzending vereist.

>[!IMPORTANT]
>
>Als u implementeert met de Google Play Install Referrer-API&#39;s, kunt u acquisitie niet testen voordat uw app zich in de Google Play Store bevindt.

De app moet nieuw zijn geïnstalleerd of gegevens moeten zijn gewist **[!UICONTROL Settings]**, elke keer dat een test wordt uitgevoerd. Dit zorgt ervoor dat de aanvankelijke levenscyclusmetriek die met de de koordparameters van de campagnerequery wordt geassocieerd worden verzonden wanneer app voor het eerst wordt gelanceerd.

1. Voltooi de vereiste taken in [Mobile App Acquisition](/help/android/acquisition-main/acquisition.md) en zorg ervoor dat u de broadcastontvanger correct hebt geïmplementeerd voor `INSTALL_REFERRER`.

1. Klik in de gebruikersinterface van Adobe Mobile Services op  **[!UICONTROL Acquisition]** > **[!UICONTROL Marketing Links Builder]** en genereer een Acquisition Marketing Link URL die Google Play instelt als het doel voor Android-apparaten.

   Zie voor meer informatie [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).

   Bijvoorbeeld, `https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=g&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode`.

   >[!TIP]
   >
   >Als u zowel Android- als iOS-toepassingen in de aankoopkoppeling wilt raadplegen, gebruikt u Google Play als de standaardwinkel.

1. Open de gegenereerde koppeling in een desktopbrowser.

   U moet worden omgeleid naar een pagina met een URL die lijkt op het volgende voorbeeld:
   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. De unieke id kopiëren na `utm_content%3D`.

   In het vorige voorbeeld is de id `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

1. Construeer de verbinding van het verwervingseind door unieke identiteitskaart van stap 3 te gebruiken door het volgende formaat te gebruiken:

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`.

   Bijvoorbeeld, `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

1. Open de koppeling in een desktopbrowser.

   Je moet de `contextData` in het JSON-antwoord:

   `{"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.`

   Als u niet ziet `contextData`, of een deel van de tekenreeks ontbreekt, zorgt u ervoor dat de aankoop-URL de indeling in [Koppeling voor overname handmatig maken](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md).
1. Herhaal stap 3 voor een nieuwe unieke id.
1. Controleer of de volgende instellingen in het configuratiebestand correct zijn:

   | Instelling | Waarde |
   |--- |--- |
   | verwerving | De server moet `c00.adobe.com`.   *`appid`*  moet gelijk zijn aan `appid`  in uw acquisitie link. |
   | analyse | Voor testdoeleinden stelt u de time-out van de referentie zo in dat er voldoende tijd (60 seconden of meer) is om de uitzending handmatig te verzenden. U kunt de oorspronkelijke time-outinstelling na de test herstellen. |

1. Sluit het apparaat aan op een computer, verwijder en installeer de toepassing opnieuw.
1. Start ADB Shell en start de toepassing op het apparaat.
1. Verzend uitzending met behulp van het volgende `adb` opdracht:

   `am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"`

1. Voer de volgende stappen uit:
   1. Vervangen `com.adobe.android` met de pakketnaam van uw toepassing.
   1. Verwijzing naar ontvanger bijwerken met de locatie van de ontvanger voor het bijhouden van de campagne in uw app
   1. Waarden vervangen die zijn gekoppeld aan `utm_content`.

   Als de uitzending slaagt, kunt u een reactie verwachten gelijkend op het volgende voorbeeld:

   ```
   Broadcasting: Intent
   { act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) }
   Broadcast completed: result=0
   ```

1. (Optioneel) U kunt foutopsporingslogboekregistratie van de SDK inschakelen voor aanvullende informatie.

   Als alles correct werkt, zou u volgende logboeken moeten zien:

`"Analytics - Received referrer information(<referrer content>)"   "Analytics - Trying to fetch referrer data from (acquisition end url)"; "Analytics - Received Referrer Data(<A JSON Response>)"`

Als de bovenstaande logboeken niet worden weergegeven, controleert u of u de stappen 6 tot en met 12 hebt uitgevoerd.

De volgende tabel bevat aanvullende informatie over de mogelijke fouten:

| Fout | Beschrijving |
|--- |--- |
| Analytics - Unable to decode response(*String*). | De reactie is onjuist geformuleerd. |
| Analytics - Unable to parse response (*een JSON-reactie*). | De JSON-tekenreeks is onjuist geformuleerd. |
| Analytics - Unable to parse purchase service response (no contextData parameter in response). | Er is geen contextData parameter in de reactie. |
| Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in contextgegevens), negeren. | `a.referrer.campaign.name`  is niet opgenomen in contextData. |
| Analytics - Acquisition reference time out. | Kan de reactie niet ophalen in de tijd gedefinieerd door `referrerTimeout`. Verhoog de waarde en probeer het opnieuw.  Zorg er ook voor dat u de acquisitie-koppeling hebt geopend voordat u de app installeert. |

De volgende informatie onthouden:

* De berichten die vanuit de app worden verzonden, kunnen worden gecontroleerd met de HTTP-controlehulpmiddelen om de acquisitie-toewijzing te verifiëren.
* Voor meer informatie over hoe te om uit te zenden `INSTALL_REFERRER`, zie [Meting van Google Play-campagne testen](https://developers.google.com/analytics/solutions/testing-play-campaigns) in de handleiding voor Google-ontwikkelaars.

* Op Android 4.8.2 is een bug fix uitgebracht voor overname.

   Upgrade de SDK naar de meest recente versie voordat u gaat testen.

* U kunt de meegeleverde `acquisitionTest.jar` Het hulpmiddel van Java om u te helpen de unieke identiteitskaart krijgen en uitzendingsreferentie, die beurtelings, u de informatie in stap 3 tot 12 helpt verkrijgen.

   **Het gereedschap Java installeren**

Java installeren:

1. Download de [`acquisitionTester.zip`](/help/android/assets/acquisitionTester.zip) bestand.

1. Extraheer het .jar-bestand.

   U kunt het bestand op de opdrachtregel uitvoeren.

   Bijvoorbeeld:

   ```java
   java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
   ```
