---
description: Met Actief batchverwerking kunnen toepassingen waarvoor offline reeksspatiëring is ingeschakeld, hits bevatten die niet worden verzonden totdat het aantal controles in de wachtrij een configureerbare limiet heeft bereikt.
seo-description: Met Actief batchverwerking kunnen toepassingen waarvoor offline reeksspatiëring is ingeschakeld, hits bevatten die niet worden verzonden totdat het aantal controles in de wachtrij een configureerbare limiet heeft bereikt.
seo-title: Batch
solution: Experience Cloud,Analytics
title: Batch
topic-fix: Developer and implementation
uuid: 3dda7372-0695-4cb7-b779-6abca2d6e0d9
exl-id: af21f435-13cb-4353-9fbb-c99274bce411
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---

# Batch {#hit-batching}

Met Actief batchverwerking kunnen toepassingen waarvoor offline reeksspatiëring is ingeschakeld, hits bevatten die niet worden verzonden totdat het aantal controles in de wachtrij een configureerbare limiet heeft bereikt.

>[!IMPORTANT]
>
>Voor batchverwerking is SDK versie 4.1 of hoger vereist.

Als u batchverwerking bij raakbewegingen wilt inschakelen, werkt u het `ADBMobileConfig.json`-bestand bij en geeft u een waarde op voor `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Wanneer ingesteld op een getal hoger dan 0, plaatst de SDK het aantal hits gelijk aan *`batchLimit`* in de wachtrij. Nadat deze drempel is bereikt, worden alle treffers in de wachtrij verzonden.

De volgende methoden worden gebruikt voor batchverwerking:

* `trackingGetQueueSize()` retourneert een  `NSUInteger` met het aantal treffers dat momenteel in de wachtrij met batchgegevens voorkomt.
* `trackingSendQueuedHits()` Hiermee dwingt u de bibliotheek alle resultaten in de wachtrij te verzenden, ongeacht het aantal dat momenteel in de wachtrij staat.
* `trackingClearQueue()` Hiermee wist u alle resultaten van de wachtrij zonder deze te verzenden.

>[!CAUTION]
>
>Offline bijhouden moet zijn ingeschakeld om batchverwerking te kunnen gebruiken.
