---
description: U kunt een ander JSON-configuratiebestand voor ADBMobile laden wanneer de toepassing wordt gestart.
seo-description: U kunt een ander JSON-configuratiebestand voor ADBMobile laden wanneer de toepassing wordt gestart.
seo-title: Het pad ADBMobile JSON Config overschrijven
solution: Marketing Cloud,Analytics
title: Het pad ADBMobile JSON Config overschrijven
topic: Developer and implementation
uuid: 6872a5d7-0c5a-4fdc-b7bf-ad1534763a6a
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Het JSON-configuratiepad voor ADBMobile overschrijven {#override-the-adbmobile-json-config-path}

U kunt een ander JSON-configuratiebestand voor ADBMobile laden wanneer de toepassing wordt gestart.

Met deze `Config.overrideConfigStream(configInput)` methode kunt u het pad naar een ander `ADBMobile.json` configuratiebestand opgeven wanneer de toepassing wordt gestart. Deze methode moet worden aangeroepen voordat een andere Experience Cloud SDK-aanroep wordt uitgevoerd (vóór `Config.collectLifecycleData()` ), meestal in de `onCreate` methode van de eerste geladen activiteit.

Als deze methode wordt aangeroepen met een ander pad, wordt het configuratiebestand eenmalig overschreven totdat de toepassing wordt gesloten.

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```

