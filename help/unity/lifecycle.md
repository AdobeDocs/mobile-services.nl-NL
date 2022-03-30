---
description: Metriek en afmetingen meten die automatisch door de mobiele bibliotheek kunnen worden gemeten
keywords: Eenheid
solution: Experience Cloud Services
title: Levenscyclus implementeren
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
exl-id: eca0cebb-6c69-4b0f-b003-c7fc422d0383
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 2%

---

# Levenscyclus implementeren{#implement-lifecycle}

Voor meer informatie over de metriek en afmetingen die automatisch door de mobiele bibliotheek kunnen worden gemeten nadat de levenscyclus is geïmplementeerd, raadpleegt u [Levenscyclusstatistieken in Android](/help/android/metrics.md) of [Levenscyclus in iOS](/help/ios/metrics.md).

## iOS

De levenscycluswaarden worden automatisch verzameld in iOS.

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
