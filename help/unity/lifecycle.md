---
description: Metriek en afmetingen meten die automatisch door de mobiele bibliotheek kunnen worden gemeten
keywords: Eenheid
solution: Experience Cloud
title: Levenscyclus implementeren
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
exl-id: eca0cebb-6c69-4b0f-b003-c7fc422d0383
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 2%

---

# Levenscyclus implementeren{#implement-lifecycle}

Zie [Levenscyclusmetriek in Android](/help/android/metrics.md) of [Levenscyclus in iOS](/help/ios/metrics.md) voor meer informatie over de metriek en afmetingen die automatisch door de mobiele bibliotheek kunnen worden gemeten nadat de levenscyclus is geïmplementeerd.

## iOS

Metrische gegevens over de levenscyclus worden automatisch verzameld in iOS.

## Android

In uw script Unity stelt u de toepassingscontext voor de Android-SDK in. Voeg de volgende code toe aan de functie `Awake()` van de EERSTE scène:

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
