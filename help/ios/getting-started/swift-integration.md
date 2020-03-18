---
description: De iOS Adobe Mobile SDK kan naadloos worden geïntegreerd in een Swift-project met behulp van de functie Mix en Match in de iOS Developer Library.
seo-description: De iOS Adobe Mobile SDK kan naadloos worden geïntegreerd in een Swift-project met behulp van de functie Mix en Match in de iOS Developer Library.
seo-title: Swift-integratie
solution: Marketing Cloud,Analytics
title: Swift-integratie
topic: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Swift-integratie {#swift-integration}

De iOS Adobe Mobile SDK kan naadloos worden geïntegreerd in een Swift-project met behulp van de functie Mix en Match in de iOS Developer Library.

Zie [Taalinteroperabiliteit](https://developer.apple.com/documentation/swift#2984801.html)voor meer informatie.

Door bijvoorbeeld de headermethode voor overbruggen te gebruiken, zoals beschreven in de documentatie, kunt u het Adobe Mobile iOS SDK-headerbestand importeren:

```
#import “ADBMobile.h”
```

Gebruik de volgende indeling voor toegang tot methoden van de SDK in uw SWIFT-bestanden:

```
ADBMobile.{methodname}
```

