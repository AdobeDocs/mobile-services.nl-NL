---
description: De Adobe SDK maakt gebruik van API's voor zoekopdrachten in advertenties van Apple om ontwikkelaars en marketers in staat te stellen toepassingsdownloads die afkomstig zijn van campagnes voor zoekopdrachten in de Apple App Store, te volgen en te kenmerken.
solution: Experience Cloud Services,Analytics
title: Zoeken in Apple-advertenties
topic-fix: Developer and implementation
uuid: 790080e8-067e-4bfd-a169-0027db4fdff3
exl-id: efcdd430-f08d-4ee2-85f3-2697c3bd72db
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Zoeken in Apple-advertenties {#apple-search-ads}

De Adobe SDK maakt gebruik van API&#39;s voor zoekopdrachten in advertenties van Apple om ontwikkelaars en marketers in staat te stellen toepassingsdownloads die afkomstig zijn van campagnes voor zoekopdrachten in de Apple App Store, te volgen en te kenmerken. Ga voor meer informatie over campagnes in advertentie zoeken naar [Zoeken in Apple-advertenties](https://searchads.apple.com).

## Voordelen {#section_CEA30C652AC8470784B8054E299B80FA}

Hier volgen enkele voordelen van het gebruik van Apple-advertenties:

* U kunt eenvoudig de doeltreffendheid van uw downloadcampagnes voor zoekadvertenties meten door een paar coderegels aan uw app toe te voegen.
* Ontwikkelaars hebben toegang tot de datum/tijd van de download en het trefwoord dat u hebt geboden tijdens de conversie.

## Apple-advertenties implementeren {#section_F1094676793540CFA1DBB540174EEB6A}

>[!TIP]
>
>Als u Apple Ads wilt implementeren, moet u iOS SDK versie 4.13.2 of hoger hebben.

Uw app inschakelen voor kenmerk Zoeken en toevoegen:

1. Voer versie 4.13.2 of hoger van Adobe SDK uit.

   Zie voor meer informatie [Kernimplementatie en levenscyclus](/help/ios/getting-started/dev-qs.md).

1. Voeg het Advertentieframework toe aan het Xcode-projectbestand voor uw app.

## Rapportage over kenmerken van zoekopdrachten {#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. De toewijzingsgegevens van Apple Search Ads worden opgegeven in de naam van de acquisitie, de bron en de term waarden.

   Indien attributie = `true`, alle `iad-*` velden worden opgenomen in de hit tijdens de levenscyclus.

   Daarnaast worden de volgende waarden toegewezen op basis van de `"iad"` woordenboek voor onze typische gegevensvelden van de verwervingscontext:

   * `"iad-campaign-id"` --> `"a.referrer.campaign.trackingcode"`
   * `"iad-campaign-name"` —> `"a.referrer.campaign.name"`
   * `"iad-adgroup-id"` —> `"a.referrer.campaign.content"`
   * `"iad-keyword"` —> `"a.referrer.campaign.term"`
   Deze toewijzing zorgt ervoor dat de waarden in onze standaardrapportering beschikbaar zijn.
