---
description: Neem contact op met uw Adobe als u de Experience Cloud Device Co-op wilt gebruiken.
title: Experience Cloud Device Co-op
uuid: 434a6f8f-ec24-439d-95f0-a246b384b3b5
exl-id: bf4f7a81-152c-4033-bcdf-22a939a3109e
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 2%

---

# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Neem contact op met uw Adobe als u de Experience Cloud Device Co-op wilt gebruiken.

Voer de volgende stappen uit voor de Experience Cloud iOS SDK&#39;s om uw mobiele apps in te schakelen voor de Experience Cloud Device Co-op.

>[!IMPORTANT]
>
>Voor deze functionaliteit is iOS SDK versie 4.8.5 of hoger vereist.

Vanaf SDK-versie 4.16.1 kunnen apparaatcoopleden hun gegevens voor mobiele apparaten uitschakelen via de Experience Cloud Device Co-op. Zie [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md) en de `visitorAPI.js`-methode voor [isCoopSafe](https://experienceleague.adobe.com/docs/id-service/using/id-service-api/configurations/coopsafe.html) in de documentatie van de Adobe Experience Cloud Identity Service voor meer informatie.

1. Implementeer de Adobe Mobile SDK.

   Zie [Core Implementation and Lifecycle](/help/ios/getting-started/dev-qs.md) voor meer informatie.
1. Schakel uw Experience Cloud-id in.

   Zie [Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md) voor meer informatie.
1. Geef geverifieerde identiteiten zoals CRM-id&#39;s of gehashte e-mails door met een van de hier vermelde synchronisatiemethoden.

   Zie [Methoden van de identiteitsservice van Adobe Experience Platform](/help/ios/marketing-cloud/mc-methods.md) voor meer informatie.

## `coopUnsafe` markeren

Hier volgt aanvullende informatie over de markering `coopUnsafe`:

* Minimale SDK-versie: 4.16.1
* De eigenschap Boolean van het object `marketingCloud` dat, wanneer ingesteld op `true`, ervoor zorgt dat het apparaat wordt uitgeschakeld in Apparaat Co-Op.
* De standaardwaarde is `false`.
* Deze instelling wordt alleen gebruikt **alleen** voor klanten met apparaatco-op-provisioning.

Voor leden van Coop van het Apparaat die deze waarde vereisen worden geplaatst aan `true`, moet u met het team van Coop werken om een vlag van de lijst van gewezen personen op uw rekening van de Co-op van het Apparaat te verzoeken. Er is geen zelfbedieningspad om deze markeringen in te schakelen.

De volgende informatie onthouden:

* Als `coopUnsafe` is ingesteld op `true`, wordt `coop_unsafe=1` altijd toegevoegd aan Audience Manager- en bezoekersidentiteitscontroles.
* Als u het door:sturen van de server-kant van Analytics aan Audience Manager toelaat, zult u `coop_unsafe=1` op de treffers van Analytics ook zien.
