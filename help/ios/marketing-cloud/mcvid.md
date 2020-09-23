---
description: De Adobe Experience Platform Identity Service biedt een universele bezoekersidentiteitskaart voor alle Experience Cloud-oplossingen. De dienst van identiteitskaart wordt vereist door Analytics voor Doel, videohartslag, en toekomstige integratie van Experience Cloud.
seo-description: De Adobe Experience Platform Identity Service biedt een universele bezoekersidentiteitskaart voor alle Experience Cloud-oplossingen. De dienst van identiteitskaart wordt vereist door Analytics voor Doel, videohartslag, en toekomstige integratie van Experience Cloud.
seo-title: Experience Cloud-id
solution: Experience Cloud,Analytics
title: Experience Cloud-id
topic: Developer and implementation
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 3%

---


# Experience Cloud ID {#experience-cloud-id}

De Adobe Experience Platform Identity Service biedt een universele bezoekersidentiteitskaart voor alle Experience Cloud-oplossingen. De dienst van identiteitskaart wordt vereist door Analytics voor Doel, videohartslag, en toekomstige integratie van Experience Cloud.

>[!TIP]
>
>U hoeft de Experience Cloud-id alleen in te vullen met de Adobe Experience Platform Identity Service. Zie [Adobe Experience Platform Identity Service](https://docs.adobe.com/content/help/nl-NL/id-service/using/home.html)voor meer informatie.

**Vereist SDK versie 4.3 of hoger**

## Enable the Experience Cloud ID {#section_79F984271C3B4366B7B04F864F4FF8C2}

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

   De organisatie-id&#39;s van Experience Cloud identificeren uniek elk clientbedrijf in de Adobe Experience Cloud en zijn vergelijkbaar met de volgende waarde: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >U dient dit op te nemen `@AdobeOrg`.

   Als deze waarden niet aanwezig zijn, downloadt u een bijgewerkt `ADBMobileConfig.json` bestand van de mobiele Adobe-services. Zie [ADBMobile JSON config](/help/ios/getting-started/requirements.md)voor meer informatie.

Na de configuratie, wordt een identiteitskaart van de Experience Cloud geproduceerd en inbegrepen op alle treffers. Andere bezoeker-id&#39;s, zoals aangepaste en automatisch gegenereerde id&#39;s, worden bij elke treffer verzonden.
