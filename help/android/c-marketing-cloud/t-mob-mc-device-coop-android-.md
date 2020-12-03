---
description: Neem contact op met uw Adobe als u de Experience Cloud Device Co-op wilt gebruiken.
seo-description: Neem contact op met uw Adobe als u de Experience Cloud Device Co-op wilt gebruiken.
seo-title: Experience Cloud Device Co-op
title: Experience Cloud Device Co-op
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
translation-type: tm+mt
source-git-commit: 86ba045b44bf6553e80727c0d61ccdd9a552d16c
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 2%

---


# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Neem contact op met uw Adobe als u de Experience Cloud Device Co-op wilt gebruiken.

Voer de volgende stappen voor de Experience Cloud Android-SDK&#39;s uit om uw mobiele apps in te schakelen voor de Experience Cloud Device Co-op:

>[!IMPORTANT]
>
>Voor deze functionaliteit is Android SDK versie 4.8.3 of hoger vereist.

Vanaf SDK-versie 4.16.1 kunnen apparaatcoopleden hun gegevens voor mobiele apparaten uitschakelen via de Experience Cloud Device Co-op. Zie [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md) en de `visitorAPI.js` methode voor [isCoopSafe](https://docs.adobe.com/content/help/en/id-service/using/id-service-api/configurations/coopsafe.html)voor meer informatie.

1. Implementeer de Adobe Mobile SDK.

   Zie [Core Implementation en Lifecycle](/help/android/getting-started/dev-qs.md)voor meer informatie.
1. Schakel uw Experience Cloud-id in.

   Voor meer informatie, zie de Configuratie [van identiteitskaart van de](/help/android/c-marketing-cloud/mcvid.md)Experience Cloud.
1. Geef geverifieerde identiteiten, zoals CRM-id&#39;s of gehashte e-mails, door een van de synchronisatiemethoden te gebruiken.

   Zie Methoden van [Adobe Experience Platform Identity Service voor meer informatie](/help/android/c-marketing-cloud/mc-methods.md).

## `coopUnsafe` markeren

Hier is wat extra informatie over de `coopUnsafe` vlag:

* Minimale SDK-versie: 4.16.1
* De Booleaanse eigenschap van het `marketingCloud` object dat, wanneer ingesteld op `true`, ervoor zorgt dat het apparaat wordt uitgeschakeld in de Mac OS-Op van het Experience Cloud.
* De standaardwaarde is `false`.
* Deze instelling wordt **alleen** gebruikt voor klanten die via Device Co-op zijn ingericht.

Voor leden van Coop van het Apparaat die deze waarde aan `true`vereisen, moet u met het team van Coop samenwerken om een vlag van de lijst van afgewezen personen op uw rekening van de Co-op van het Apparaat te verzoeken. Er is geen zelfbedieningspad om deze markeringen in te schakelen.

De volgende informatie onthouden:

* Wanneer `coopUnsafe` deze optie is ingesteld op `true`, `coop_unsafe=1` worden deze altijd toegevoegd aan treffers voor Audience Manager- en bezoekersidentiteitskaart.
* Als u het door:sturen van de server-kant van de Analyse aan Audience Manager toelaat, zult u ook de `coop_unsafe=1` Inslagen van Analytics zien.