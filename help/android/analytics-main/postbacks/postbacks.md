---
description: Met Postbacks kunt u gegevens die door de SDK zijn verzameld, naar een externe server verzenden. Door gebruik te maken van dezelfde triggers en kenmerken die u gebruikt om een bericht in de app weer te geven, kunt u de SDK zodanig configureren dat aangepaste gegevens naar een bestemming van een derde worden verzonden.
keywords: android;library;mobile;sdk
seo-description: Met Postbacks kunt u gegevens die door de SDK zijn verzameld, naar een externe server verzenden. Door gebruik te maken van dezelfde triggers en kenmerken die u gebruikt om een bericht in de app weer te geven, kunt u de SDK zodanig configureren dat aangepaste gegevens naar een bestemming van een derde worden verzonden.
seo-title: Postbacks
solution: Marketing Cloud,Analytics
title: Overzicht van postbacks
topic: Developer and implementation
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
translation-type: tm+mt
source-git-commit: f26dcd5cf9b19de49c9d034c854d9738c7843fb2

---


# Postbacks {#postbacks}

Met Postbacks kunt u gegevens die door de SDK zijn verzameld, naar een externe server verzenden. Door gebruik te maken van dezelfde triggers en kenmerken die u gebruikt om een bericht in de app weer te geven, kunt u de SDK zodanig configureren dat aangepaste gegevens naar een bestemming van een derde worden verzonden.

>[!IMPORTANT]
>
>Voor deze functionaliteit is SDK-versie 4.6.0 of hoger vereist.

Postbackberichten worden in een wachtrij geplaatst en volgen alle bestaande online/offline regels die de gegevensverzameling van analysegegevens regelen. Wanneer een bericht aanpast (als getoond-berichten), annuleert de postbackberichten niet de rest van de berichten. Op deze manier kunnen meerdere postbacks optreden bij dezelfde hit voor analysemogelijkheden. Voor de definitie, zie de *postbacks* rij in [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md).

## Sjabloonuitbreidingen {#section_6758AD05A24C4E9E965F5253294C164A}

Sjabloonuitbreidingen zijn beschikbaar in de `templateurl` eigenschappen en `templatebody` eigenschappen. Sjabloonitems hebben de vorm van `{key}``key` een contextgegevenssleutel of een traditionele gegevenssleutel. De waarden die voor malplaatjeuitbreiding beschikbaar zijn zijn beperkt tot de metriek [van de](/help/android/metrics.md)Levenscyclus, naast om het even welke douanegegevens die aan slag in bijlage zijn die het bericht teweegbrengt. Er zijn momenteel geen historische of op een segment gebaseerde gegevens beschikbaar.

Er zijn ook specifieke, gereserveerde sjablonen die de SDK automatisch vervangt door interne gegevens die bekend zijn bij de SDK.

Deze lijst bevat:

| Tokennaam | Beschrijving van token |
|--- |--- |
| {%sdkver%} | Retourneert de SDK-versie. |
| {%cachebust%} | Hiermee wordt een willekeurig getal tussen 1 en 100000000 ingesteld. |
| {%adid%} | Retourneert Advertiser-id voor Android. Dit werkt alleen als u dit hebt gebruikt `submitAdvertisingIdentifierTask`. |
| {%pushID%} | Retourneert het token voor de push-id. Dit werkt alleen als u dit hebt gebruikt `setPushIdentifier`. |
| {%timestampu%} | Retourneert de huidige tijdstempel in tijdperk. |
| {%timestampz%} | Hiermee wordt de huidige tijdstempel geretourneerd in de JavaScript-indeling (ISO 8601). |