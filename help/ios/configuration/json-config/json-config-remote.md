---
description: U kunt een ander ADBMobile JSON Config-bestand laden wanneer de toepassing wordt gestart.
solution: Experience Cloud Services,Analytics
title: Het JSON-configuratiepad voor ADBMobile overschrijven
topic-fix: Developer and implementation
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
exl-id: 3a191e9c-905f-4bea-8a6f-5ccf5ea02aff
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 1%

---

# Het JSON-configuratiepad voor ADBMobile overschrijven {#override-the-adbmobile-json-config-path}

U kunt een ander ADBMobile JSON Config-bestand laden wanneer de toepassing wordt gestart.

De `ADBMobile overrideConfigPath:filePath` kunt u een ander pad opgeven `ADBMobile.json` configuratiebestand gebruiken wanneer de toepassing wordt gestart. Deze methode moet worden aangeroepen in het dialoogvenster `applicationDidFinishLaunchingWithOptions` methode, en de vraag moet vóór een andere vraag van Experience Cloud SDK voorkomen, zoals `collectLifecycleData`.

Wanneer u deze methode aanroept met een ander pad, wordt het configuratiebestand eenmalig overschreven totdat de toepassing wordt gesloten.

Bijvoorbeeld:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```
