---
description: De SDK van Adobe maakt gebruik van API's voor zoekadvertenties van Apple om ontwikkelaars en marketers in staat te stellen toepassingsdownloads die afkomstig zijn van campagnes voor zoekopdrachten in de Apple App Store, bij te houden en te kenmerken.
seo-description: De SDK van Adobe maakt gebruik van API's voor zoekadvertenties van Apple om ontwikkelaars en marketers in staat te stellen toepassingsdownloads die afkomstig zijn van campagnes voor zoekopdrachten in de Apple App Store, bij te houden en te kenmerken.
seo-title: Apple-zoekadvertenties
solution: Marketing Cloud,Analytics
title: Apple-zoekadvertenties
topic: Developer and implementation
uuid: 790080e8-067e-4bfd-a169-0027db4fdff3
translation-type: tm+mt
source-git-commit: ebcc04ab3e80aafb9d9ec2e1fbc809c743554cb7

---


# Apple-zoekadvertenties {#apple-search-ads}

De SDK van Adobe maakt gebruik van API&#39;s voor zoekadvertenties van Apple om ontwikkelaars en marketers in staat te stellen toepassingsdownloads die afkomstig zijn van campagnes voor zoekopdrachten in de Apple App Store, bij te houden en te kenmerken. Raadpleeg [zoekadvertenties](https://searchads.apple.com)van Apple voor meer informatie over campagnes voor Zoeken in advertenties.

## Voordelen {#section_CEA30C652AC8470784B8054E299B80FA}

Hier volgen enkele voordelen van het gebruik van Apple-advertenties:

* U kunt eenvoudig de doeltreffendheid van uw downloadcampagnes voor zoekadvertenties meten door een paar coderegels aan uw app toe te voegen.
* Ontwikkelaars hebben toegang tot de datum/tijd van de download en het trefwoord dat u hebt geboden tijdens de conversie.

## Apple-advertenties implementeren {#section_F1094676793540CFA1DBB540174EEB6A}

>[!TIP]
>
>Als u Apple Ads wilt implementeren, hebt u iOS SDK versie 4.13.2 of hoger nodig.

Uw app inschakelen voor kenmerk Zoeken en toevoegen:

1. Implementeer Adobe SDK versie 4.13.2 of hoger.

   Zie [Core-implementatie en levenscyclus](/help/ios/getting-started/dev-qs.md)voor meer informatie.

1. Voeg het Advertentieframework toe aan het Xcode-projectbestand voor uw app.

## Rapportage over kenmerken van zoekopdrachten {#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. De toewijzingsgegevens van Apple Search Ads worden opgegeven in de naam van de verwerving, de bron en de term waarden.

   Als attributie = `true`, zullen alle `iad-*` gebieden in het loopbaankletter worden omvat.

   Bovendien worden de volgende waarden toegewezen van het `"iad"` woordenboek aan onze typische gegevensgebieden van de verwervingscontext:

   * `"iad-campaign-id"` --> `"a.referrer.campaign.trackingcode"`
   * `"iad-campaign-name"` --> `"a.referrer.campaign.name"`
   * `"iad-adgroup-id"` --> `"a.referrer.campaign.content"`
   * `"iad-keyword"` --> `"a.referrer.campaign.term"`
   Deze toewijzing zorgt ervoor dat de waarden in onze standaardrapportering beschikbaar zijn.
