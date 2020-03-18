---
description: Ervaar Cloud Mobile SDK's bieden API's die klaar zijn voor algemene gegevensbeveiliging (GDPR) voor controllers waarmee gebruikers lokaal opgeslagen identiteiten kunnen ophalen en statusvlaggen voor gegevensverzameling en -overdracht kunnen instellen.
seo-description: Ervaar Cloud Mobile SDK's bieden API's die klaar zijn voor algemene gegevensbeveiliging (GDPR) voor controllers waarmee gebruikers lokaal opgeslagen identiteiten kunnen ophalen en statusvlaggen voor gegevensverzameling en -overdracht kunnen instellen.
seo-title: Overzicht van de privacy- en algemene gegevensbeschermingsverordening
title: Overzicht van de privacy- en algemene gegevensbeschermingsverordening
uuid: 56d6f155-efec-4b3f-a972-a63155729167
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# Overzicht van de privacy- en algemene gegevensbeschermingsverordening {#privacy-and-general-data-protection-regulation}

Ervaar Cloud Mobile SDK&#39;s bieden API&#39;s die klaar zijn voor algemene gegevensbeveiliging (GDPR) voor controllers waarmee gebruikers lokaal opgeslagen identiteiten kunnen ophalen en statusvlaggen voor gegevensverzameling en -overdracht kunnen instellen.

## Nieuwe release van Adobe Experience Platform Mobile SDK

Op zoek naar informatie en documentatie over de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via het [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga om aan de slag te gaan naar Adobe Experience Platform Launch.
* Ga naar [Github om te zien wat er in de repositories van Experience Platform SDK staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Overzicht

>[!IMPORTANT]
>
>GDPR wordt **alleen** ondersteund in Mobile SDK versie 4.16.0 of hoger.

Als Adobe software en services aan een onderneming levert, fungeert Adobe als gegevensverwerker voor persoonlijke gegevens die het verwerkt en opslaat als onderdeel van het aanbieden van deze services. Als gegevensverwerker verwerkt Adobe persoonlijke gegevens volgens de toestemming en instructies van uw bedrijf (bijvoorbeeld zoals die in uw overeenkomst met Adobe zijn vermeld).

Als gegevenscontroller kunt u SDK&#39;s van Adobe Mobile Services gebruiken voor ondersteuning van GDPR om aanvragen van uw mobiele apps op te halen en te verwijderen.

Voor de Adobe Mobile SDK-delen van uw mobiele apps kunt u de volgende instellingen en methoden gebruiken:

* Om gegevens van SDKs terug te winnen, en deze gegevens naar uw servers te verzenden, gebruik de `getAllIdentifiersAsync` methode.

   Zie Opgeslagen id&#39;s [ophalen voor meer informatie](/help/android/c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md).

* Gebruik de volgende instellingen om de status van uw keuze in te stellen en u te helpen met een aanvraag voor het verwijderen van GDPR-gegevens:

   * `privacyDefault`
   * `setPrivacyStatus`
   Zie [Opt-status](/help/android/c-mob-privacy-gdpr-android/privacy.md)van gebruiker instellen voor meer informatie.