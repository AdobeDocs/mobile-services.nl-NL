---
description: Verwervingskoppelingen met unieke volgcodes kunnen worden gegenereerd in Adobe Mobile-services. Wanneer een gebruiker een app downloadt en uitvoert vanuit de Apple App Store nadat hij op de gegenereerde koppeling heeft geklikt, verzamelt de SDK automatisch de overnamegegevens en stuurt deze naar Adobe Mobile-services.
solution: Experience Cloud,Analytics
title: Aanschaf van mobiele apps
topic-fix: Developer and implementation
uuid: 5fece619-e4b8-4d06-9250-dcb66fa32ce0
exl-id: a90dcb2f-babb-4c97-b67a-8468925ee5c8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Aanschaf van mobiele apps {#mobile-app-acquisition}

Verwervingskoppelingen met unieke volgcodes kunnen worden gegenereerd in Adobe Mobile-services. Wanneer een gebruiker een app downloadt en uitvoert vanuit de Apple App Store nadat hij op de gegenereerde koppeling heeft geklikt, verzamelt de SDK automatisch de overnamegegevens en stuurt deze naar Adobe Mobile-services.

Om Acquisition te gebruiken, **must** heeft SDK versie 4.1 of later.

Verwervingsverbindingen moeten in de Mobiele diensten van Adobe worden gecreeerd. Zie [Acquisitie](/help/using/acquisition-main/acquisition-main.md) voor meer informatie.

Aan de hand van de informatie in deze sectie kan de SDK aanschafgegevens verzenden vanuit een acquisitie-koppeling.

## Aanschaf van mobiele apps bijhouden {#section_CEA30C652AC8470784B8054E299B80FA}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie *SDK en configuratiebestand toevoegen aan uw project* in [Core-implementatie en LiveCycle](/help/ios/getting-started/dev-qs.md) voor meer informatie.
1. De bibliotheek importeren:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Controleer of het `ADBMobileConfig.json`-bestand de vereiste acquisitie-instellingen bevat:

   ```xml
   "acquisition": { 
      "server": "c00.adobe.com", 
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f" 
   }, 
   "analytics": { 
     "referrerTimeout": 5, 
     ...
   ```

   >[!IMPORTANT]
   >
   >Als u gegevens naar meerdere rapportenreeksen verzendt, gebruikt u de aankoopinstellingen (acquisitieserver en appid) van de app die is gekoppeld aan de eerste rapportsuite in uw lijst met id&#39;s van rapportsuite.

   De `acquisition`-instellingen worden gegenereerd door Adobe Mobile-services en mogen niet worden gewijzigd. Voor meer informatie over hoe te om een aangepast `ADBMobileConfig.json` dossier met `acquisition` vooraf gevormde montages te downloaden, zie [Voor u ](/help/ios/getting-started/requirements.md) begint.

Nadat deze instellingen zijn ingeschakeld, worden acquisitiegegevens automatisch verzonden met de eerste levenscyclusaanroep nadat de app voor het eerst is gestart.

>[!CAUTION]
>
>`referrerTimeout` moet een waarde hoger dan 0 zijn om het aanschaffen van apps mogelijk te maken.

## Uw iOS-app inschakelen voor Universal Links

Als u Universal Links gebruikt in uw app, voegt u het domein Adobe-marketingkoppelingen toe aan de lijst Gekoppelde domeinen voor uw app.

In Xcode, om uw domein van de Verbindingen van de Adobe Marketing aan de Gekoppelde lijst van Domeinen toe te voegen:

1. Ga naar uw projectdoel en klik **[!UICONTROL Capabilities]** tabel.
2. Blader omlaag naar de sectie **[!UICONTROL Associated Domains]** en schakel deze in.
3. Voeg een ingang in **[!UICONTROL Domains]** lijst voor uw domein van de Verbindingen van de Marketing van uw Verbindingen URL van de Marketing toe.

Uw invoer zal er ongeveer als `applinks:5848561889a02a6996aea62b.c00.adobe.com` uitzien.
