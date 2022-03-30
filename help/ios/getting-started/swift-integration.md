---
description: De iOS Adobe Mobile SDK kan naadloos worden geïntegreerd in een Swift-project met de functie Mix en Match in de iOS Developer Library.
solution: Experience Cloud Services,Analytics
title: Swift-integratie
topic-fix: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
exl-id: 3c1a2e28-53b0-4128-a5d9-d2403885098d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# Swift-integratie {#swift-integration}

De iOS Adobe Mobile SDK kan naadloos worden geïntegreerd in een Swift-project met de functie Mix en Match in de iOS Developer Library.

Zie voor meer informatie [Taalinteroperabiliteit](https://developer.apple.com/documentation/swift#2984801.html).

Door bijvoorbeeld de headermethode voor overbruggen te gebruiken, zoals beschreven in de documentatie, kunt u het Adobe Mobile SDK-headerbestand importeren:

```
#import "ADBMobile.h"
```

Gebruik de volgende indeling voor toegang tot methoden van de SDK in uw SWIFT-bestanden:

```
ADBMobile.{methodname}
```
