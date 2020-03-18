---
description: De volgende instructies helpen u een aanschafcampagne met een Verbinding van de Marketing uitvoeren die op een apparatenvingerafdruk gebaseerd is.
keywords: android;library;mobile;sdk
seo-description: De volgende instructies helpen u een aanschafcampagne met een Verbinding van de Marketing uitvoeren die op een apparatenvingerafdruk gebaseerd is.
seo-title: Verwerving marketinglink testen
solution: Marketing Cloud,Analytics
title: Verwerving marketinglink testen
topic: Developer and implementation
uuid: 69503e01-182d-44c6-b0fb-e1c012ffa3bd
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Verwerving marketinglink testen {#testing-marketing-link-acquisition}

De volgende instructies helpen u een aanschafcampagne met een Verbinding van de Marketing uitvoeren die op een apparatenvingerafdruk gebaseerd is.

1. Voltooi de vereiste taken in [Mobile App Acquisition](/help/ios/acquisition-main/acquisition.md).
1. Klik in de gebruikersinterface van Adobe Mobile Services op een URL voor een inkoopmarketingkoppeling **[!UICONTROL Marketing Links Builder]** en genereer deze die de App Store instelt als de bestemming voor iOS-apparaten.

   Bijvoorbeeld:

   ```
   https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f
   ```

   Zie [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md)voor meer informatie.


1. Open de gegenereerde koppeling op het iOS-apparaat en open `https://c00.adobe.com/v3/<appid>/end`.

   U moet de contextData zien in het JSON-antwoord:

   ```js{"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":
   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}
   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

1. Controleer of de volgende instellingen in het configuratiebestand correct zijn:

   | Instelling | Waarde |
   |--- |--- |
   | verwerving | De server moet `c00.adobe.com`zijn. `appid` moet gelijk zijn aan de *`appid`* in uw acquisitie-koppeling. |
   | analyse | `referrerTimeout` moet een waarde groter dan 0 hebben. |

1. (Voorwaardelijk) Als de SSL-instelling in het configuratiebestand van uw app is `false`, werkt u uw acquisitie-koppeling bij zodat u het HTTP-protocol in plaats van HTTPS kunt gebruiken.
1. Klik op de gegenereerde koppeling van het mobiele apparaat waarop u de toepassing wilt installeren.

   De vingerafdruk wordt opgeslagen op de servers (`c00.adobe.com`) van Adobe en omgeleid naar de App Store. De app hoeft niet te worden gedownload om te testen.
1. Start de toepassing voor de eerste keer vanaf hetzelfde mobiele apparaat als dat u in stap 6 hebt gebruikt.

   U kunt de toepassing indien nodig verwijderen en opnieuw installeren.
1. (Optioneel) Schakel foutopsporingslogbestand van de SDK in om aanvullende informatie op te halen.

   Als alles correct werkt, zou u volgende logboeken moeten zien:

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   Als deze logboeken niet worden weergegeven, controleert u of u de stappen 4 en 5 hebt uitgevoerd.

   Hier volgt informatie over mogelijke fouten:

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`:

      Er is een netwerkfout opgetreden.

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      De reactie heeft niet de juiste indeling.

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      De reactie bevat geen `contextData` parameter.

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` is niet opgenomen in `contextData`.

   * `Analytics - Acquisition referrer timed out`

      Kan de reactie niet ophalen in de tijd die wordt gedefinieerd door `referrerTimeout`. Verhoog de waarde en probeer het opnieuw. Zorg er ook voor dat u de acquisitie-koppeling hebt geopend voordat u de app installeert en dat u hetzelfde netwerk gebruikt wanneer u op de URL klikt en de app opent.

De volgende informatie onthouden:

* De verwervingsserver biedt een toewijzingsovereenkomst die is gebaseerd op het IP-adres en de informatie van de gebruikersagent die is opgenomen in de koppelingsklik (stap 6) en wanneer de app wordt gestart (stap 7).

   U moet zich op hetzelfde netwerk bevinden wanneer u op de URL klikt en de app opent.

* Met de HTTP-controleprogramma&#39;s kunt u hits die vanuit de app worden verzonden controleren om de acquisitie-toewijzing te controleren.

   U zou één `/v3/<appid>/start` verzoek en één `/v3/<appid>/end` verzoek moeten zien die naar de verwervingsserver worden verzonden.

* De variaties in verzonden user-agent zouden attributie kunnen veroorzaken om te ontbreken.

   Zorg ervoor dat `https://c00.adobe.com/v3/<appid>/start` en `https://c00.adobe.com/v3/<appid>/end` dezelfde gebruiker-agent waarden hebben.

* De acquisitie-koppeling en de hit van de SDK moeten hetzelfde HTTP/HTTPS-protocol gebruiken.

   Als de verbinding en de slag verschillende protocollen gebruiken, waar bijvoorbeeld, de verbinding HTTP gebruikt en SDK HTTPS gebruikt, zou het IP adres op sommige dragers voor elke aanvraag kunnen verschillen. Hierdoor kan de toewijzing mislukken.

* De marketingkoppelingen worden in het cachegeheugen geplaatst aan de serverzijde met een vervaltijd van tien minuten.

   Wanneer u wijzigingen aanbrengt in marketingkoppelingen, moet u ongeveer 10 minuten wachten voordat u de koppelingen gebruikt.