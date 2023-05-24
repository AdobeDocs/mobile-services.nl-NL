---
description: Maak, beheer en rapporteer over in-app- en pushberichten.
keywords: mobiel
solution: Experience Cloud Services,Analytics
title: Berichten
topic-fix: Metrics
uuid: e32d3e35-2d09-4ddf-8919-75dc895abcb3
exl-id: e6d076fc-3176-4591-8388-314b936c58cd
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 2%

---

# Berichten {#messaging}

{#eol}

U kunt in-app- en pushberichten maken, beheren en rapporteren.

## Nieuwe Adobe Experience Cloud SDK-release

Op zoek naar informatie en documentatie met betrekking tot de Adobe Experience Platform Mobile SDK? Klikken [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga om aan de slag te gaan naar [Starten](https://launch.adobe.com/).
* Ga naar [Github: Adobe Experience Platform SDK&#39;s](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> Als u de Adobe Experience Platform Mobile SDK&#39;s gebruikt met Adobe Launch, kunt u **moet** Installeer ook de Adobe Analytics Mobile Services-extensie om Adobe Mobile Services-functies, zoals de Acquisition-koppelingen, te gebruiken. Zie voor meer informatie [Adobe Analytics - Mobiele services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). Voor informatie over het gebruiken van duw overseinen en in-app overseinen met de Experience Platform SDKs, zie [Pushberichten instellen](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) en [In-app berichten instellen](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

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

   Met deze rechten hebt u toegang tot aanschafkoppelingen en berichten in de app. Zie voor meer informatie [Rollen en machtigingen](/help/using/gs/c-mob-roles-and-permissions.md).
* Nadat een bericht wordt goedgekeurd, wordt het bericht gepubliceerd automatisch aan de toepassing.
* SDK stelt het bericht aan gebruikers voor wanneer de berichtparameters, zoals eigenschappen, trekker, en programma, worden voldaan.
* Berichten kunnen aangepaste HTML of een afbeelding bevatten via een online-URL.

   Een back-up of een alternatieve afbeelding uit de app-bundel kan ook worden opgegeven voor berichten die worden geactiveerd terwijl ze offline zijn.
* De actieve en voltooide berichten verstrekken rapporten over totale meningen, klik-door tarieven, etc.
* Sjablonen zijn beschikbaar voor aangepaste berichten, waarmee u eenvoudig uw eigen in-app-bericht kunt maken.

## Pushberichten {#section_90555A55BCE7427A90B1577E14BEF51B}

Pushberichten worden verzonden naar gebruikers die zich hebben aangemeld om meldingen te ontvangen. U kunt deze pushberichten richten aan gebruikers in Analytics-segmenten of aangepaste segmenten. Met pushberichten kunt u passieve gebruikers opnieuw inschakelen of tijd- en locatiespecifieke informatie doorgeven, omdat de berichten buiten uw app worden weergegeven.

Voordat u pushberichten kunt configureren, raadpleegt u [Vereisten om pushberichten in te schakelen](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md). Nadat u deze taken hebt uitgevoerd, moet u pushberichten configureren in de instellingen van uw app. Zie voor meer informatie [Pushberichten configureren](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-push-messaging.md).
