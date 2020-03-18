---
description: Met deze informatie kunt u een koppeling naar de aanschafcampagne versie 3 op een Android-apparaat gebruiken om een campagne voor het aanschaffen van een versie 3 uit te voeren.
keywords: android;library;mobile;sdk
seo-description: Met deze informatie kunt u een koppeling naar de aanschafcampagne versie 3 op een Android-apparaat gebruiken om een campagne voor het aanschaffen van een versie 3 uit te voeren.
seo-title: Testversie 3-overname
solution: Marketing Cloud,Analytics
title: Testversie 3-overname
topic: Developer and implementation
uuid: 5e38b43d-389e-4412-99e5-3e6223b6ad28
translation-type: tm+mt
source-git-commit: 657e8b93d1516690ad21d6cf504f9c8f611747b6

---


# V3-overname testen {#testing-version-acquisition}

Met deze informatie kunt u een koppeling naar de aanschafcampagne versie 3 op een Android-apparaat gebruiken om een campagne voor het aanschaffen van een versie 3 uit te voeren.

>[!IMPORTANT]
>
>Verwerving in V3 verwijst naar de aanschafkoppelingen die u maakt met de Verwervingsbouwer in de gebruikersinterface van Adobe Mobile Services. Als u deze functie wilt gebruiken, moet u een upgrade uitvoeren naar Android SDK 4.x voor Experience Cloud Solutions 4.6.0 of hoger.

Als de mobiele app zich nog niet in Google Play bevindt, kunt u bij het maken van de koppeling naar de campagne elke mobiele app als doel selecteren. Dit is alleen van invloed op de app waarnaar de verwervingsserver u omleidt nadat u op de verwervingskoppeling hebt geklikt, maar heeft geen invloed op de mogelijkheid om de koppeling te testen. Parameters van de queryreeks worden doorgegeven aan de Google Play-winkel, die tijdens de installatie worden doorgegeven aan de app als onderdeel van een campagne-uitzending. Voor het testen van het aanschaffen van mobiele apps voor Roundtrip is de simulatie van dit type uitzending vereist.

>[!IMPORTANT]
>
>Als u implementeert met de Google Play-API&#39;s van de Google Play-installatieverwijzing, kunt u acquisitie niet testen voordat uw app zich in de Google Play-winkel bevindt.

Telkens wanneer een test wordt uitgevoerd, moet de app opnieuw zijn geïnstalleerd of moeten gegevens worden gewist **[!UICONTROL Settings]**. Dit zorgt ervoor dat de aanvankelijke levenscyclusmetriek die met de de koordparameters van de campagnerequery wordt geassocieerd worden verzonden wanneer app voor het eerst wordt gelanceerd.

1. Voltooi de vereiste taken in [Mobiele App Aankoop](/help/android/acquisition-main/acquisition.md) en zorg ervoor dat u de uitzendingsontvanger voor correct hebt uitgevoerd `INSTALL_REFERRER`.

1. Klik in de gebruikersinterface van Adobe Mobile Services op **[!UICONTROL Acquisition]** > **[!UICONTROL Marketing Links Builder]** en genereer een URL voor een Acquisition Marketing Link die Google Play instelt als de bestemming voor Android-apparaten.

   Zie [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)voor meer informatie.

   Bijvoorbeeld, `https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=g&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode`.

   >[!TIP]
   >
   >Als u zowel Android- als iOS-apps in de acquisitie-koppeling gebruikt, gebruikt u Google Play als de standaardwinkel.

1. Open de gegenereerde koppeling in een desktopbrowser.

   U moet worden omgeleid naar een pagina met een URL die lijkt op het volgende voorbeeld:
   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Kopieer de unieke id na `utm_content%3D`.

   In het vorige voorbeeld is de id `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

1. Construeer de verbinding van het verwervingseind door unieke identiteitskaart van stap 3 te gebruiken door het volgende formaat te gebruiken:

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`.

   Bijvoorbeeld, `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

1. Open de koppeling in een desktopbrowser.

   U moet de reacties `contextData` van JSON zien:

   `{"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.`

   Als u niet ziet `contextData`of een gedeelte van de tekenreeks ontbreekt, moet u ervoor zorgen dat de aankoop-URL de indeling in [Verwervingskoppeling handmatig](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md)maken volgt.
1. Herhaal stap 3 voor een nieuwe unieke id.
1. Controleer of de volgende instellingen in het configuratiebestand correct zijn:

   | Instelling | Waarde |
   |--- |--- |
   | verwerving | De server moet `c00.adobe.com`zijn.   *`appid`*  moet gelijk zijn aan de `appid` in uw acquisitie-koppeling. |
   | analyse | Voor testdoeleinden stelt u de time-out van de referentie zo in dat er voldoende tijd (60 seconden of meer) is om de uitzending handmatig te verzenden. U kunt de oorspronkelijke time-outinstelling na de test herstellen. |

1. Sluit het apparaat aan op een computer, verwijder en installeer de toepassing opnieuw.
1. Start ADB Shell en start de toepassing op het apparaat.
1. Verzend een uitzending door het volgende `adb` bevel te gebruiken:

   `am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"`

1. Voer de volgende stappen uit:
   1. Vervangen `com.adobe.android` door de pakketnaam van de toepassing.
   1. Verwijzing naar ontvanger bijwerken met de locatie van de ontvanger voor het bijhouden van de campagne in uw app
   1. Waarden vervangen die zijn gekoppeld aan `utm_content`.
   Als de uitzending slaagt, kunt u een reactie verwachten gelijkend op het volgende voorbeeld:

   `Broadcasting: Intent
{ act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) }
Broadcast completed: result=0`

1. (Optioneel) U kunt foutopsporingslogboekregistratie van de SDK inschakelen voor aanvullende informatie.

   Als alles correct werkt, zou u volgende logboeken moeten zien:

`"Analytics - Received referrer information(<referrer content>)"   "Analytics - Trying to fetch referrer data from (acquisition end url)"; "Analytics - Received Referrer Data(<A JSON Response>)"`

Als de bovenstaande logboeken niet worden weergegeven, controleert u of u de stappen 6 tot en met 12 hebt uitgevoerd.

De volgende tabel bevat aanvullende informatie over de mogelijke fouten:

| Fout | Beschrijving |
|--- |--- |
| Analytics - Unable to decode response(*String*). | De reactie is onjuist geformuleerd. |
| Analytics - Unable to parse response (*a JSON Response*). | De JSON-tekenreeks is onjuist geformuleerd. |
| Analytics - Unable to parse purchase service response (no contextData parameter in response). | Er is geen contextData parameter in de reactie. |
| Analytics - Acquisition reference data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name`  is niet opgenomen in contextData. |
| Analytics - Acquisition reference time out. | Kan de reactie niet ophalen in de tijd gedefinieerd door `referrerTimeout`. Verhoog de waarde en probeer het opnieuw.  Zorg er ook voor dat u de acquisitie-koppeling hebt geopend voordat u de app installeert. |

De volgende informatie onthouden:

* De berichten die vanuit de app worden verzonden, kunnen worden gecontroleerd met de HTTP-controlehulpmiddelen om de acquisitie-toewijzing te verifiëren.
* Zie Meting van Google Play-campagne `INSTALL_REFERRER`testen in de handleiding voor Google-ontwikkelaars voor meer informatie over het uitzenden [van](https://developers.google.com/analytics/solutions/testing-play-campaigns) programma&#39;s.

* Op Android 4.8.2 is een bug fix uitgebracht voor overname.

   Upgrade de SDK naar de meest recente versie voordat u gaat testen.

* U kunt het meegeleverde gereedschap `acquisitionTest.jar` Java gebruiken om u te helpen de unieke id en installatiefunctionaris voor uitzendingen te verkrijgen. Deze referentie helpt u bij het ophalen van de informatie in de stappen 3 tot en met 12.

   **Het gereedschap Java installeren**

Java installeren:

1. Download het [`acquisitionTester.zip`](/help/android/assets/acquisitionTester.zip) bestand.

1. Extraheer het .jar-bestand.

   U kunt het bestand op de opdrachtregel uitvoeren.

   Bijvoorbeeld:

   ```java
   java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
   ```