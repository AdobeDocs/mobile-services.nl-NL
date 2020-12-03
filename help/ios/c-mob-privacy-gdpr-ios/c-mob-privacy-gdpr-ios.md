---
description: Experience Cloud Mobile SDK's bieden API's die geschikt zijn voor algemene gegevensbeschermingsregels (GDPR) voor controllers waarmee gebruikers lokaal opgeslagen identiteiten kunnen ophalen en statusvlaggen voor gegevensverzameling en -overdracht kunnen instellen.
seo-description: Experience Cloud Mobile SDK's bieden API's die geschikt zijn voor algemene gegevensbeschermingsregels (GDPR) voor controllers waarmee gebruikers lokaal opgeslagen identiteiten kunnen ophalen en statusvlaggen voor gegevensverzameling en -overdracht kunnen instellen.
seo-title: Privacy en algemene gegevensbeschermingsverordening
title: Privacy en algemene gegevensbeschermingsverordening
uuid: 69bb82de-1993-440c-a1b0-8d37919b48b6
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 2%

---


# Privacy en algemene gegevensbeschermingsverordening {#privacy-and-general-data-protection-regulation}

Experience Cloud Mobile SDK&#39;s bieden API&#39;s die geschikt zijn voor algemene gegevensbeschermingsregels (GDPR) voor controllers waarmee gebruikers lokaal opgeslagen identiteiten kunnen ophalen en statusvlaggen voor gegevensverzameling en -overdracht kunnen instellen.

>[!IMPORTANT]
>
>GDPR wordt **alleen** ondersteund in Mobile SDK versie 4.16.0 of hoger.

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar Adobe Experience Platform Launch om aan de slag te gaan.
* Ga naar [Github om te zien wat er in de SDK-opslagruimten van het Experience Platform staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Overzicht

Wanneer Adobe software en diensten aan een onderneming verleent, handelt Adobe als gegevensverwerker voor om het even welke persoonlijke gegevens het verwerkt en opslaat als deel van het verlenen van deze diensten. Als gegevensverwerker verwerkt Adobe persoonlijke gegevens in overeenstemming met de toestemming en instructies van uw bedrijf (bijvoorbeeld, zoals die in uw overeenkomst met Adobe worden uiteengezet).

Als gegevenscontroller kunt u SDK&#39;s van Adobe Mobile Services gebruiken voor ondersteuning van GDPR om aanvragen van uw mobiele apps op te halen en te verwijderen.

Voor de Adobe Mobile SDK-delen van uw mobiele apps kunt u de volgende instellingen en methoden gebruiken:

* Om gegevens van SDKs terug te winnen, en deze gegevens naar uw servers te verzenden, gebruik de `getAllIdentifiersAsync` methode.

   Zie Opgeslagen id&#39;s [ophalen voor meer informatie](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md).

* Gebruik de volgende instellingen om de status van uw keuze in te stellen en u te helpen met een aanvraag voor het verwijderen van GDPR-gegevens:

   * `privacyDefault`
   * `setPrivacyStatus`

   Zie [Opt-status](/help/ios/c-mob-privacy-gdpr-ios/privacy.md)van gebruiker instellen voor meer informatie.

## Extra informatie {#section_7C7124C50D85469C8C8714533FB1A37D}

* Zie [GDPR en Uw bedrijf](https://www.adobe.com/nl/privacy/general-data-protection-regulation.html)voor meer informatie over GDPR.
* Ga naar de API [voor](https://adobe.io/apis/cloudplatform/gdpr.html)algemene gegevensbeveiliging voor meer informatie over de GDPR API-documentatie.

