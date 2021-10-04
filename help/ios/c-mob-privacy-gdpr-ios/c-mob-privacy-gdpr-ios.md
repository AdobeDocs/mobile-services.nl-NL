---
description: Experience Cloud Mobile SDK's bieden API's die geschikt zijn voor algemene gegevensbeschermingsregels (GDPR) voor controllers waarmee gebruikers lokaal opgeslagen identiteiten kunnen ophalen en statusvlaggen voor gegevensverzameling en -overdracht kunnen instellen.
title: Privacy en algemene gegevensbeschermingsverordening
uuid: 69bb82de-1993-440c-a1b0-8d37919b48b6
exl-id: 8549310d-31b8-49a3-9276-f8e9ab980a10
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 4%

---

# Privacy en algemene gegevensbeschermingsverordening {#privacy-and-general-data-protection-regulation}

Experience Cloud Mobile SDK&#39;s bieden API&#39;s die geschikt zijn voor algemene gegevensbeschermingsregels (GDPR) voor controllers waarmee gebruikers lokaal opgeslagen identiteiten kunnen ophalen en statusvlaggen voor gegevensverzameling en -overdracht kunnen instellen.

>[!IMPORTANT]
>
>GDPR wordt **alleen** ondersteund in Mobile SDK versie 4.16.0 of hoger.

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze recentste documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar Adobe Experience Platform Launch om aan de slag te gaan.
* Ga naar [Github om te zien wat er in de SDK-opslagruimten van het Experience Platform staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Overzicht

Wanneer Adobe software en diensten aan een onderneming verleent, handelt Adobe als gegevensverwerker voor om het even welke persoonlijke gegevens het verwerkt en opslaat als deel van het verlenen van deze diensten. Als gegevensverwerker verwerkt Adobe persoonlijke gegevens in overeenstemming met de toestemming en instructies van uw bedrijf (bijvoorbeeld, zoals die in uw overeenkomst met Adobe worden uiteengezet).

Als gegevenscontroller kunt u SDK&#39;s van Adobe Mobile Services gebruiken voor ondersteuning van GDPR om aanvragen van uw mobiele apps op te halen en te verwijderen.

Voor de Adobe Mobile SDK-delen van uw mobiele apps kunt u de volgende instellingen en methoden gebruiken:

* Gebruik de methode `getAllIdentifiersAsync` om gegevens van de SDK&#39;s op te halen en deze gegevens naar uw servers te verzenden.

   Zie [Opgeslagen id&#39;s ophalen](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md) voor meer informatie.

* Gebruik de volgende instellingen om de status van uw keuze in te stellen en u te helpen met een aanvraag voor het verwijderen van GDPR-gegevens:

   * `privacyDefault`
   * `setPrivacyStatus`

   Voor meer informatie, zie [Plaatsend de Status van de Gebruiker van de Opt](/help/ios/c-mob-privacy-gdpr-ios/privacy.md).

## Aanvullende informatie {#section_7C7124C50D85469C8C8714533FB1A37D}

* Voor meer informatie over GDPR, zie [GDPR en Uw Zaken](https://www.adobe.com/nl/privacy/general-data-protection-regulation.html).
* Ga naar [Algemene gegevensbeschermingsverordening API](https://adobe.io/apis/cloudplatform/gdpr.html) om de GDPR API-documentatie te bekijken.
