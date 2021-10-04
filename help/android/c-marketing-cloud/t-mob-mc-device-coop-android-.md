---
description: Neem contact op met uw Adobe als u de Experience Cloud Device Co-op wilt gebruiken.
title: Experience Cloud Device Co-op
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
exl-id: e34b8a7e-3b70-4725-94a5-9903987c34f8
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 2%

---

# Experience Cloud Device Co-op {#experience-cloud-device-co-op}

Neem contact op met uw Adobe als u de Experience Cloud Device Co-op wilt gebruiken.

Voer de volgende stappen voor de Experience Cloud Android-SDK&#39;s uit om uw mobiele apps in te schakelen voor de Experience Cloud Device Co-op:

>[!IMPORTANT]
>
>Voor deze functionaliteit is Android SDK versie 4.8.3 of hoger vereist.

Vanaf SDK-versie 4.16.1 kunnen apparaatcoopleden hun gegevens voor mobiele apparaten uitschakelen via de Experience Cloud Device Co-op. Zie [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md) en de methode `visitorAPI.js` voor [isCoopSafe](https://experienceleague.adobe.com/docs/id-service/using/id-service-api/configurations/coopsafe.html) voor meer informatie.

1. Implementeer de Adobe Mobile SDK.

   Zie [Core Implementation and Lifecycle](/help/android/getting-started/dev-qs.md) voor meer informatie.
1. Schakel uw Experience Cloud-id in.

   Voor meer informatie, zie [Experience Cloud ID Configuratie](/help/android/c-marketing-cloud/mcvid.md).
1. Geef geverifieerde identiteiten, zoals CRM-id&#39;s of gehashte e-mails, door een van de synchronisatiemethoden te gebruiken.

   Zie [Methoden van de identiteitsservice van Adobe Experience Platform](/help/android/c-marketing-cloud/mc-methods.md) voor meer informatie.

## `coopUnsafe` markeren

Hier is wat extra informatie over de `coopUnsafe` vlag:

* Minimale SDK-versie: 4.16.1
* De eigenschap Boolean van het object `marketingCloud` dat, wanneer ingesteld op `true`, ervoor zorgt dat het apparaat wordt uitgeschakeld in Apparaat Co-Op.
* De standaardwaarde is `false`.
* Deze instelling wordt alleen gebruikt **alleen** voor klanten met apparaatco-op-provisioning.

Voor leden van Coop van het Apparaat die deze waarde aan `true` vereisen, moet u met het team van Coop samenwerken om een vlag van de lijst van gewezen personen op uw rekening van de Co-op van het Apparaat te verzoeken. Er is geen zelfbedieningspad om deze markeringen in te schakelen.

De volgende informatie onthouden:

* Als `coopUnsafe` is ingesteld op `true`, wordt `coop_unsafe=1` altijd toegevoegd aan Audience Manager- en bezoekersidentiteitscontroles.
* Als u het door:sturen van de server-kant van de Analyse aan Audience Manager toelaat, zult u `coop_unsafe=1` de hits van de Analyse ook zien.
