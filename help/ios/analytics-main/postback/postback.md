---
description: Met Postbacks kunt u gegevens die door de SDK zijn verzameld, naar een externe server verzenden. Door gebruik te maken van dezelfde triggers en kenmerken die u gebruikt om een bericht in de app weer te geven, kunt u de SDK zodanig configureren dat aangepaste gegevens naar een bestemming van een derde worden verzonden.
solution: Experience Cloud,Analytics
title: Overzicht van postbacks
uuid: 25e2a5fb-1203-40dd-96cd-b23e0f23376d
exl-id: c5aa0b99-2cb3-4dd7-9da8-e573241e864b
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Overzicht van postbacks {#postbacks}

Met Postbacks kunt u gegevens die door de SDK zijn verzameld, naar een externe server verzenden. Door gebruik te maken van dezelfde triggers en kenmerken die u gebruikt om een bericht in de app weer te geven, kunt u de SDK zodanig configureren dat aangepaste gegevens naar een bestemming van een derde worden verzonden.

>[!IMPORTANT]
>
>Voor deze functionaliteit is SDK-versie 4.6.0 of hoger vereist.

Postbackberichten worden in een wachtrij geplaatst en volgen alle bestaande online/offline regels die de gegevensverzameling van analysegegevens regelen. Wanneer een bericht aanpast (als getoond-berichten), annuleert de postbackberichten niet de rest van de berichten. Op deze manier kunnen meerdere postbacks optreden bij dezelfde hit voor analysemogelijkheden. Voor de definitie, zie *postbacks* rij in [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md).

## Sjabloonuitbreidingen {#section_6758AD05A24C4E9E965F5253294C164A}

Sjabloonuitbreidingen zijn zowel in de eigenschappen `templateurl` als `templatebody` beschikbaar. Sjabloonitems hebben de vorm van `{key}`, waarbij `key` een contextgegevenssleutel of een traditionele gegevenssleutel is. De waarden beschikbaar voor malplaatjeverhoging zijn beperkt tot [standaardLijst van de variabelen van de Levenscyclus ](/help/ios/metrics.md), naast om het even welke douanegegevens in bijlage aan slag die het bericht teweegbrengt. Op dit moment zijn er geen gegevens op basis van historie of segment beschikbaar.

Er zijn ook specifieke, gereserveerde sjablonen die de SDK automatisch vervangt door interne gegevens die bekend zijn bij de SDK.

Deze lijst bevat:

| Tokennaam | Beschrijving van token |
|--- |--- |
| `{%sdkver%}` | Retourneert de SDK-versie. |
| `{%cachebust%}` | Hiermee wordt een willekeurig getal tussen 1 en 100000000 ingesteld. |
| `{%adid%}` | Retourneert IDFA. Dit token werkt alleen als u `setAdvertisingIdentifier` hebt gebruikt. |
| `{%pushid%}` | Retourneert het token voor de push-id. Dit token werkt alleen als u `setPushIdentifier` hebt gebruikt. |
| `{%timestampu%}` | Retourneert de huidige tijdstempel in tijdperk. |
| `{%timestampz%}` | Hiermee wordt de huidige tijdstempel geretourneerd in de JavaScript-indeling (ISO 8601). |
