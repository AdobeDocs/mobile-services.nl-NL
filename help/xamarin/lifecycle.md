---
description: Informatie die u helpt bij het implementeren van levenscyclusmetriek voor Android. Metrische gegevens over de levenscyclus worden automatisch verzameld voor iOS.
keywords: Xamarin
seo-description: Informatie die u helpt bij het implementeren van levenscyclusmetriek voor Android. Metrische gegevens over de levenscyclus worden automatisch verzameld voor iOS.
seo-title: Levenscyclus implementeren
solution: Marketing Cloud,Developer
title: Levenscyclus implementeren
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Levenscyclus implementeren {#implement-lifecycle}

Met deze informatie kunt u levenscyclusmetriek voor Android implementeren.

>[!TIP]
>
>Metrische gegevens over de levenscyclus worden automatisch verzameld voor iOS.

Zie Metriek van [levenscyclus voor de metriek en afmetingen die automatisch door de mobiele bibliotheek kunnen worden gemeten nadat de levenscyclus is geïmplementeerd](/help/ios/metrics.md).

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
