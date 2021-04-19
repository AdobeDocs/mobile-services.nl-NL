---
description: De Adobe SDK gebruikt de API's voor zoekadvertenties van Apple om ontwikkelaars en marketers in staat te stellen app-downloads die afkomstig zijn van campagnes voor zoekopdrachten in de Apple App Store, te volgen en aan te duiden.
seo-description: De Adobe SDK gebruikt de API's voor zoekadvertenties van Apple om ontwikkelaars en marketers in staat te stellen app-downloads die afkomstig zijn van campagnes voor zoekopdrachten in de Apple App Store, te volgen en aan te duiden.
seo-title: Apple-zoekadvertenties
solution: Experience Cloud,Analytics
title: Apple-zoekadvertenties
topic-fix: Developer and implementation
uuid: 790080e8-067e-4bfd-a169-0027db4fdff3
exl-id: efcdd430-f08d-4ee2-85f3-2697c3bd72db
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Apple-zoekadvertenties {#apple-search-ads}

De Adobe SDK gebruikt de API&#39;s voor zoekadvertenties van Apple om ontwikkelaars en marketers in staat te stellen app-downloads die afkomstig zijn van campagnes voor zoekopdrachten in de Apple App Store, te volgen en aan te duiden. Zie [Apple Search Ads](https://searchads.apple.com) voor meer informatie over campagnes voor zoekopdrachten.

## Voordelen {#section_CEA30C652AC8470784B8054E299B80FA}

Hier volgen enkele voordelen van het gebruik van Apple-advertenties:

* U kunt eenvoudig de doeltreffendheid van uw downloadcampagnes voor zoekadvertenties meten door een paar coderegels aan uw app toe te voegen.
* Ontwikkelaars hebben toegang tot de datum/tijd van de download en het trefwoord dat u hebt geboden tijdens de conversie.

## Apple-advertenties {#section_F1094676793540CFA1DBB540174EEB6A} implementeren

>[!TIP]
>
>Als u Apple Ads wilt implementeren, hebt u iOS SDK versie 4.13.2 of hoger nodig.

Uw app inschakelen voor kenmerk Zoeken en toevoegen:

1. Voer versie 4.13.2 of hoger van Adobe SDK uit.

   Zie [Core-implementatie en levenscyclus](/help/ios/getting-started/dev-qs.md) voor meer informatie.

1. Voeg het Advertentieframework toe aan het Xcode-projectbestand voor uw app.

## Rapportage over kenmerk Zoekadvertenties {#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. De toewijzingsgegevens van Apple Search Ads worden opgegeven in de naam van de verwerving, de bron en de term waarden.

   Als attributie = `true`, zullen alle `iad-*` gebieden in de levenscyclushit worden omvat.

   Daarnaast worden de volgende waarden vanuit het woordenboek `"iad"` toegewezen aan de gegevensvelden van onze standaardverzamelingscontext:

   * `"iad-campaign-id"` --> `"a.referrer.campaign.trackingcode"`
   * `"iad-campaign-name"` —>  `"a.referrer.campaign.name"`
   * `"iad-adgroup-id"` —>  `"a.referrer.campaign.content"`
   * `"iad-keyword"` —>  `"a.referrer.campaign.term"`
   Deze toewijzing zorgt ervoor dat de waarden in onze standaardrapportering beschikbaar zijn.
