---
description: De volgende instructies helpen u een acquisitiecampagne met een Marketing Link op een Android-apparaat te roundtrip.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Verwerving marketingkoppeling testen
topic-fix: Developer and implementation
uuid: d0933dcc-8fc3-4f60-987f-7a54559aacf5
exl-id: 86fdaef7-5b6c-4e9d-a470-df66c96f2e9d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 1%

---

# Verwerving marketinglink testen {#testing-marketing-link-acquisition}

De volgende instructies helpen u een acquisitiecampagne met een Marketing Link op een Android-apparaat te roundtrip.

Als uw mobiele app zich nog niet in Google Play bevindt, kunt u bij het maken van de marketingkoppeling elke mobiele app als doel selecteren. Dit is alleen van invloed op de app waarnaar de verwervingsserver u omleidt, nadat u op de verwervingskoppeling klikt en niet op de mogelijkheid om de verwervingskoppeling te testen. Parameters van de queryreeks worden doorgegeven aan de Google Play-winkel. Deze worden tijdens de installatie doorgegeven aan de app als onderdeel van een campagneuitzending. Voor het testen van het aanschaffen van mobiele apps voor Roundtrip is de simulatie van dit type uitzending vereist.

De app moet nieuw zijn geïnstalleerd of gegevens moeten zijn gewist **[!UICONTROL Settings]**, elke keer dat een test wordt uitgevoerd. Dit zorgt ervoor dat de aanvankelijke levenscyclusmetriek die met de de koordparameters van de campagnerequery wordt geassocieerd worden verzonden wanneer app voor het eerst wordt gelanceerd.

1. Voltooi de vereiste taken in [Aanschaf Mobile-app](/help/android/acquisition-main/acquisition.md) en zorg ervoor dat u de broadcastontvanger correct hebt geïmplementeerd voor `INSTALL_REFERRER`.
1. Klik in de gebruikersinterface van Adobe Mobile Services op  **[!UICONTROL Acquisition]** > **[!UICONTROL Marketing Links Builder]** en genereer een Acquisition Marketing Link URL die Google Play instelt als het doel voor Android-apparaten.

   Zie voor meer informatie [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).

   Bijvoorbeeld:

   `https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. Open de gegenereerde koppeling op het Android-apparaat.

   U moet worden omgeleid naar een pagina met een URL die lijkt op het volgende voorbeeld:

   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. De unieke id kopiëren na `utm_content%3D`.

   In het vorige voorbeeld is de id `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

   Als u de unieke id niet op het apparaat kunt ophalen, voert u het volgende uit `CURL` op uw bureaublad om de unieke id op te halen uit de responstekenreeks.

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" <Your Marketing Link>`

   Bijvoorbeeld:

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. Construeer de verbinding van het verwervingseind door unieke identiteitskaart van stap 3 te gebruiken, door het volgende formaat te gebruiken:

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`

   Bijvoorbeeld: `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Open de koppeling in een browser.

   Je moet de `contextData` in het JSON-antwoord:

   ```
   {"fingerprint":"44b2f88a062df7e727c047f006deb9971304617b","endCallbacks":["***"],"timestamp":1464301282,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData": 
   {"a.launch.campaign.trackingcode":"trymttvm","a.referrer.campaign.name":"Android Demo","a.referrer.campaign.trackingcode":"trymttvm"} 
   ,"adobeData":{"unique_id":"9a2be52764a8db125c29a8c10f3b1b3d5d8ed915","deeplinkid":"57476c26072932ec6d3a470b"}}.
   ```

1. Herhaal stap 3 voor een nieuwe unieke id.
1. Controleer of de volgende instellingen in het configuratiebestand correct zijn:

   | Instelling | Waarde |
   |--- |--- |
   | verwerving | De server moet `c00.adobe.com`, en      *`appid`*  moet gelijk zijn aan `appid` in uw acquisitie link. |
   | analyse | Voor testdoeleinden stelt u de time-out van de referentie zo in dat er voldoende tijd (60 seconden of meer) is om de uitzending handmatig te verzenden. U kunt de oorspronkelijke time-outinstelling na de test herstellen. |

1. Sluit het apparaat aan op een computer, verwijder en installeer de toepassing opnieuw.
1. Start ADB Shell en start de toepassing op het apparaat.

   ```
   adb shell
   ```

1. Verzend uitzending met behulp van het volgende `adb` opdracht:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"
   ```

1. Vervangen `com.adobe.android` met de pakketnaam van uw toepassing, werkt u de verwijzing naar de ontvanger bij met de verwijzing naar de locatie van de ontvanger voor het bijhouden van de campagne in uw app en vervangt u de waarden die aan `utm_content`.

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
   | Analytics - Unable to parse acquisition service response (no `contextData` parameter in reactie). | Er is geen  `contextData`  in de reactie. |
   | Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in contextgegevens), negeren. | `a.referrer.campaign.name` is niet opgenomen in contextData. |
   | Analytics - Acquisition reference time out. | Kan de reactie niet ophalen in de tijd gedefinieerd door `referrerTimeout`. Verhoog de waarde en probeer het opnieuw.  Zorg er ook voor dat u de acquisitie-koppeling hebt geopend voordat u de app installeert. |

De volgende informatie onthouden:

* De uren die van app worden verzonden kunnen worden gecontroleerd door de controlehulpmiddelen van HTTP te gebruiken om de verwervingsattributie te verifiëren.
* Voor meer informatie over hoe te om uit te zenden `INSTALL_REFERRER`, zie [Meting van Google Play-campagne testen](https://developers.google.com/analytics/solutions/testing-play-campaigns) in de handleiding voor Google-ontwikkelaars.
* U kunt de meegeleverde `acquisitionTest.jar` Het hulpmiddel van Java om u te helpen de unieke identiteitskaart krijgen en uitzendingsreferentie, die beurtelings u helpt de informatie in stappen 3 tot 10 verkrijgen.

**Het Java-gereedschap installeren**

Java installeren:

1. Download de [`acquistionTester.zip`](../assets/acquisitionTester.zip) bestand.
1. Extraheer het .jar-bestand.

   U kunt het .jar dossier op de bevellijn in werking stellen.

Bijvoorbeeld:

```
java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
```

De marketingkoppelingen worden in het cachegeheugen geplaatst aan de serverzijde met een vervaltijd van tien minuten. Wanneer u wijzigingen aanbrengt in het markeren van koppelingen, wacht u ongeveer 10 minuten voordat de wijzigingen van kracht worden voordat u de koppelingen opnieuw gebruikt.
