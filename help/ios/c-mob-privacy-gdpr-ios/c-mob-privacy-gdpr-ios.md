---
description: Experience Cloud Mobile SDK's bieden API's die klaar zijn voor algemene gegevensbeschermingsregels (GDPR) voor controllers waarmee gebruikers lokaal opgeslagen identiteiten kunnen ophalen en statusvlaggen voor gegevensverzameling en -overdracht kunnen instellen.
title: Privacy en algemene gegevensbeschermingsverordening
uuid: 69bb82de-1993-440c-a1b0-8d37919b48b6
exl-id: 8549310d-31b8-49a3-9276-f8e9ab980a10
source-git-commit: bd55e3525488f24bc9845220f0df62706ec28f31
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 2%

---

# Privacy en algemene gegevensbeschermingsverordening {#privacy-and-general-data-protection-regulation}

Experience Cloud Mobile SDK&#39;s bieden API&#39;s die klaar zijn voor algemene gegevensbeschermingsregels (GDPR) voor controllers waarmee gebruikers lokaal opgeslagen identiteiten kunnen ophalen en statusvlaggen voor gegevensverzameling en -overdracht kunnen instellen.

>[!IMPORTANT]
>
>GDPR wordt ondersteund **alleen** in Mobile SDK versie 4.16.0 of hoger.

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de SDK van Adobe Experience Platform Mobile? Klikken [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar Adobe Experience Platform Launch om aan de slag te gaan.
* Ga naar [Github: Adobe Experience Platform SDK&#39;s](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Overzicht

Wanneer Adobe software en diensten aan een onderneming verleent, handelt Adobe als gegevensverwerker voor om het even welke persoonlijke gegevens het verwerkt en opslaat als deel van het verlenen van deze diensten. Als gegevensverwerker verwerkt Adobe persoonlijke gegevens in overeenstemming met de toestemming en instructies van uw bedrijf (bijvoorbeeld, zoals die in uw overeenkomst met Adobe worden uiteengezet).

Als gegevenscontroller kunt u Adobe Mobile Services SDK&#39;s gebruiken om GDPR te ondersteunen bij het ophalen en verwijderen van aanvragen van uw mobiele apps.

Voor de Adobe Mobile SDK-delen van uw mobiele apps kunt u de volgende instellingen en methoden gebruiken:

* Om gegevens van SDKs terug te winnen, en deze gegevens naar uw servers te verzenden, gebruik `getAllIdentifiersAsync` methode.

   Zie voor meer informatie [Opgeslagen id&#39;s ophalen](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md).

* Gebruik de volgende instellingen om de status van uw keuze in te stellen en u te helpen met een aanvraag voor het verwijderen van GDPR-gegevens:

   * `privacyDefault`
   * `setPrivacyStatus`

   Zie voor meer informatie [De status Opt van de gebruiker instellen](/help/ios/c-mob-privacy-gdpr-ios/privacy.md).

## Aanvullende informatie {#section_7C7124C50D85469C8C8714533FB1A37D}

* Voor meer informatie over GDPR raadpleegt u [GDPR en uw bedrijf](https://www.adobe.com/nl/privacy/general-data-protection-regulation.html).
