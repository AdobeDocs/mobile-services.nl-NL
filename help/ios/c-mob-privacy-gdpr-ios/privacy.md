---
description: Deze informatie helpt u met een GDPR verzoek om gegevens te schrappen.
seo-description: Deze informatie helpt u met een GDPR verzoek om gegevens te schrappen.
seo-title: De status Opt van de gebruiker instellen
solution: Experience Cloud,Analytics
title: De status Opt van de gebruiker instellen
topic-fix: Developer and implementation
uuid: 44a09a25-93c6-4e1a-b69e-710018e8b6c3
exl-id: 8fd30bea-6316-46ac-9787-8ca594545d1b
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# De status {#setting-the-user-s-opt-status} van de gebruiker instellen

Deze informatie helpt u met een GDPR verzoek om gegevens te schrappen.

>[!IMPORTANT]
>
>Vanaf Experience Cloud iOS SDKs 4.15, die de privacystatus aan `unknown` plaatst houdt Audience Manager en Experience Cloud identiteitskaart- klappen.

U kunt met de volgende instellingen bepalen of de activiteit Analytics, Target en Audience Manager is toegestaan op een apparaat:

* `privacyDefault` in  [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md).

   Met deze instelling bepaalt u de begininstelling die blijft bestaan totdat deze in de code wordt gewijzigd.

* `setPrivacyStatus` methode.

   Nadat de privacy-instelling met deze methode is gewijzigd, is de wijziging permanent totdat deze opnieuw wordt gewijzigd met deze methode, of wanneer u de app opnieuw verwijdert en installeert.

   Voor meer informatie over de methodes, zie [de Methoden van de Configuratie](/help/ios/configuration/json-config/json-config.md).

Hier volgt informatie over elke privacystatus:

* **Aanmelden**

   * Analyse: De berichten worden verzonden.
   * Doel: Mbox-aanvragen worden verzonden.
   * Audience Manager: Signalen en id-syncs worden verzonden.
   * Waarde in het JSON-configuratiebestand: `optedin`
   * Waarde in `setPrivacyStatus`: `ADBMobilePrivacyStatusOptIn`

* **Weigeren**

   * Analyse: Hits worden weggegooid.
   * Doel: Mbox-aanvragen zijn niet toegestaan.
   * Audience Manager: Signalen en id-syncs zijn niet toegestaan.
   * Waarde in het JSON-configuratiebestand: `optedout`
   * Waarde in `setPrivacyStatus`: `ADBMobilePrivacyStatusOptOut`

* **Onbekend**

   * Analyse: Als offline bijhouden **is** ingeschakeld, worden treffers opgeslagen totdat de privacystatus verandert in opt-in (hits worden verzonden) of opt-out (hits worden genegeerd).

      Als het offline volgen **niet** toegelaten is, worden de klappen verworpen tot de privacystatus in opt-in verandert.

   * Doel: Mbox-aanvragen worden verzonden.
   * Audience Manager: Signalen en id-syncs worden verzonden.
   * Waarde in het JSON-configuratiebestand: `optunknown`
   * Waarde in `setPrivacyStatus`: `ADBMobilePrivacyStatusUnknown`

## Voorbeelden {#section_128AC455EE024193B5D4E5A565B53D00}

```objective-c
- (IBAction) setPrivacyOptIn { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn]; 
} 
- (IBAction) setPrivacyOptOut { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptOut]; 
} 
- (IBAction) setPrivacyOptUnknown { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusUnknown]; 
}
```
