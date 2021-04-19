---
description: Met deze informatie kunt u de iOS SDK met Adobe Analytics gebruiken.
seo-description: Met deze informatie kunt u de iOS SDK met Adobe Analytics gebruiken.
seo-title: Overzicht van analysemogelijkheden
solution: Experience Cloud,Analytics
title: Overzicht van analysemogelijkheden
topic-fix: Developer and implementation
uuid: 8c7fb76a-be0b-4465-8151-ece7bad11b55
exl-id: 7c383b1d-2e59-4473-9de5-80c84d896f6d
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# Analyseoverzicht {#analytics}

Met de informatie in deze sectie kunt u de iOS SDK met Adobe Analytics gebruiken.

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze recentste documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar Adobe Experience Platform Launch om aan de slag te gaan.
* Ga naar [Github om te zien wat er in de SDK-opslagruimten van het Experience Platform staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Id&#39;s voor het bijhouden van analyses genereren

In SDKs, worden de herkenningstekens gebruikt om gebruikers te volgen, en hier is de hiërarchie van herkenningstekens:

1. Aangepaste bezoeker-id (VID)
1. Identificatiecode voor analytische tracking (AID)
1. Experience Cloud-id (MID)

>[!TIP]
>
>Het juiste acroniem voor Experience Cloud-id is ECID. Hoewel SDKs nog MID gebruikt, is het de oude naam.

De HULP, die ook wel de tracking-id wordt genoemd, wordt gegenereerd door de SDK wanneer de toepassing niet is geconfigureerd voor het gebruik van een MID. De waarde blijft bestaan tussen het starten en het upgraden van de app in `NSUserDefaults`. Als de gebruiker de app van het apparaat verwijdert en de app vervolgens opnieuw installeert, of als de ontwikkelaar van de app `NSUserDefaults` wist, wordt een nieuwe id gegenereerd door de SDK. Dit proces resulteert in een nieuwe gebruiker in Analytics rapportering.

Voor gebruikers in een app die Identity Service Support (MID) introduceert, worden bestaande HULP-waarden verzonden met Analytics-resultaten en bevat de treffer voor Analytics een HULP en een MID. Voor nieuwe gebruikers in een toepassing met identiteitsservice-ondersteuning bevatten de analyseverzoeken alleen een id. Zie [Bezoekers identificeren](https://docs.adobe.com/content/help/en/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html) voor meer informatie over het identificeren van bezoekers.
