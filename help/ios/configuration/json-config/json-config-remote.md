---
description: U kunt een ander ADBMobile JSON Config-bestand laden wanneer de toepassing wordt gestart.
seo-description: U kunt een ander ADBMobile JSON Config-bestand laden wanneer de toepassing wordt gestart.
seo-title: Het JSON-configuratiepad voor ADBMobile overschrijven
solution: Experience Cloud,Analytics
title: Het JSON-configuratiepad voor ADBMobile overschrijven
topic-fix: Developer and implementation
uuid: 0d1be674-c634-4a48-aa31-5701681911b9
exl-id: 3a191e9c-905f-4bea-8a6f-5ccf5ea02aff
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 1%

---

# Hef het JSON-configuratiepad voor ADBMobile {#override-the-adbmobile-json-config-path} op

U kunt een ander ADBMobile JSON Config-bestand laden wanneer de toepassing wordt gestart.

Met de methode `ADBMobile overrideConfigPath:filePath` kunt u het pad naar een ander `ADBMobile.json`-configuratiebestand opgeven wanneer de toepassing wordt gestart. Deze methode moet in de `applicationDidFinishLaunchingWithOptions` methode worden geroepen, en de vraag moet vóór een andere vraag van Experience Cloud SDK, zoals `collectLifecycleData` voorkomen.

Wanneer u deze methode aanroept met een ander pad, wordt het configuratiebestand eenmalig overschreven totdat de toepassing wordt gesloten.

Bijvoorbeeld:

```objective-c
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile" ofType:@"json"]; 
[ADBMobile overrideConfigPath:filePath];
```
