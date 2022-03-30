---
description: Het slaan van het haar staat toepassingen toe om klappen te houden van worden verzonden tot het aantal klappen in de rij de gevormde grens hebben overschreden.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Batch gebruiken
topic-fix: Developer and implementation
uuid: ada35be3-242b-4b2b-a828-9bf998dd58b5
exl-id: 74147f09-52fc-46dc-b4dd-2bf60b039f6e
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---

# Batch {#hit-batching}

Het slaan van het haar staat toepassingen toe om klappen te houden van worden verzonden tot het aantal klappen in de rij de gevormde grens hebben overschreden.

>[!IMPORTANT]
>
>Als u een batchverwerking wilt gebruiken, **moet** offline bijhouden inschakelen en SDK versie 4.1 of hoger gebruiken

Als u batchverwerking voor treffers wilt inschakelen, werkt u uw `ADBMobileConfig.json` en geef een waarde op voor `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Wanneer de waarde op een getal groter dan 0 wordt ingesteld, plaatst de SDK het aantal hits in de wachtrij dat gelijk is aan het aantal *`batchLimit`* waarde. Nadat deze drempel is bereikt, worden alle treffers in de wachtrij verzonden.

De volgende methoden worden gebruikt voor batchverwerking:

* `Analytics.getQueueSize` retourneert een `long` met het aantal treffers dat momenteel in de rij van de raakpartij is.

* `Analytics.sendQueuedHits` Hiermee dwingt u de bibliotheek alle treffers in de wachtrij te verzenden, ongeacht het aantal treffers dat momenteel in de wachtrij wordt geplaatst.
* `Analytics.clearQueue` Hiermee wist u alle resultaten van de wachtrij zonder deze te verzenden.
