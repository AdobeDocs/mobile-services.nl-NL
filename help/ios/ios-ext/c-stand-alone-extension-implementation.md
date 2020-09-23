---
description: Vanaf iOS 10 kunt u met Apple een extensie maken die een zelfstandige extensie wordt genoemd en die u kunt distribueren zonder een omvattende app. Met deze extensie hebt u geen app-groep nodig, omdat er geen app is waarin gegevens kunnen worden gedeeld.
seo-description: Vanaf iOS 10 kunt u met Apple een extensie maken die een zelfstandige extensie wordt genoemd en die u kunt distribueren zonder een omvattende app. Met deze extensie hebt u geen app-groep nodig, omdat er geen app is waarin gegevens kunnen worden gedeeld.
seo-title: Standalone extensie-implementatie
solution: Experience Cloud,Analytics
title: Standalone extensie-implementatie
topic: Developer and implementation
uuid: 9b47f082-b78f-4611-968d-014c32ede6bc
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---


# Zelfstandige extensie-implementatie {#stand-alone-extension-implementation}

Vanaf iOS 10 kunt u met Apple een extensie maken die een zelfstandige extensie wordt genoemd en die u kunt distribueren zonder een omvattende app. Met deze extensie hebt u geen app-groep nodig, omdat er geen app is waarin gegevens kunnen worden gedeeld.

>[!IMPORTANT]
>
>Als u zelfstandige extensies wilt gebruiken, moet u beschikken over Mobile SDK versie 4.13.0 of hoger.

## Vorm uw stand-alone uitbreiding voor gebruik met SDK {#section_B7A84603BB9D4B48BB46BE8D3B9E3CF0}

Uw zelfstandige extensie configureren:

1. Zorg ervoor dat het `ADBMobileConfig.json` bestand lid is van het doel van de extensie.
1. Koppel de volgende bibliotheken en frameworks:

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. Stel in de hoofdweergavecontroller van de extensie het extensietype in de SDK in voordat u SDK-gerelateerde activiteiten voltooit. `ADBMobileAppExtensionTypeStandAlone`

   ```objective-c
   [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone];
   ```

1. Bevestig dat uw app zonder onverwachte fouten wordt gemaakt.

## Aanvullende opmerkingen {#section_1C9A55E2309A44BF842310F735702B3D}

Hieronder vindt u aanvullende informatie:

* Er `a.RunMode` is een extra waarde voor contextgegevens toegevoegd om aan te geven of de gegevens afkomstig zijn van de bevattende app of van uw extensie:

   * `a.RunMode = Application`

      Deze waarde betekent dat de hit afkomstig is van de bevattende app.
   * `a.RunMode = Extension`

      Deze waarde betekent dat de hit afkomstig is van de extensie.

* Er wordt geen levenscyclusaanroep gestart voor iOS-extensie-apps.

