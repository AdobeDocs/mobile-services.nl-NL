---
description: Android-widgets kunnen worden bijgehouden met dezelfde methoden als uw app. Widgets delen de toepassingscontext met uw app, zodat de raakvolgorde en de bezoekersidentificatie behouden blijven.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Android-widgets
topic-fix: Developer and implementation
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
exl-id: 229ea987-256a-45f4-a5ca-afe17dd596b8
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Android-widgets {#android-widgets}

Android-widgets kunnen worden bijgehouden met dezelfde methoden als uw app. Widgets delen de toepassingscontext met uw app, zodat de raakvolgorde en de bezoekersidentificatie behouden blijven.

De volgende richtlijnen helpen u bij het volgen van Android-widgets:

* Levenscyclusmetriek niet implementeren ( `startActivity`/ `stopActivity`) roept in de widget.

* Als u wilt bijhouden wanneer een widget aan het beginscherm wordt toegevoegd, voegt u een `trackState` of `trackEvent` de `onEnabled` methode van de widget.

* Als u wilt bijhouden wanneer de app vanuit een widget wordt gestart, voegt u een `trackState` of `trackEvent` aanroep voordat u de intentie maakt om de toepassing te starten.

* Als u de context van een handeling wilt bijhouden, kunt u een `ContextData` variabele die de optie biedt om elke actie afzonderlijk te segmenteren (bijvoorbeeld `AppExperienceType="widget"` vs `app`).
