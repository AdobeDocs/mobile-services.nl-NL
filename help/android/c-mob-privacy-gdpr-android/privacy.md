---
description: Deze informatie helpt u met een GDPR verzoek om gegevens te schrappen.
seo-description: Deze informatie helpt u met een GDPR verzoek om gegevens te schrappen.
seo-title: De status van de gebruiker instellen
solution: Marketing Cloud,Analytics
title: De status van de gebruiker instellen
topic: Developer and implementation
uuid: f8a3e6be-44dd-494e-9cda-dbbac86d6772
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# De status van de gebruiker instellen{#setting-the-user-s-opt-status}

Deze informatie helpt u met een GDPR verzoek om gegevens te schrappen.

>[!IMPORTANT]
>
>Vanaf Android SDK 4.15 kunt u de privacystatus zo instellen dat Audience Manager en Experience Cloud ID-resultaten worden `unknown` opgeslagen.

U kunt met de volgende instellingen bepalen of de activiteit Analytics, Target en Audience Manager is toegestaan op een apparaat:

* `privacyDefault` in [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md).

   Met deze instelling bepaalt u de begininstelling die blijft bestaan totdat deze wordt gewijzigd in de code.

* De `Config.setPrivacyStatus` methode.

   Nadat u de privacy-instelling met deze methode hebt gewijzigd, blijft deze wijziging van kracht totdat u deze opnieuw wijzigt of wanneer u de app opnieuw verwijdert en installeert. Voor meer informatie over de methodes, zie de Methoden [van de](/help/android/configuration/methods.md)Configuratie.

In de volgende tabel wordt elke privacystatus beschreven:

* **Aanmelden**

   * **Analyse**: De berichten worden verzonden.
   * **Doel**: Mbox-aanvragen worden verzonden.
   * **Poortbeheer**: Signalen en id-syncs worden verzonden.
   * Waarde in het bestand JSON Config: `optedin`
   * Waarde in `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_IN`

* **Weigeren**

   * **Analyse**: Hits worden weggegooid.
   * **Doel**: Mbox-aanvragen zijn niet toegestaan.
   * **Poortbeheer**: Signalen en id-syncs zijn niet toegestaan.
   * Waarde in het JSON-configuratiebestand: `optedout`
   * Waarde in `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_OUT`

* **Onbekend**

   * **Analyse**: Als offline bijhouden is **ingeschakeld**, worden treffers opgeslagen totdat de privacystatus verandert in aanmelden (treffers worden verzonden) of Afmelden (treffers worden verwijderd).

      Als offline bijhouden <b>niet</b> is ingeschakeld, worden treffers genegeerd totdat de privacystatus verandert in aanmelden.
   * **Doel**: Mbox-aanvragen worden verzonden.
   * **Poortbeheer**: Signalen en id-syncs worden verzonden.
   * Waarde in het JSON-configuratiebestand: `optunknown`
   * Waarde in `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_UNKNOWN`

## Voorbeelden {#section_128AC455EE024193B5D4E5A565B53D00}

```java
public void setOptIn(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptOut(View view) { 
 Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_OUT); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptUnknown(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_UNKNOWN); 
 currentStatus = Config.getPrivacyStatus(); 
}
```

