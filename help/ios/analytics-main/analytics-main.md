---
description: Deze informatie helpt u bij het gebruik van de iOS SDK met Adobe Analytics.
seo-description: Deze informatie helpt u bij het gebruik van de iOS SDK met Adobe Analytics.
seo-title: Overzicht van analysemogelijkheden
solution: Marketing Cloud,Analytics
title: Overzicht van analysemogelijkheden
topic: Developer and implementation
uuid: 8c7fb76a-be0b-4465-8151-ece7bad11b55
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Overzicht van analysemogelijkheden {#analytics}

Met de informatie in deze sectie kunt u de iOS SDK met Adobe Analytics gebruiken.

## Nieuwe release van Adobe Experience Platform Mobile SDK

Op zoek naar informatie en documentatie over de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via het [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga om aan de slag te gaan naar Adobe Experience Platform Launch.
* Ga naar [Github om te zien wat er in de repositories van Experience Platform SDK staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Id&#39;s voor het bijhouden van analyses genereren

In SDKs, worden de herkenningstekens gebruikt om gebruikers te volgen, en hier is de hiërarchie van herkenningstekens:

1. Aangepaste bezoeker-id (VID)
2. Identificatiecode voor analytische tracking (AID)
3. Experience Cloud Identifier (MID)

>[!TIP]
>
>Het juiste acroniem voor Experience Cloud Identifier is ECID. Hoewel SDKs nog MID gebruikt, is het de oude naam.
De HULP, die ook wel de tracking-id wordt genoemd, wordt gegenereerd door de SDK wanneer de toepassing niet is geconfigureerd voor het gebruik van een MID. De waarde blijft bestaan tussen het starten en het upgraden van de app in `NSUserDefaults`. Als de gebruiker de app van het apparaat verwijdert en de app opnieuw installeert, of als de ontwikkelaar van de app deze wist `NSUserDefaults`, wordt een nieuwe id gegenereerd door de SDK. Dit proces resulteert in een nieuwe gebruiker in Analytics rapportering.

Voor gebruikers in een app die Identity Service Support (MID) introduceert, worden bestaande HULP-waarden verzonden met Analytics-resultaten en bevat de treffer voor Analytics een HULP en een MID. Voor nieuwe gebruikers in een toepassing met identiteitsservice-ondersteuning bevatten de analyseverzoeken alleen een id. Zie [Bezoekers](https://docs.adobe.com/content/help/en/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html)identificeren voor meer informatie over het identificeren van bezoekers.
