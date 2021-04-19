---
description: Android-widgets kunnen worden bijgehouden met dezelfde methoden als uw app. Widgets delen de toepassingscontext met uw app, zodat de raakvolgorde en de bezoekersidentificatie behouden blijven.
keywords: android;bibliotheek;mobile;sdk
seo-description: Android-widgets kunnen worden bijgehouden met dezelfde methoden als uw app. Widgets delen de toepassingscontext met uw app, zodat de raakvolgorde en de bezoekersidentificatie behouden blijven.
seo-title: Android-widgets
solution: Experience Cloud,Analytics
title: Android-widgets
topic-fix: Developer and implementation
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
exl-id: 229ea987-256a-45f4-a5ca-afe17dd596b8
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Android-widgets {#android-widgets}

Android-widgets kunnen worden bijgehouden met dezelfde methoden als uw app. Widgets delen de toepassingscontext met uw app, zodat de raakvolgorde en de bezoekersidentificatie behouden blijven.

De volgende richtlijnen helpen u bij het volgen van Android-widgets:

* Implementeer geen levenscyclusmetrieaanroepen ( `startActivity`/ `stopActivity`) in de widget.

* Als u wilt bijhouden wanneer een widget aan het beginscherm wordt toegevoegd, voegt u een `trackState`- of `trackEvent`-aanroep toe aan de methode `onEnabled` van de widget.

* Als u wilt bijhouden wanneer de app vanuit een widget wordt gestart, voegt u een `trackState`- of `trackEvent`-aanroep toe voordat u de intent maakt om de toepassing te starten.

* Als u de context van een actie wilt bijhouden, kunt u een variabele `ContextData` definiëren die de optie biedt om elke actie afzonderlijk te segmenteren (bijvoorbeeld `AppExperienceType="widget"` vs. `app`).
