---
description: Android-widgets kunnen worden bijgehouden met dezelfde methoden als uw app. Widgets delen de toepassingscontext met uw app, zodat de raakvolgorde en de bezoekersidentificatie behouden blijven.
keywords: android;library;mobile;sdk
seo-description: Android-widgets kunnen worden bijgehouden met dezelfde methoden als uw app. Widgets delen de toepassingscontext met uw app, zodat de raakvolgorde en de bezoekersidentificatie behouden blijven.
seo-title: Android-widgets
solution: Experience Cloud,Analytics
title: Android-widgets
topic: Developer and implementation
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# Android-widgets {#android-widgets}

Android-widgets kunnen worden bijgehouden met dezelfde methoden als uw app. Widgets delen de toepassingscontext met uw app, zodat de raakvolgorde en de bezoekersidentificatie behouden blijven.

De volgende richtlijnen helpen u bij het volgen van Android-widgets:

* Implementeer geen levenscyclusmetrieaanroepen ( `startActivity`/ `stopActivity`) in de widget.

* Als u wilt bijhouden wanneer een widget aan het beginscherm wordt toegevoegd, voegt u een `trackState` of `trackEvent` aanroep aan de `onEnabled` methode van de widget toe.

* Als u wilt bijhouden wanneer de app vanuit een widget wordt gestart, voegt u een `trackState` of `trackEvent` aanroep toe voordat u de intentie maakt om de toepassing te starten.

* Als u de context van een actie wilt bijhouden, kunt u een `ContextData` variabele definiëren die de optie biedt om elke actie afzonderlijk te segmenteren (bijvoorbeeld `AppExperienceType="widget"` vs. `app`).

