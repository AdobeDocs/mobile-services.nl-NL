---
description: Deze informatie helpt u met een GDPR verzoek om gegevens te schrappen.
solution: Experience Cloud Services,Analytics
title: De status van de gebruiker instellen
topic-fix: Developer and implementation
uuid: f8a3e6be-44dd-494e-9cda-dbbac86d6772
exl-id: ef5160ac-5a73-4433-b217-1bd990f8456b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# De status van de gebruiker instellen{#setting-the-user-s-opt-status}

Deze informatie helpt u met een GDPR verzoek om gegevens te schrappen.

>[!IMPORTANT]
>
>Vanaf Android SDK 4.15 stelt u de privacystatus in op `unknown` houdt Audience Manager- en Experience Cloud-id-treffers vast.

U kunt met de volgende instellingen bepalen of de activiteit Analytics, Target en Audience Manager is toegestaan op een apparaat:

* `privacyDefault` in [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md).

   Met deze instelling bepaalt u de begininstelling die blijft bestaan totdat deze wordt gewijzigd in de code.

* De `Config.setPrivacyStatus` methode.

   Nadat u de privacy-instelling met deze methode hebt gewijzigd, blijft deze wijziging van kracht totdat u deze opnieuw wijzigt of wanneer u de app opnieuw verwijdert en installeert. Zie voor meer informatie over de methoden [Configuratiemethoden](/help/android/configuration/methods.md).

In de volgende tabel wordt elke privacystatus beschreven:

* **Aanmelden**

   * **Analyse**: De berichten worden verzonden.
   * **Doel**: Mbox-aanvragen worden verzonden.
   * **Audience Manager**: Signalen en id-syncs worden verzonden.
   * Waarde in het bestand JSON Config: `optedin`
   * Waarde in `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_IN`

* **Weigeren**

   * **Analyse**: Hits worden weggegooid.
   * **Doel**: Mbox-aanvragen zijn niet toegestaan.
   * **Audience Manager**: Signalen en id-syncs zijn niet toegestaan.
   * Waarde in het JSON-configuratiebestand: `optedout`
   * Waarde in `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_OUT`

* **Onbekend**

   * **Analyse**: Indien offline bijhouden **enabled**, worden treffers opgeslagen totdat de status van de privacy verandert in opt-in (hits worden verzonden) of opt-out (hits worden verwijderd).

      Indien offline bijhouden <b>is niet</b> Geactiveerd, worden de klappen verworpen tot de privacystatus in opt-in verandert.
   * **Doel**: Mbox-aanvragen worden verzonden.
   * **Audience Manager**: Signalen en id-syncs worden verzonden.
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
