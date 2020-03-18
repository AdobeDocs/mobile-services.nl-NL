---
description: De identiteitsservice van het Adobe Experience Platform biedt een universele bezoeker-id voor alle Experience Cloud-oplossingen. De id-service wordt vereist door Analytics voor Target, videohartslag en toekomstige Experience Cloud-integratie.
seo-description: De identiteitsservice van het Adobe Experience Platform biedt een universele bezoeker-id voor alle Experience Cloud-oplossingen. De id-service wordt vereist door Analytics voor Target, videohartslag en toekomstige Experience Cloud-integratie.
seo-title: Configuratie van Experience Cloud ID
solution: Marketing Cloud,Analytics
title: Configuratie van Experience Cloud ID
topic: Developer and implementation
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Configuratie van Experience Cloud ID {#experience-cloud-id-configuration}

De identiteitsservice van het Adobe Experience Platform biedt een universele bezoeker-id voor alle Experience Cloud-oplossingen. De id-service wordt vereist door Analytics voor Target, videohartslag en toekomstige Experience Cloud-integratie.

>[!TIP]
>
>U hoeft deze id alleen in te vullen met de Adobe Experience Platform Identity Service. Zie [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/)voor meer informatie.

>[!IMPORTANT]
>
>Voor deze functionaliteit is SDK-versie 4.3 of hoger vereist.

Zo schakelt u de Experience Cloud-id in:

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Voor meer informatie, zie *Voeg het Dossier SDK en Config aan uw IDEA IntelliJ of Project* Eclipse in de implementatie en de levenscyclus [van de](/help/android/getting-started/dev-qs.md)Kern toe.

1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. Controleer of het `ADBMobileConfig.json` bestand het volgende bevat `marketingCloudorg`:

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Ervaar de organisatie-id&#39;s van de cloud die uniek zijn voor elk clientbedrijf in de Adobe Experience Cloud en die overeenkomen met de volgende waarde:

   ```js
   016D5C175213CCA80A490D05@AdobeOrg`
   ```

   >[!IMPORTANT]
   >
   >U dient dit op te nemen `@AdobeOrg`.

   Als deze id&#39;s niet zijn geconfigureerd, downloadt u een bijgewerkt `ADBMobileConfig.json` bestand van Adobe Mobile-services. Zie [Voor u begint](/help/android/getting-started/requirements.md)voor meer informatie.

Nadat de configuratie is voltooid, wordt een Experience Cloud-id gegenereerd en opgenomen in alle hits. Andere id&#39;s, zoals aangepaste en automatisch gegenereerde id&#39;s, worden bij elke treffer nog steeds verzonden.
