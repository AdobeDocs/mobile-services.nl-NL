---
description: Met Actief batchverwerking kunnen toepassingen waarvoor offline reeksspatiëring is ingeschakeld, hits bevatten die niet worden verzonden totdat het aantal controles in de wachtrij een configureerbare limiet heeft bereikt.
seo-description: Met Actief batchverwerking kunnen toepassingen waarvoor offline reeksspatiëring is ingeschakeld, hits bevatten die niet worden verzonden totdat het aantal controles in de wachtrij een configureerbare limiet heeft bereikt.
seo-title: Batch
solution: Experience Cloud,Analytics
title: Batch
topic: Developer and implementation
uuid: 3dda7372-0695-4cb7-b779-6abca2d6e0d9
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---


# Batch {#hit-batching}

Met Actief batchverwerking kunnen toepassingen waarvoor offline reeksspatiëring is ingeschakeld, hits bevatten die niet worden verzonden totdat het aantal controles in de wachtrij een configureerbare limiet heeft bereikt.

>[!IMPORTANT]
>
>Voor batchverwerking is SDK versie 4.1 of hoger vereist.

Als u batchverwerking bij treffers wilt inschakelen, werkt u uw `ADBMobileConfig.json` bestand bij en geeft u een waarde op voor `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Wanneer ingesteld op een getal hoger dan 0, plaatst de SDK het aantal hits gelijk aan *`batchLimit`*. Nadat deze drempel is bereikt, worden alle treffers in de wachtrij verzonden.

De volgende methoden worden gebruikt voor batchverwerking:

* `trackingGetQueueSize()` geeft een resultaat `NSUInteger` met het aantal treffers dat zich momenteel in de wachtrij bevindt.
* `trackingSendQueuedHits()` Hiermee dwingt u de bibliotheek alle resultaten in de wachtrij te verzenden, ongeacht het aantal dat momenteel in de wachtrij staat.
* `trackingClearQueue()` Hiermee wist u alle resultaten van de wachtrij zonder deze te verzenden.

>[!CAUTION]
>
>Offline bijhouden moet zijn ingeschakeld om batchverwerking te kunnen gebruiken.

