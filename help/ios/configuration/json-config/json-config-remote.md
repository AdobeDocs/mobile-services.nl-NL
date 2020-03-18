---
description: U kunt een ander ADBMobile JSON Config-bestand laden wanneer de toepassing wordt gestart.
seo-description: U kunt een ander ADBMobile JSON Config-bestand laden wanneer de toepassing wordt gestart.
seo-title: Het JSON-configuratiepad voor ADBMobile overschrijven
solution: Marketing Cloud,Analytics
title: Het JSON-configuratiepad voor ADBMobile overschrijven
topic: Developer and implementation
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Het JSON-configuratiepad voor ADBMobile overschrijven {#override-the-adbmobile-json-config-path}

U kunt een ander ADBMobile JSON Config-bestand laden wanneer de toepassing wordt gestart.

Met deze `ADBMobile overrideConfigPath:filePath` methode kunt u het pad naar een ander `ADBMobile.json` configuratiebestand opgeven wanneer de toepassing wordt gestart. Deze methode moet in de `applicationDidFinishLaunchingWithOptions` methode worden aangeroepen en de aanroep moet plaatsvinden vóór elke andere aanroep van Experience Cloud SDK, zoals `collectLifecycleData`.

Wanneer u deze methode aanroept met een ander pad, wordt het configuratiebestand eenmalig overschreven totdat de toepassing wordt gesloten.

Bijvoorbeeld:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```

