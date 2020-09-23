---
description: De Adobe Experience Platform Identity Service biedt een universele bezoekersidentiteitskaart voor alle Experience Cloud-oplossingen. De dienst van identiteitskaart wordt vereist door Analytics voor Doel, videohartslag, en toekomstige integratie van Experience Cloud.
seo-description: De Adobe Experience Platform Identity Service biedt een universele bezoekersidentiteitskaart voor alle Experience Cloud-oplossingen. De dienst van identiteitskaart wordt vereist door Analytics voor Doel, videohartslag, en toekomstige integratie van Experience Cloud.
seo-title: Experience Cloud ID-configuratie
solution: Experience Cloud,Analytics
title: Experience Cloud ID-configuratie
topic: Developer and implementation
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 2%

---


# Experience Cloud ID-configuratie {#experience-cloud-id-configuration}

De Adobe Experience Platform Identity Service biedt een universele bezoekersidentiteitskaart voor alle Experience Cloud-oplossingen. De dienst van identiteitskaart wordt vereist door Analytics voor Doel, videohartslag, en toekomstige integratie van Experience Cloud.

>[!TIP]
>
>U hoeft deze id alleen in te vullen met de Adobe Experience Platform Identity Service. Zie [Adobe Experience Platform Identity Service](https://docs.adobe.com/content/help/nl-NL/id-service/using/home.html)voor meer informatie.

>[!IMPORTANT]
>
>Voor deze functionaliteit is SDK-versie 4.3 of hoger vereist.

De Experience Cloud-id inschakelen:

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

   De organisatie-id&#39;s van Experience Cloud identificeren uniek elk clientbedrijf in de Adobe Experience Cloud en zijn vergelijkbaar met de volgende waarde:

   ```js
   016D5C175213CCA80A490D05@AdobeOrg`
   ```

   >[!IMPORTANT]
   >
   >U dient dit op te nemen `@AdobeOrg`.

   Als deze id&#39;s niet zijn geconfigureerd, downloadt u een bijgewerkt `ADBMobileConfig.json` bestand van de Adobe Mobile-services. Zie [Voor u begint](/help/android/getting-started/requirements.md)voor meer informatie.

Nadat de configuratie volledig is, wordt een identiteitskaart van de Experience Cloud geproduceerd en inbegrepen op alle treffers. Andere id&#39;s, zoals aangepaste en automatisch gegenereerde id&#39;s, worden bij elke treffer nog steeds verzonden.
