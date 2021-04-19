---
description: Het slaan van het haar staat toepassingen toe om klappen te houden van worden verzonden tot het aantal klappen in de rij de gevormde grens hebben overschreden.
keywords: android;bibliotheek;mobile;sdk
seo-description: Het slaan van het haar staat toepassingen toe om klappen te houden van worden verzonden tot het aantal klappen in de rij de gevormde grens hebben overschreden.
seo-title: Batch gebruiken
solution: Experience Cloud,Analytics
title: Batch gebruiken
topic-fix: Developer and implementation
uuid: ada35be3-242b-4b2b-a828-9bf998dd58b5
exl-id: 74147f09-52fc-46dc-b4dd-2bf60b039f6e
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# Batch {#hit-batching}

Het slaan van het haar staat toepassingen toe om klappen te houden van worden verzonden tot het aantal klappen in de rij de gevormde grens hebben overschreden.

>[!IMPORTANT]
>
>Als u batchverwerking wilt gebruiken, **must** schakelt u offline bijhouden in en hebt u SDK-versie 4.1 of hoger

Als u batchverwerking bij raakbewegingen wilt inschakelen, werkt u het `ADBMobileConfig.json`-bestand bij en geeft u een waarde op voor `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Wanneer de waarde op een getal groter dan 0 wordt ingesteld, plaatst de SDK het aantal hits in de wachtrij dat gelijk is aan de waarde *`batchLimit`*. Nadat deze drempel is bereikt, worden alle treffers in de wachtrij verzonden.

De volgende methoden worden gebruikt voor batchverwerking:

* `Analytics.getQueueSize` geeft een resultaat  `long` met het aantal treffers dat zich momenteel in de wachtrij met batchgegevens bevindt.

* `Analytics.sendQueuedHits` Hiermee dwingt u de bibliotheek alle treffers in de wachtrij te verzenden, ongeacht het aantal treffers dat momenteel in de wachtrij wordt geplaatst.
* `Analytics.clearQueue` Hiermee wist u alle resultaten van de wachtrij zonder deze te verzenden.
