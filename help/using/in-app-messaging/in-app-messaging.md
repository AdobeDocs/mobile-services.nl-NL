---
description: Maak, beheer en rapporteer over in-app- en pushberichten.
keywords: mobiel
seo-description: Maak, beheer en rapporteer over in-app- en pushberichten.
seo-title: Berichten
solution: Experience Cloud,Analytics
title: Berichten
topic-fix: Metrics
uuid: e32d3e35-2d09-4ddf-8919-75dc895abcb3
exl-id: e6d076fc-3176-4591-8388-314b936c58cd
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 1%

---

# Berichten {#messaging}

U kunt in-app- en pushberichten maken, beheren en rapporteren.

## Nieuwe Adobe Experience Cloud SDK-release

Op zoek naar informatie en documentatie met betrekking tot de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze recentste documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga om aan de slag te gaan naar [Launch](https://launch.adobe.com/).
* Ga naar [Github om te zien wat er in de SDK-opslagruimten van het Experience Platform staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> Als u Adobe Experience Platform Mobile SDKs met de Lancering van de Adobe gebruikt, **must** ook installeert de uitbreiding van de Diensten van Adobe Analytics Mobile om de eigenschappen van de Diensten van de Mobiele Adobe te gebruiken zoals de Verbindingen van de Aankoop. Zie [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services) voor meer informatie. Zie [Pushberichten instellen](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) en [In-app messaging instellen](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging) voor informatie over het gebruik van pushberichten en in-app berichten met de Experience Platform-SDK&#39;s.

## In-app berichten {#section_8984F4568BC24D32A87429FFCB5184A6}

Berichten in de app worden in realtime aan gebruikers geleverd op basis van hun handelingen en kenmerken. De berichten worden geactiveerd op basis van analysegegevens die al door de SDK worden bijgehouden.

De volgende berichttypen worden ondersteund:

* Aangepast en thema
* Volledig scherm
* Native waarschuwingen
* Lokale meldingen

Hier volgt een aantal aanvullende informatie om u te helpen begrijpen hoe berichten in apps werken:

* Voor in-app-berichten is SDK versie 4.2 of hoger vereist.
* U moet opgeven wie beheerrechten voor mobiele apps heeft.

   Met deze rechten hebt u toegang tot aanschafkoppelingen en berichten in de app. Zie [Rollen en machtigingen](/help/using/gs/c-mob-roles-and-permissions.md) voor meer informatie.
* Nadat een bericht wordt goedgekeurd, wordt het bericht gepubliceerd automatisch aan de toepassing.
* SDK stelt het bericht aan gebruikers voor wanneer de berichtparameters, zoals eigenschappen, trekker, en programma, worden voldaan.
* Berichten kunnen aangepaste HTML of een afbeelding bevatten via een online-URL.

   Een back-up of een alternatieve afbeelding uit de app-bundel kan ook worden opgegeven voor berichten die worden geactiveerd terwijl ze offline zijn.
* De actieve en voltooide berichten verstrekken rapporten over totale meningen, klik-door tarieven, etc.
* Sjablonen zijn beschikbaar voor aangepaste berichten, waarmee u eenvoudig uw eigen in-app-bericht kunt maken.

## Pushberichten {#section_90555A55BCE7427A90B1577E14BEF51B}

Pushberichten worden verzonden naar gebruikers die zich hebben aangemeld om meldingen te ontvangen. U kunt deze pushberichten richten aan gebruikers in Analytics-segmenten of aangepaste segmenten. Met pushberichten kunt u passieve gebruikers opnieuw inschakelen of tijd- en locatiespecifieke informatie doorgeven, omdat de berichten buiten uw app worden weergegeven.

Alvorens u drukkend overseinen kunt vormen, zie [Eerste vereisten om duw overseinen](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md) toe te laten. Nadat u deze taken hebt uitgevoerd, moet u pushberichten configureren in de instellingen van uw app. Zie [Pushberichten configureren](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-push-messaging.md) voor meer informatie.
