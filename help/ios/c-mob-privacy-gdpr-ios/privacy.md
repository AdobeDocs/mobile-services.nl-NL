---
description: Deze informatie helpt u met een GDPR verzoek om gegevens te schrappen.
seo-description: Deze informatie helpt u met een GDPR verzoek om gegevens te schrappen.
seo-title: De status Opt van de gebruiker instellen
solution: Marketing Cloud,Analytics
title: De status Opt van de gebruiker instellen
topic: Developer and implementation
uuid: 44a09a25-93c6-4e1a-b69e-710018e8b6c3
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# De status van de gebruiker instellen {#setting-the-user-s-opt-status}

Deze informatie helpt u met een GDPR verzoek om gegevens te schrappen.

>[!IMPORTANT]
>
>Vanaf Experience Cloud iOS SDK&#39;s 4.15 kunt u de privacystatus zo instellen dat Audience Manager en Experience Cloud ID-resultaten `unknown` behouden blijven.

U kunt controleren of de activiteit van de Manager van de Analyse, van het Doel, en van de Audience op een apparaat door de volgende montages te gebruiken wordt toegestaan:

* `privacyDefault` in [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md).

   Met deze instelling bepaalt u de begininstelling die blijft bestaan totdat deze in de code wordt gewijzigd.

* `setPrivacyStatus` methode.

   Nadat de privacy-instelling met deze methode is gewijzigd, is de wijziging permanent totdat deze opnieuw wordt gewijzigd met deze methode, of wanneer u de app opnieuw verwijdert en installeert.

   Voor meer informatie over de methodes, zie de Methoden [van de](/help/ios/configuration/json-config/json-config.md)Configuratie.

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

   * Analyse: Als offline bijhouden **is** ingeschakeld, worden treffers opgeslagen totdat de privacystatus verandert in aanmelden (treffers worden verzonden) of Afmelden (treffers worden verwijderd).

      Als offline bijhouden **niet** is ingeschakeld, worden treffers genegeerd totdat de privacystatus verandert in aanmelden.

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
