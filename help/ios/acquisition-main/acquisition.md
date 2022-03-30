---
description: Verwervingskoppelingen met unieke volgcodes kunnen worden gegenereerd in Adobe Mobile-services. Wanneer een gebruiker een app downloadt en uitvoert vanuit de Apple App Store nadat hij op de gegenereerde koppeling heeft geklikt, verzamelt de SDK automatisch de overnamegegevens en stuurt deze naar de Adobe Mobile-services.
solution: Experience Cloud Services,Analytics
title: Aanschaf Mobile-app
topic-fix: Developer and implementation
uuid: 5fece619-e4b8-4d06-9250-dcb66fa32ce0
exl-id: a90dcb2f-babb-4c97-b67a-8468925ee5c8
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Aanschaf Mobile-app {#mobile-app-acquisition}

Verwervingskoppelingen met unieke volgcodes kunnen worden gegenereerd in Adobe Mobile-services. Wanneer een gebruiker een app downloadt en uitvoert vanuit de Apple App Store nadat hij op de gegenereerde koppeling heeft geklikt, verzamelt de SDK automatisch de overnamegegevens en stuurt deze naar de Adobe Mobile-services.

Om Acquisitie te gebruiken, **moet** hebben SDK versie 4.1 of hoger.

Verwervingskoppelingen moeten worden gemaakt in Adobe Mobile-services. Zie voor meer informatie [Verwerving](/help/using/acquisition-main/acquisition-main.md).

Aan de hand van de informatie in deze sectie kan de SDK aanschafgegevens verzenden vanuit een acquisitie-koppeling.

## Aanschaf van mobiele apps bijhouden {#section_CEA30C652AC8470784B8054E299B80FA}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie voor meer informatie *SDK en configuratiebestand toevoegen aan uw project* in [Core-implementatie en levenscyclus](/help/ios/getting-started/dev-qs.md).
1. De bibliotheek importeren:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Controleer of de `ADBMobileConfig.json` bestand bevat de vereiste acquisitie-instellingen:

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

   De `acquisition` instellingen worden gegenereerd door Adobe Mobile-services en mogen niet worden gewijzigd. Voor meer informatie over het downloaden van aangepaste `ADBMobileConfig.json` met de `acquisition` vooraf geconfigureerde instellingen, zie [Voordat u begint](/help/ios/getting-started/requirements.md).

Nadat deze instellingen zijn ingeschakeld, worden acquisitiegegevens automatisch verzonden met de eerste levenscyclusaanroep nadat de app voor het eerst is gestart.

>[!CAUTION]
>
>`referrerTimeout` moet een waarde hoger dan 0 zijn om het aanschaffen van apps mogelijk te maken.

## iOS-app voor Universal Links inschakelen

Als u Universal Links gebruikt in uw app, voegt u het domein Adobe-marketingkoppelingen toe aan de lijst Gekoppelde domeinen voor uw app.

In Xcode, om uw domein van de Verbindingen van de Adobe Marketing aan de Gekoppelde lijst van Domeinen toe te voegen:

1. Ga naar uw projectdoel en klik op de knop **[!UICONTROL Capabilities]** tab.
2. Omlaag schuiven naar **[!UICONTROL Associated Domains]** en schakelt u deze in.
3. Een item toevoegen in het dialoogvenster **[!UICONTROL Domains]** lijst voor uw domein van de Verbindingen van de Marketing van uw Verbindingen URL.

Uw invoer ziet er ongeveer zo uit  `applinks:5848561889a02a6996aea62b.c00.adobe.com`.
