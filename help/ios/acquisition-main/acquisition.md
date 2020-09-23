---
description: Verwervingskoppelingen met unieke volgcodes kunnen worden gegenereerd in Adobe Mobile-services. Wanneer een gebruiker een app downloadt en uitvoert vanuit de Apple App Store nadat hij op de gegenereerde koppeling heeft geklikt, verzamelt de SDK automatisch de overnamegegevens en stuurt deze naar Adobe Mobile-services.
seo-description: Verwervingskoppelingen met unieke volgcodes kunnen worden gegenereerd in Adobe Mobile-services. Wanneer een gebruiker een app downloadt en uitvoert vanuit de Apple App Store nadat hij op de gegenereerde koppeling heeft geklikt, verzamelt de SDK automatisch de overnamegegevens en stuurt deze naar Adobe Mobile-services.
seo-title: Aanschaf van mobiele apps
solution: Experience Cloud,Analytics
title: Aanschaf van mobiele apps
topic: Developer and implementation
uuid: 5fece619-e4b8-4d06-9250-dcb66fa32ce0
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---


# Mobile app acquisition {#mobile-app-acquisition}

Verwervingskoppelingen met unieke volgcodes kunnen worden gegenereerd in Adobe Mobile-services. Wanneer een gebruiker een app downloadt en uitvoert vanuit de Apple App Store nadat hij op de gegenereerde koppeling heeft geklikt, verzamelt de SDK automatisch de overnamegegevens en stuurt deze naar Adobe Mobile-services.

Als u Acquisition wilt gebruiken, **moet** u SDK versie 4.1 of hoger hebben.

Verwervingsverbindingen moeten in de Mobiele diensten van Adobe worden gecreeerd. Zie [Overname](/help/using/acquisition-main/acquisition-main.md)voor meer informatie.

Aan de hand van de informatie in deze sectie kan de SDK aanschafgegevens verzenden vanuit een acquisitie-koppeling.

## Aanschaf van mobiele apps bijhouden {#section_CEA30C652AC8470784B8054E299B80FA}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie SDK en configuratiebestand *toevoegen aan uw project* in [Core-implementatie en levenscyclus](/help/ios/getting-started/dev-qs.md)voor meer informatie.
1. De bibliotheek importeren:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Controleer of het `ADBMobileConfig.json` bestand de vereiste acquisitie-instellingen bevat:

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

   De `acquisition` instellingen worden gegenereerd door Adobe Mobile-services en mogen niet worden gewijzigd. Voor meer informatie over hoe te om een aangepast `ADBMobileConfig.json` dossier met de vooraf gevormde montages te downloaden, zie `acquisition` alvorens u begint [](/help/ios/getting-started/requirements.md).

Nadat deze instellingen zijn ingeschakeld, worden acquisitiegegevens automatisch verzonden met de eerste levenscyclusaanroep nadat de app voor het eerst is gestart.

>[!CAUTION]
>
>`referrerTimeout` moet een waarde hoger dan 0 zijn om het aanschaffen van apps mogelijk te maken.

## Uw iOS-app inschakelen voor Universal Links

Als u Universal Links gebruikt in uw app, voegt u het domein Adobe-marketingkoppelingen toe aan de lijst Gekoppelde domeinen voor uw app.

In Xcode, om uw domein van de Verbindingen van de Adobe Marketing aan de Gekoppelde lijst van Domeinen toe te voegen:

1. Ga naar uw projectdoel en klik de **[!UICONTROL Capabilities]** tabel.
2. Schuif omlaag naar de **[!UICONTROL Associated Domains]** sectie en schakel deze in.
3. Voeg een ingang in de **[!UICONTROL Domains]** lijst voor uw domein van de Verbindingen van de Marketing van uw Verbindingen URL toe.

Uw invoer zal er ongeveer zo uitzien `applinks:5848561889a02a6996aea62b.c00.adobe.com`.