---
description: Met Postbacks kunt u gegevens die door de SDK zijn verzameld, naar een externe server verzenden. Door gebruik te maken van dezelfde triggers en kenmerken die u gebruikt om een bericht in de app weer te geven, kunt u de SDK zodanig configureren dat aangepaste gegevens naar een bestemming van een derde worden verzonden.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud,Analytics
title: Overzicht van postbacks
topic-fix: Developer and implementation
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
exl-id: 318f6eab-ff71-4bfe-8eb7-51a35380b992
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Postbacks {#postbacks}

Met Postbacks kunt u gegevens die door de SDK zijn verzameld, naar een externe server verzenden. Door gebruik te maken van dezelfde triggers en kenmerken die u gebruikt om een bericht in de app weer te geven, kunt u de SDK zodanig configureren dat aangepaste gegevens naar een bestemming van een derde worden verzonden.

>[!IMPORTANT]
>
>Voor deze functionaliteit is SDK-versie 4.6.0 of hoger vereist.

Postbackberichten worden in een wachtrij geplaatst en volgen alle bestaande online/offline regels die de gegevensverzameling van analysegegevens regelen. Wanneer een bericht aanpast (als getoond-berichten), annuleert de postbackberichten niet de rest van de berichten. Op deze manier kunnen meerdere postbacks optreden bij dezelfde hit voor analysemogelijkheden. Voor de definitie, zie *postbacks* rij in [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md).

## Sjabloonuitbreidingen {#section_6758AD05A24C4E9E965F5253294C164A}

Sjabloonuitbreidingen zijn beschikbaar in de eigenschappen `templateurl` en `templatebody`. Sjabloonitems hebben de vorm van `{key}`, waarbij `key` een contextgegevenssleutel of een traditionele gegevenssleutel is. De waarden die voor malplaatjeuitbreiding beschikbaar zijn zijn beperkt tot [De metriek van de Levenscyclus](/help/android/metrics.md), naast om het even welke douanegegevens die aan slag in bijlage zijn die het bericht teweegbrengt. Er zijn momenteel geen historische of op een segment gebaseerde gegevens beschikbaar.

Er zijn ook specifieke, gereserveerde sjablonen die de SDK automatisch vervangt door interne gegevens die bekend zijn bij de SDK.

Deze lijst bevat:

| Tokennaam | Beschrijving van token |
|--- |--- |
| {%sdkver%} | Retourneert de SDK-versie. |
| {%cachebust%} | Hiermee wordt een willekeurig getal tussen 1 en 100000000 ingesteld. |
| {%adid%} | Retourneert Advertiser-id voor Android. Opmerking: dit werkt alleen als u `submitAdvertisingIdentifierTask` hebt gebruikt. |
| {%pushID%} | Retourneert het token voor de push-id. Opmerking: dit werkt alleen als u `setPushIdentifier` hebt gebruikt. |
| {%timestampu%} | Retourneert de huidige tijdstempel in tijdperk. |
| {%timestampz%} | Hiermee wordt de huidige tijdstempel geretourneerd in de JavaScript-indeling (ISO 8601). |
