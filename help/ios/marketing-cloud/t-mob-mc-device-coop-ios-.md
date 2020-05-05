---
description: Neem contact op met uw Adobe-vertegenwoordiger om de Experience Cloud Device Co-op te starten.
seo-description: Neem contact op met uw Adobe-vertegenwoordiger om de Experience Cloud Device Co-op te starten.
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 434a6f8f-ec24-439d-95f0-a246b384b3b5
translation-type: tm+mt
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Neem contact op met uw Adobe-vertegenwoordiger om de Experience Cloud Device Co-op te starten.

Voer de volgende stappen uit voor de Experience Cloud iOS SDK&#39;s om uw mobiele apps in te schakelen voor de Experience Cloud Device Co-op.

>[!IMPORTANT]
>
>Voor deze functionaliteit is iOS SDK versie 4.8.5 of hoger vereist.

Vanaf SDK-versie 4.16.1 kunnen leden van Device Co-op hun gegevens van mobiele apparaten opteren voor de Experience Cloud Device Co-op. Zie [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md) en de `visitorAPI.js` methode voor [isCoopSafe](https://docs.adobe.com/content/help/en/id-service/using/id-service-api/configurations/coopsafe.html)voor meer informatie.

1. Implementeer de Adobe Mobile SDK.

   Zie [Core Implementation en Lifecycle](/help/ios/getting-started/dev-qs.md)voor meer informatie.
1. Schakel uw Experience Cloud-id in.

   Zie [Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md)voor meer informatie.
1. Geef geverifieerde identiteiten zoals CRM-id&#39;s of gehashte e-mails door met een van de hier vermelde synchronisatiemethoden.

   Zie Methoden van de identiteitsservice van [Adobe Experience Platform voor meer informatie](/help/ios/marketing-cloud/mc-methods.md).

## `coopUnsafe` markeren

Hier is wat extra informatie over de `coopUnsafe` vlag:

* Minimale SDK-versie: 4.16.1
* De Booleaanse eigenschap van het `marketingCloud` object dat, wanneer ingesteld op `true`, ervoor zorgt dat het apparaat wordt uitgeschakeld voor de codering apparaat van de Experience Cloud.
* De standaardwaarde is `false`.
* Deze instelling wordt **alleen** gebruikt voor klanten die via Device Co-op zijn ingericht.

Voor leden van Coop van het Apparaat die deze waarde vereisen wordt geplaatst aan `true`, moet u met het team van Coop samenwerken om een zwarte lijstvlag op uw Co-op rekening van het Apparaat te verzoeken. Er is geen zelfbedieningspad om deze markeringen in te schakelen.

De volgende informatie onthouden:

* Wanneer `coopUnsafe` is ingesteld op `true`, `coop_unsafe=1` worden deze altijd toegevoegd aan Audience Manager- en Bezoekersidentiteitscontroles.
* Als u het door:sturen van de server-kant van de Analyse aan de Manager van het Publiek toelaat, zult u ook `coop_unsafe=1` op de treffers van Analytics zien.


