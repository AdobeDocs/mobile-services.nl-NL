---
description: Met Postbacks kunt u gegevens die door de SDK zijn verzameld, naar een externe server verzenden. Door gebruik te maken van dezelfde triggers en kenmerken die u gebruikt om een bericht in de app weer te geven, kunt u de SDK zodanig configureren dat aangepaste gegevens naar een bestemming van een derde worden verzonden.
seo-description: Met Postbacks kunt u gegevens die door de SDK zijn verzameld, naar een externe server verzenden. Door gebruik te maken van dezelfde triggers en kenmerken die u gebruikt om een bericht in de app weer te geven, kunt u de SDK zodanig configureren dat aangepaste gegevens naar een bestemming van een derde worden verzonden.
seo-title: Postbacks
solution: Experience Cloud,Analytics
title: Overzicht van postbacks
uuid: 25e2a5fb-1203-40dd-96cd-b23e0f23376d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---


# Overzicht van postbacks {#postbacks}

Met Postbacks kunt u gegevens die door de SDK zijn verzameld, naar een externe server verzenden. Door gebruik te maken van dezelfde triggers en kenmerken die u gebruikt om een bericht in de app weer te geven, kunt u de SDK zodanig configureren dat aangepaste gegevens naar een bestemming van een derde worden verzonden.

>[!IMPORTANT]
>
>Voor deze functionaliteit is SDK-versie 4.6.0 of hoger vereist.

Postbackberichten worden in een wachtrij geplaatst en volgen alle bestaande online/offline regels die de gegevensverzameling van analysegegevens regelen. Wanneer een bericht aanpast (als getoond-berichten), annuleert de postbackberichten niet de rest van de berichten. Op deze manier kunnen meerdere postbacks optreden bij dezelfde hit voor analysemogelijkheden. Voor de definitie, zie de *postbacks* rij in [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md).

## Sjabloonuitbreidingen {#section_6758AD05A24C4E9E965F5253294C164A}

Sjabloonuitbreidingen zijn zowel in de `templateurl` eigenschappen als in de `templatebody` eigenschappen beschikbaar. Sjabloonitems hebben de vorm van `{key}`, waar `key` een contextgegevenssleutel of een traditionele gegevenssleutel staat. De waarden beschikbaar voor malplaatjeuitbreiding zijn beperkt tot de [standaardlijst](/help/ios/metrics.md)van de variabelen van de Levenscyclus, naast om het even welke douanegegevens in bijlage aan slag die het bericht teweegbrengt. Op dit moment zijn er geen gegevens op basis van historie of segment beschikbaar.

Er zijn ook specifieke, gereserveerde sjablonen die de SDK automatisch vervangt door interne gegevens die bekend zijn bij de SDK.

Deze lijst bevat:

| Tokennaam | Beschrijving van token |
|--- |--- |
| `{%sdkver%}` | Retourneert de SDK-versie. |
| `{%cachebust%}` | Hiermee wordt een willekeurig getal tussen 1 en 100000000 ingesteld. |
| `{%adid%}` | Retourneert IDFA. Deze token werkt alleen als u deze gebruikt `setAdvertisingIdentifier`. |
| `{%pushid%}` | Retourneert het token voor de push-id. Deze token werkt alleen als u deze gebruikt `setPushIdentifier`. |
| `{%timestampu%}` | Retourneert de huidige tijdstempel in tijdperk. |
| `{%timestampz%}` | Hiermee wordt de huidige tijdstempel geretourneerd in de JavaScript-indeling (ISO 8601). |