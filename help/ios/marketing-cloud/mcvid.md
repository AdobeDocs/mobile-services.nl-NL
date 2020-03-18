---
description: De identiteitsservice van het Adobe Experience Platform biedt een universele bezoeker-id voor alle Experience Cloud-oplossingen. De id-service wordt vereist door Analytics voor Target, videohartslag en toekomstige Experience Cloud-integratie.
seo-description: De identiteitsservice van het Adobe Experience Platform biedt een universele bezoeker-id voor alle Experience Cloud-oplossingen. De id-service wordt vereist door Analytics voor Target, videohartslag en toekomstige Experience Cloud-integratie.
seo-title: Experience Cloud ID
solution: Marketing Cloud,Analytics
title: Experience Cloud ID
topic: Developer and implementation
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID {#experience-cloud-id}

De identiteitsservice van het Adobe Experience Platform biedt een universele bezoeker-id voor alle Experience Cloud-oplossingen. De id-service wordt vereist door Analytics voor Target, videohartslag en toekomstige Experience Cloud-integratie.

>[!TIP]
>
>U hoeft de Experience Cloud-id alleen in te vullen met de Adobe Experience Platform Identity Service. Zie [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/)voor meer informatie.

**Vereist SDK versie 4.3 of hoger**

## De Experience Cloud-id inschakelen {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie SDK en configuratiebestand *toevoegen aan uw project* in [Core-implementatie en levenscyclus](/help/ios/getting-started/dev-qs.md)voor meer informatie.
1. De bibliotheek importeren:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Controleer of de `ADBMobileConfig.json` bestanden het `marketingCloud` `org`volgende bevatten:

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Ervaar de organisatie-id&#39;s van de cloud die uniek zijn voor elk clientbedrijf in de Adobe Experience Cloud en die overeenkomen met de volgende waarde: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >U dient dit op te nemen `@AdobeOrg`.

   Als deze waarden niet aanwezig zijn, downloadt u een bijgewerkt `ADBMobileConfig.json` bestand van Adobe Mobile-services. Zie [ADBMobile JSON config](/help/ios/getting-started/requirements.md)voor meer informatie.

Na de configuratie wordt een Experience Cloud-id gegenereerd die wordt opgenomen in alle hits. Andere bezoeker-id&#39;s, zoals aangepaste en automatisch gegenereerde id&#39;s, worden bij elke treffer verzonden.
