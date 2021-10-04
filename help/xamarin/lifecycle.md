---
description: Informatie die u helpt bij het implementeren van levenscyclusmetriek voor Android. Metrische gegevens over de levenscyclus worden automatisch verzameld voor iOS.
keywords: Xamarine
solution: Experience Cloud
title: Levenscyclus implementeren
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
exl-id: c76e63d1-48a5-4831-85d5-f3d3e9798a43
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 2%

---

# Levenscyclus implementeren {#implement-lifecycle}

Met deze informatie kunt u levenscyclusmetriek voor Android implementeren.

>[!TIP]
>
>Metrische gegevens over de levenscyclus worden automatisch verzameld voor iOS.

Zie [Levenscyclusmetriek](/help/ios/metrics.md) voor de metriek en afmetingen die automatisch door de mobiele bibliotheek kunnen worden gemeten nadat de levenscyclus is geïmplementeerd.

## iOS

In iOS worden levenscyclusgegevens automatisch verzameld.

## Android

Stel in uw hoofdactiviteit de toepassingscontext voor de Android-SDK in.

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

In elke activiteit, voer levenscyclusvraag uit.

```java
protected override void OnResume()
{
    ...
    Config.CollectLifecycleData (this);
    ...
}
protected override void OnPause() 
{
    ...
    Config.PauseCollectingLifecycleData ();
    ...
}
```
