---
description: Vanaf iOS 10 kunt u met Apple een extensie maken die een zelfstandige extensie wordt genoemd en die u kunt distribueren zonder een omvattende app. Met deze extensie hebt u geen app-groep nodig, omdat er geen app is waarin gegevens kunnen worden gedeeld.
solution: Experience Cloud Services,Analytics
title: Standalone extensie-implementatie
topic-fix: Developer and implementation
uuid: 9b47f082-b78f-4611-968d-014c32ede6bc
exl-id: b51247b6-c4ba-4a00-9ba0-1824450ac067
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Zelfstandige extensie-implementatie {#stand-alone-extension-implementation}

Vanaf iOS 10 kunt u met Apple een extensie maken die een zelfstandige extensie wordt genoemd en die u kunt distribueren zonder een omvattende app. Met deze extensie hebt u geen app-groep nodig, omdat er geen app is waarin gegevens kunnen worden gedeeld.

>[!IMPORTANT]
>
>Als u zelfstandige extensies wilt gebruiken, hebt u Mobile SDK versie 4.13.0 of hoger nodig.

## Vorm uw stand-alone uitbreiding voor gebruik met SDK {#section_B7A84603BB9D4B48BB46BE8D3B9E3CF0}

Uw zelfstandige extensie configureren:

1. Zorg ervoor dat de `ADBMobileConfig.json` is een lid van het doel van uw extensie.
1. Koppel de volgende bibliotheken en frameworks:

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. Stel in de hoofdweergavecontroller van de extensie het extensietype in op `ADBMobileAppExtensionTypeStandAlone` in de SDK voordat enige aan SDK gerelateerde activiteiten worden voltooid.

   ```objective-c
   [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone];
   ```

1. Bevestig dat uw app zonder onverwachte fouten wordt gemaakt.

## Aanvullende opmerkingen {#section_1C9A55E2309A44BF842310F735702B3D}

Hieronder vindt u aanvullende informatie:

* Een extra waarde voor contextgegevens. `a.RunMode` is toegevoegd om aan te geven of de gegevens afkomstig zijn van uw bevattende app of uw extensie:

   * `a.RunMode = Application`

      Deze waarde betekent dat de hit afkomstig is van de bevattende app.
   * `a.RunMode = Extension`

      Deze waarde betekent dat de hit afkomstig is van de extensie.

* Er wordt geen levenscyclusaanroep gestart voor iOS-extensie-apps.
