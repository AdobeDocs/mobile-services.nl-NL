---
description: Met deze informatie kunt u een koppeling naar een V3-acquisitiecampagne uitvoeren op basis van een vingerafdruk van een apparaat.
seo-description: Met deze informatie kunt u een koppeling naar een V3-acquisitiecampagne uitvoeren op basis van een vingerafdruk van een apparaat.
seo-title: V3-overname testen
solution: Experience Cloud,Analytics
title: V3-overname testen
uuid: 89137ccf-4839-4b37-926e-303cf8e511a5
exl-id: 3cf66802-1f2c-428f-86ef-a9afc57e3470
source-git-commit: 8db8f51a42acbbc0bbc4545b7d97cb214b490ab3
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# V3-acquisitie testen{#testing-v-acquisition}

Met deze informatie kunt u een koppeling naar een V3-acquisitiecampagne uitvoeren op basis van een vingerafdruk van een apparaat.

>[!IMPORTANT]
>
>V3 Acquisition verwijst naar de acquisitie-koppelingen die u maakt met de Acquisition Builder in de gebruikersinterface van Adobe Mobile Services. Als u deze functie wilt gebruiken, moet u een upgrade uitvoeren naar iOS SDK versie 4.6.0 of hoger.

Als de mobiele app zich nog niet in de App Store bevindt, selecteert u bij het maken van de koppeling naar de campagne een willekeurige mobiele app als bestemming. Dit is alleen van invloed op de app waarnaar de verwervingsserver u omleidt nadat u op de verwervingskoppeling hebt geklikt, maar heeft geen invloed op de mogelijkheid om de koppeling te testen.

1. Voltooi de vereiste taken in [Mobile App Acquisition](/help/ios/acquisition-main/acquisition.md).
1. Navigeer naar **[!UICONTROL Acquisition Builder]** in de UI van de Diensten van de Mobiele Adobe en produceer een aanschafcampagne URL.

   Bijvoorbeeld:

   ```
   https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode
   ```


   Als u zowel iOS- als Android-apps in de aankoopkoppeling gebruikt, gebruikt u de Apple Store als de standaardwinkel.
1. Open de gegenereerde koppeling in een desktopbrowser en ga naar `https://c00.adobe.com/v3/<appid>/end`.

   De `contextData` moet worden weergegeven in het JSON-antwoord:

   ```js
   {"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.
   ```

   Als u `contextData` niet ziet, of een deel ervan ontbreekt, zorg ervoor dat de aanschaf-URL de indeling volgt die is opgegeven in [Handmatig overnamekoppeling maken](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md).
1. Controleer of de volgende instellingen in het configuratiebestand correct zijn:

   | Instelling | Waarde |
   |--- |--- |
   | verwerving | De server moet `c00.adobe.com` zijn. *`appid`* moet gelijk zijn aan de  *`appid`* in uw acquisitie-koppeling. |
   | analyse | `referrerTimeout` moet een waarde groter dan 0 hebben. |


1. (Voorwaardelijk) Als de `ssl`-instelling in het configuratiebestand van uw app waar is, werkt u uw acquisitie-koppeling bij om het HTTPS-protocol te gebruiken.
1. Klik op de gegenereerde koppeling van het mobiele apparaat waarop u de toepassing wilt installeren.

   Adobe ( `c00.adobe.com`) slaan vingerafdruk op en leiden deze om naar de App Store. De app hoeft niet te worden gedownload om te testen.
1. Start de toepassing voor de eerste keer vanaf hetzelfde mobiele apparaat als dat u in stap 6 hebt gebruikt.

   U kunt de toepassing indien nodig verwijderen en opnieuw installeren.
1. (Optioneel) U kunt foutopsporingslogboekregistratie van de SDK inschakelen voor aanvullende informatie.

   Als alles correct werkt, zou u volgende logboeken moeten zien:

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   Als de bovenstaande logboeken niet worden weergegeven, controleert u of u de stappen 4 en 5 hebt uitgevoerd.

   Hier volgt informatie over mogelijke fouten:

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`
Er is een netwerkfout opgetreden.

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      De reactie heeft niet de juiste indeling.

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      De reactie bevat geen parameter `contextData`.

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` is niet opgenomen in  `contextData`.

   * `Analytics - Acquisition referrer timed out`

      Kan de reactie niet ophalen in de tijd die wordt gedefinieerd door `referrerTimeout`. Verhoog de waarde en probeer het opnieuw. Zorg er ook voor dat u de acquisitie-koppeling hebt geopend voordat u de app installeert en dat u hetzelfde netwerk gebruikt wanneer u op de URL klikt en de app opent.

      De volgende informatie onthouden:

      * De verwervingsserver biedt een toewijzingsovereenkomst die is gebaseerd op het IP-adres en de informatie van de gebruikersagent die is opgenomen in de koppelingsklik (stap 6) en wanneer de app wordt gestart (stap 7).

         U moet zich op hetzelfde netwerk bevinden wanneer u op de URL klikt en de app opent.

      * Met de HTTP-controleprogramma&#39;s kunt u controles uitvoeren op resultaten die vanuit de app worden verzonden om de acquisitie-toewijzing te controleren.

         Er wordt een `/v3/<appid>/start`-verzoek weergegeven en een `/v3/<appid>/end`-verzoek dat naar de overnameserver is verzonden. De variaties in verzonden user-agent zouden attributie kunnen veroorzaken om te ontbreken.

         >[!TIP]
         >
         >Zorg ervoor dat `https://c00.adobe.com/v3/<appid>/start` en `https://c00.adobe.com/v3/<appid>/end` dezelfde gebruiker-agent waarden hebben.

      * De acquisitie-koppeling en de hit van de SDK moeten hetzelfde HTTP/HTTPS-protocol gebruiken.

         Als zij verschillende protocollen gebruiken (bijvoorbeeld, gebruikt de verbinding HTTP en SDK HTTPS), zou het IP adres voor elk verzoek (op sommige dragers) kunnen verschillen, en de attributie zou kunnen ontbreken.
