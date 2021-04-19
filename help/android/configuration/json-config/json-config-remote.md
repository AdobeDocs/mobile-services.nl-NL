---
description: U kunt een ander JSON-configuratiebestand voor ADBMobile laden wanneer de toepassing wordt gestart.
seo-description: U kunt een ander JSON-configuratiebestand voor ADBMobile laden wanneer de toepassing wordt gestart.
seo-title: Het pad ADBMobile JSON Config overschrijven
solution: Experience Cloud,Analytics
title: Het pad ADBMobile JSON Config overschrijven
topic-fix: Developer and implementation
uuid: 6872a5d7-0c5a-4fdc-b7bf-ad1534763a6a
exl-id: 6ca8e264-af79-4734-aeb9-824582980953
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# Hef het JSON-configuratiepad voor ADBMobile {#override-the-adbmobile-json-config-path} op

U kunt een ander JSON-configuratiebestand voor ADBMobile laden wanneer de toepassing wordt gestart.

Met de methode `Config.overrideConfigStream(configInput)` kunt u het pad naar een ander `ADBMobile.json`-configuratiebestand opgeven wanneer de toepassing wordt gestart. Deze methode moet worden aangeroepen vóór elke andere aanroep van Experience Cloud-SDK (vóór `Config.collectLifecycleData()`), doorgaans in de methode `onCreate` van uw eerste geladen activiteit.

Als deze methode wordt aangeroepen met een ander pad, wordt het configuratiebestand eenmalig overschreven totdat de toepassing wordt gesloten.

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```
