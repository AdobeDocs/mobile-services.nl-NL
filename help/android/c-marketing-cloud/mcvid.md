---
description: De Adobe Experience Platform Identity Service biedt een universele bezoekersidentiteitskaart voor alle Experience Cloud-oplossingen. De dienst van identiteitskaart wordt vereist door Analytics voor Doel, videohartslag, en toekomstige integratie van Experience Cloud.
solution: Experience Cloud,Analytics
title: Experience Cloud ID-configuratie
topic-fix: Developer and implementation
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
exl-id: 97dc6768-bf31-4a0d-a460-9caf9ecda5fb
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Experience Cloud ID-configuratie {#experience-cloud-id-configuration}

De Adobe Experience Platform Identity Service biedt een universele bezoekersidentiteitskaart voor alle Experience Cloud-oplossingen. De dienst van identiteitskaart wordt vereist door Analytics voor Doel, videohartslag, en toekomstige integratie van Experience Cloud.

>[!TIP]
>
>U hoeft deze id alleen in te vullen met de Adobe Experience Platform Identity Service. Zie [Adobe Experience Platform Identity Service](https://experienceleague.adobe.com/docs/id-service/using/home.html) voor meer informatie.

>[!IMPORTANT]
>
>Voor deze functionaliteit is SDK-versie 4.3 of hoger vereist.

De Experience Cloud-id inschakelen:

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Voor meer informatie, zie *Voeg het dossier SDK en Config aan uw Project IntelliJ IDEA of Eclipse* in [de implementatie van de Kern en levenscyclus](/help/android/getting-started/dev-qs.md) toe.

1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. Controleer of het `ADBMobileConfig.json`-bestand `marketingCloudorg` bevat:

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
   >U moet `@AdobeOrg` omvatten.

   Als deze id&#39;s niet zijn geconfigureerd, downloadt u een bijgewerkt `ADBMobileConfig.json`-bestand van de Adobe Mobile-services. Voor meer informatie, zie [Voor u ](/help/android/getting-started/requirements.md) begint.

Nadat de configuratie volledig is, wordt een identiteitskaart van de Experience Cloud geproduceerd en inbegrepen op alle treffers. Andere id&#39;s, zoals aangepaste en automatisch gegenereerde id&#39;s, worden bij elke treffer nog steeds verzonden.
