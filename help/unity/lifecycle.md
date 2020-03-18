---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Levenscyclus implementeren
solution: Marketing Cloud,Developer
title: Levenscyclus implementeren
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Levenscyclus implementeren{#implement-lifecycle}

Zie [Levenscyclusstatistieken in Android](/help/android/metrics.md) of [Levenscyclus in iOS](/help/ios/metrics.md)voor meer informatie over de meetwaarden en afmetingen die automatisch door de mobiele bibliotheek kunnen worden gemeten nadat de levenscyclus is geïmplementeerd.

## iOS

Metrische gegevens over de levenscyclus worden automatisch verzameld in iOS.

## Android

In uw script Unity stelt u de toepassingscontext voor de Android-SDK in. Voeg de volgende code toe aan de `Awake()` functie van de EERSTE scène:

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

Als u levenscyclusmetriek wilt verzamelen, voegt u de volgende code toe aan al uw scènemscripts:

```java
void OnEnable()
 {
  ...
  ADBMobile.CollectLifecycleData (); 
  ...
 }
 
 void OnDisable()
 {
  ...
  ADBMobile.PauseCollectingLifecycleData (); 
  ...
 }
  
 void OnApplicationPause(bool isPaused) 
 {
  ...
  if (isPaused) {
   ADBMobile.PauseCollectingLifecycleData (); 
  }  
  else {
   ADBMobile.CollectLifecycleData(); 
  }
  ...
 }
```

