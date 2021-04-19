---
description: De iOS Adobe Mobile SDK kan naadloos worden geïntegreerd in een Swift-project met de functie Mix en Match in de iOS Developer Library.
seo-description: De iOS Adobe Mobile SDK kan naadloos worden geïntegreerd in een Swift-project met de functie Mix en Match in de iOS Developer Library.
seo-title: Swift-integratie
solution: Experience Cloud,Analytics
title: Swift-integratie
topic-fix: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
exl-id: 3c1a2e28-53b0-4128-a5d9-d2403885098d
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# Snelle integratie {#swift-integration}

De iOS Adobe Mobile SDK kan naadloos worden geïntegreerd in een Swift-project met de functie Mix en Match in de iOS Developer Library.

Zie [Taalinteroperabiliteit](https://developer.apple.com/documentation/swift#2984801.html) voor meer informatie.

Door bijvoorbeeld de headermethode voor overbruggen te gebruiken, zoals beschreven in de documentatie, kunt u het Adobe Mobile iOS SDK-headerbestand importeren:

```
#import “ADBMobile.h”
```

Gebruik de volgende indeling voor toegang tot methoden van de SDK in uw SWIFT-bestanden:

```
ADBMobile.{methodname}
```
