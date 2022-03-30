---
description: Met deze informatie kunt u de iOS SDK met Adobe Analytics gebruiken.
solution: Experience Cloud Services,Analytics
title: Overzicht van analysemogelijkheden
topic-fix: Developer and implementation
uuid: 8c7fb76a-be0b-4465-8151-ece7bad11b55
exl-id: 7c383b1d-2e59-4473-9de5-80c84d896f6d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# Overzicht van analysemogelijkheden {#analytics}

Met de informatie in deze sectie kunt u de iOS SDK met Adobe Analytics gebruiken.

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de SDK van Adobe Experience Platform Mobile? Klikken [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar Adobe Experience Platform Launch om aan de slag te gaan.
* Ga naar [Github: Adobe Experience Platform SDK&#39;s](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Id&#39;s voor het bijhouden van analyses genereren

In SDKs, worden de herkenningstekens gebruikt om gebruikers te volgen, en hier is de hiërarchie van herkenningstekens:

1. Aangepaste bezoeker-id (VID)
1. Identificatiecode voor analytische tracking (AID)
1. Experience Cloud-id (MID)

>[!TIP]
>
>Het juiste acroniem voor Experience Cloud-id is ECID. Hoewel SDKs nog MID gebruikt, is het de oude naam.

De HULP, die ook wel de tracking-id wordt genoemd, wordt gegenereerd door de SDK wanneer de toepassing niet is geconfigureerd voor het gebruik van een MID. De waarde blijft bestaan tussen het starten en het upgraden van de app in `NSUserDefaults`. Als de gebruiker de app van het apparaat verwijdert en de app opnieuw installeert, of als de ontwikkelaar van de app deze wist `NSUserDefaults`, wordt een nieuwe id gegenereerd door de SDK. Dit proces resulteert in een nieuwe gebruiker in Analytics rapportering.

Voor gebruikers in een app die Identity Service Support (MID) introduceert, worden bestaande HULP-waarden verzonden met Analytics-resultaten en bevat de treffer voor Analytics een HULP en een MID. Voor nieuwe gebruikers in een toepassing met identiteitsservice-ondersteuning bevatten de analyseverzoeken alleen een id. Voor meer informatie over het identificeren van bezoekers raadpleegt u [Unieke bezoekers](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html) in de documentatie van Adobe Analytics.
