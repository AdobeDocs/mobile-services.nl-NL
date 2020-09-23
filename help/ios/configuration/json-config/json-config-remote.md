---
description: U kunt een ander ADBMobile JSON Config-bestand laden wanneer de toepassing wordt gestart.
seo-description: U kunt een ander ADBMobile JSON Config-bestand laden wanneer de toepassing wordt gestart.
seo-title: Het JSON-configuratiepad voor ADBMobile overschrijven
solution: Experience Cloud,Analytics
title: Het JSON-configuratiepad voor ADBMobile overschrijven
topic: Developer and implementation
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 1%

---


# Het JSON-configuratiepad voor ADBMobile overschrijven {#override-the-adbmobile-json-config-path}

U kunt een ander ADBMobile JSON Config-bestand laden wanneer de toepassing wordt gestart.

Met deze `ADBMobile overrideConfigPath:filePath` methode kunt u het pad naar een ander `ADBMobile.json` configuratiebestand opgeven wanneer de toepassing wordt gestart. Deze methode moet in de `applicationDidFinishLaunchingWithOptions` methode worden geroepen, en de vraag moet vóór een andere vraag van Experience Cloud SDK, zoals `collectLifecycleData`voorkomen.

Wanneer u deze methode aanroept met een ander pad, wordt het configuratiebestand eenmalig overschreven totdat de toepassing wordt gesloten.

Bijvoorbeeld:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

