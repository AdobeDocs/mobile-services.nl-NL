---
description: Het slaan van het haar staat toepassingen toe om klappen te houden van worden verzonden tot het aantal klappen in de rij de gevormde grens hebben overschreden.
keywords: android;library;mobile;sdk
seo-description: Het slaan van het haar staat toepassingen toe om klappen te houden van worden verzonden tot het aantal klappen in de rij de gevormde grens hebben overschreden.
seo-title: Batch gebruiken
solution: Experience Cloud,Analytics
title: Batch gebruiken
topic: Developer and implementation
uuid: ada35be3-242b-4b2b-a828-9bf998dd58b5
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# Batch {#hit-batching}

Het slaan van het haar staat toepassingen toe om klappen te houden van worden verzonden tot het aantal klappen in de rij de gevormde grens hebben overschreden.

>[!IMPORTANT]
>
>Als u batchverwerking wilt gebruiken, **moet** u offline bijhouden inschakelen en SDK versie 4.1 of hoger gebruiken

Als u batchverwerking bij treffers wilt inschakelen, werkt u uw `ADBMobileConfig.json` bestand bij en geeft u een waarde op voor `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Wanneer de waarde op een getal groter dan 0 is ingesteld, plaatst de SDK het aantal hits in de wachtrij dat gelijk is aan de *`batchLimit`* waarde. Nadat deze drempel is bereikt, worden alle treffers in de wachtrij verzonden.

De volgende methoden worden gebruikt voor batchverwerking:

* `Analytics.getQueueSize` geeft een resultaat `long` met het aantal treffers dat zich momenteel in de wachtrij met batchgegevens bevindt.

* `Analytics.sendQueuedHits` Hiermee dwingt u de bibliotheek alle treffers in de wachtrij te verzenden, ongeacht het aantal treffers dat momenteel in de wachtrij wordt geplaatst.
* `Analytics.clearQueue` Hiermee wist u alle resultaten van de wachtrij zonder deze te verzenden.
