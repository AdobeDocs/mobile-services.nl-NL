---
description: U kunt een ander JSON-configuratiebestand voor ADBMobile laden wanneer de toepassing wordt gestart.
solution: Experience Cloud Services,Analytics
title: Het pad ADBMobile JSON Config overschrijven
topic-fix: Developer and implementation
uuid: 6872a5d7-0c5a-4fdc-b7bf-ad1534763a6a
exl-id: 6ca8e264-af79-4734-aeb9-824582980953
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Het JSON-configuratiepad voor ADBMobile overschrijven {#override-the-adbmobile-json-config-path}

U kunt een ander JSON-configuratiebestand voor ADBMobile laden wanneer de toepassing wordt gestart.

De `Config.overrideConfigStream(configInput)` kunt u een ander pad opgeven `ADBMobile.json` configuratiebestand gebruiken wanneer de toepassing wordt gestart. Deze methode moet worden aangeroepen vóór elke andere aanroep van Experience Cloud SDK (vóór `Config.collectLifecycleData()` ), doorgaans in de `onCreate` methode van uw eerste geladen activiteit.

Als deze methode wordt aangeroepen met een ander pad, wordt het configuratiebestand eenmalig overschreven totdat de toepassing wordt gesloten.

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```
