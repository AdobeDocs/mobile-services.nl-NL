---
description: De volgende instructies helpen u een acquisitiecampagne met een Marketing Link op een Android-apparaat te roundtrip.
keywords: android;library;mobile;sdk
seo-description: De volgende instructies helpen u een acquisitiecampagne met een Marketing Link op een Android-apparaat te roundtrip.
seo-title: Verwerving marketingkoppeling testen
solution: Experience Cloud,Analytics
title: Verwerving marketingkoppeling testen
topic: Developer and implementation
uuid: d0933dcc-8fc3-4f60-987f-7a54559aacf5
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 1%

---


# Verwerving marketinglink testen {#testing-marketing-link-acquisition}

De volgende instructies helpen u een acquisitiecampagne met een Marketing Link op een Android-apparaat te roundtrip.

Als uw mobiele app nog niet in Google Play is, kunt u elke mobiele app als doel selecteren wanneer u de marketingkoppeling maakt. Dit is alleen van invloed op de app waarnaar de verwervingsserver u omleidt, nadat u op de verwervingskoppeling klikt en niet op de mogelijkheid om de verwervingskoppeling te testen. Parameters van de queryreeks worden doorgegeven aan de Google Play-winkel, die tijdens de installatie worden doorgegeven aan de app als onderdeel van een campagne-uitzending. Voor het testen van het aanschaffen van mobiele apps voor Roundtrip is de simulatie van dit type uitzending vereist.

Telkens wanneer een test wordt uitgevoerd, moet de app opnieuw zijn geïnstalleerd of moeten gegevens worden gewist **[!UICONTROL Settings]**. Dit zorgt ervoor dat de aanvankelijke levenscyclusmetriek die met de de koordparameters van de campagnerequery wordt geassocieerd worden verzonden wanneer app voor het eerst wordt gelanceerd.

1. Voltooi de vereiste taken bij de aanschaf [van de](/help/android/acquisition-main/acquisition.md) mobiele app en zorg ervoor dat u de ontvanger voor de uitzending correct hebt geïmplementeerd `INSTALL_REFERRER`.
1. Klik in de gebruikersinterface van Adobe Mobile Services op **[!UICONTROL Acquisition]** > **[!UICONTROL Marketing Links Builder]** en genereer een URL voor een Acquisition Marketing Link die Google Play instelt als de bestemming voor Android-apparaten.

   Zie [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)voor meer informatie.

   Bijvoorbeeld:

   `https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. Open de gegenereerde koppeling op het Android-apparaat.

   U moet worden omgeleid naar een pagina met een URL die lijkt op het volgende voorbeeld:

   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Kopieer de unieke id na `utm_content%3D`.

   In het vorige voorbeeld is de id `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

   Als u de unieke id niet kunt ophalen op het apparaat, voert u de volgende `CURL` opdracht uit op uw bureaublad om de unieke id op te halen uit de responstekenreeks.

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" <Your Marketing Link>`

   Bijvoorbeeld:

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. Construeer de verbinding van het verwervingseind door unieke identiteitskaart van stap 3 te gebruiken, door het volgende formaat te gebruiken:

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`

   Bijvoorbeeld: `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Open de koppeling in een browser.

   U moet de reacties `contextData` van JSON zien:

   ```
   {"fingerprint":"44b2f88a062df7e727c047f006deb9971304617b","endCallbacks":["***"],"timestamp":1464301282,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData": 
   {"a.launch.campaign.trackingcode":"trymttvm","a.referrer.campaign.name":"Android Demo","a.referrer.campaign.trackingcode":"trymttvm"} 
   ,"adobeData":{"unique_id":"9a2be52764a8db125c29a8c10f3b1b3d5d8ed915","deeplinkid":"57476c26072932ec6d3a470b"}}.
   ```

1. Herhaal stap 3 voor een nieuwe unieke id.
1. Controleer of de volgende instellingen in het configuratiebestand correct zijn:

   | Instelling | Waarde |
   |--- |--- |
   | verwerving | De server moet gelijk zijn aan `c00.adobe.com`de *`appid`* `appid` verwervingskoppeling. |
   | analyse | Voor testdoeleinden stelt u de time-out van de referentie zo in dat er voldoende tijd (60 seconden of meer) is om de uitzending handmatig te verzenden. U kunt de oorspronkelijke time-outinstelling na de test herstellen. |

1. Sluit het apparaat aan op een computer, verwijder en installeer de toepassing opnieuw.
1. Start ADB Shell en start de toepassing op het apparaat.

   ```
   adb shell
   ```

1. Verzend een uitzending door het volgende `adb` bevel te gebruiken:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"
   ```

1. Vervang `com.adobe.android` de pakketnaam van uw toepassing, werk de verwijzing naar de ontvanger bij met de verwijzing naar de locatie van de ontvanger voor het bijhouden van de campagne in uw app en vervang de waarden die aan de ontvanger zijn gekoppeld `utm_content`.

   Als de uitzending succesvol is, zou u een reactie als het volgende voorbeeld moeten verwachten:

   ```
   Broadcasting: Intent 
   { act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) } 
   Broadcast completed: result=0 
   ```

1. (Optioneel) U kunt foutopsporingslogboekregistratie van de SDK inschakelen voor aanvullende informatie.

   Als alles correct werkt, zou u volgende logboeken moeten zien:

   ```
   "Analytics - Received referrer information(<referrer content>)" 
   "Analytics - Trying to fetch referrer data from (acquisition end url)"; 
   "Analytics - Received Referrer Data(<A JSON Response>)"
   ```

   Als deze logboeken niet worden weergegeven, controleert u of u de stappen 6 tot en met 10 hebt uitgevoerd.

   De volgende tabel bevat aanvullende informatie over de mogelijke fouten:

   | Fout | Beschrijving |
   |--- |--- |
   | Analytics - Unable to decode response(`<string>`). | De reactie is onjuist geformuleerd. |
   | Analytics - Unable to parse response (`a JSON Response`). | De JSON-tekenreeks is onjuist geformuleerd. |
   | Analytics - Unable to parse purchase service response (no `contextData` parameter in response). | Er zit geen `contextData` parameter in de reactie. |
   | Analytics - Acquisition reference data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name` is niet opgenomen in contextData. |
   | Analytics - Acquisition reference time out. | Kan de reactie niet ophalen in de tijd gedefinieerd door `referrerTimeout`. Verhoog de waarde en probeer het opnieuw.  Zorg er ook voor dat u de acquisitie-koppeling hebt geopend voordat u de app installeert. |

De volgende informatie onthouden:

* De uren die van app worden verzonden kunnen worden gecontroleerd door de controlehulpmiddelen van HTTP te gebruiken om de verwervingsattributie te verifiëren.
* Zie Meting van Google Play Campagne `INSTALL_REFERRER`testen in de handleiding Google Developers voor meer informatie over het uitzenden van [de camera](https://developers.google.com/analytics/solutions/testing-play-campaigns) .
* U kunt het meegeleverde gereedschap `acquisitionTest.jar` Java gebruiken om u te helpen de unieke id op te halen en de installatiefunctie voor uitzendingen uit te zenden, waarmee u op uw beurt de informatie in de stappen 3 tot en met 10 kunt opvragen.

**Het Java-gereedschap installeren**

Java installeren:

1. Download het [`acquistionTester.zip`](../assets/acquisitionTester.zip) bestand.
1. Extraheer het .jar-bestand.

   U kunt het .jar dossier op de bevellijn in werking stellen.

Bijvoorbeeld:

```
java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
```

De marketingkoppelingen worden in het cachegeheugen geplaatst aan de serverzijde met een vervaltijd van tien minuten. Wanneer u wijzigingen aanbrengt in het markeren van koppelingen, wacht u ongeveer 10 minuten voordat de wijzigingen van kracht worden voordat u de koppelingen opnieuw gebruikt.
