---
description: De Adobe Experience Platform Identity Service biedt een universele bezoekersidentiteitskaart voor alle Experience Cloud-oplossingen. De dienst van identiteitskaart wordt vereist door Analytics voor Doel, videohartslag, en toekomstige integratie van Experience Cloud.
solution: Experience Cloud Services,Analytics
title: Experience Cloud-id
topic-fix: Developer and implementation
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
exl-id: aa7db365-ad21-431f-bff6-2a6da212dd0c
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# Experience Cloud-id {#experience-cloud-id}

De Adobe Experience Platform Identity Service biedt een universele bezoekersidentiteitskaart voor alle Experience Cloud-oplossingen. De dienst van identiteitskaart wordt vereist door Analytics voor Doel, videohartslag, en toekomstige integratie van Experience Cloud.

>[!TIP]
>
>U hoeft de Experience Cloud-id alleen in te vullen als u de Adobe Experience Platform Identity Service gebruikt. Zie voor meer informatie de [Adobe Experience Platform Identity Service](https://experienceleague.adobe.com/docs/id-service/using/home.html) documentatie.

## Experience Cloud-id inschakelen {#section_79F984271C3B4366B7B04F864F4FF8C2}

Voor deze stappen is SDK-versie 4.3 of hoger vereist.

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie voor meer informatie *SDK en configuratiebestand toevoegen aan uw project* in [Core-implementatie en levenscyclus](/help/ios/getting-started/dev-qs.md).
1. De bibliotheek importeren:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Controleer of de `ADBMobileConfig.json` bevat de `marketingCloud` `org`:

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   De organisatie-id&#39;s van Experience Cloud identificeren uniek elk clientbedrijf in de Adobe Experience Cloud en zijn vergelijkbaar met de volgende waarde: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >U moet `@AdobeOrg`.

   Als deze waarden niet aanwezig zijn, downloadt u een bijgewerkte `ADBMobileConfig.json` bestand van Adobe Mobile-services. Zie voor meer informatie [ADBMobile JSON config](/help/ios/getting-started/requirements.md).

Na de configuratie, wordt een identiteitskaart van de Experience Cloud geproduceerd en inbegrepen op alle treffers. Andere bezoeker-id&#39;s, zoals aangepaste en automatisch gegenereerde id&#39;s, worden bij elke treffer verzonden.
