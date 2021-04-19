---
description: Met de iOS SDK 4.x voor Experience Cloud Solutions kunt u systeemeigen Apple iPhone- en iPad-toepassingen meten, gerichte inhoud binnen uw apps leveren en gegevens voor het publiek verzamelen en benutten via de Audience Manager.
seo-description: Met de iOS SDK 4.x voor Experience Cloud Solutions kunt u systeemeigen Apple iPhone- en iPad-toepassingen meten, gerichte inhoud binnen uw apps leveren en gegevens voor het publiek verzamelen en benutten via de Audience Manager.
seo-title: iOS SDK 4.x voor Experience Cloud-oplossingen
solution: Experience Cloud,Analytics
title: iOS SDK 4.x voor Experience Cloud-oplossingen
topic-fix: Developer and implementation
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
exl-id: d4dbddf7-c8be-4936-adfb-2f7aa07a0dd4
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# iOS SDK 4.x voor Experience Cloud Solutions{#ios-sdk-x-for-experience-cloud-solutions}

Met de iOS SDK 4.x voor Experience Cloud Solutions kunt u systeemeigen Apple iPhone- en iPad-toepassingen meten, gerichte inhoud binnen uw apps leveren en gegevens voor het publiek verzamelen en benutten via de Audience Manager.

>[!IMPORTANT]
>
>Vanaf versie 4.21.0 heeft de iOS SDK een minimaal vereiste versie van Xcode 12. Als u Cocoapods gebruikt om afhankelijkheden in uw app te beheren, vereist de Adobe SDK versie 1.10.0 of hoger van Cocoapods.

Als u 4.21.0 of hoger gebruikt, leest u de documentatie met de volgende wijzigingen, rekening houdend met:

* Telkens wanneer een binair bibliotheekdossier wordt vermeld, zou zijn vervanging XCFraframework in plaats daarvan moeten worden gebruikt:
   * `AdobeMobileLibrary.a` > `AdobeMobile.xcframework`
   * `AdobeMobileLibrary_Extension.a` >  `AdobeMobileExtension.xcframework`
   * `AdobeMobileLibrary_Watch.a` >  `AdobeMobileWatch.xcframework`
   * `AdobeMobileLibrary_TV.a` >  `AdobeMobileTV.xcframework`
* Als manueel het toevoegen van Adobe XCFrameworks aan uw project, zorg ervoor dat zij niet ingebed zijn.

>[!IMPORTANT]
>
>De Adobe Analytics Mobile Marketing Add-on SKU is vereist om Mobile Services toegang te geven tot mobiele aanschaf, diepe koppelingen, geolocatie en mogelijkheden voor mobiel berichtenverkeer. Neem voor meer informatie contact op met uw Adobe CSM.

>[!IMPORTANT]
>
>De iOS SDK 4.x voor Experience Cloud Solutions ondersteunt nu [iOS 13 en Xcode 11](https://developer.apple.com/ios/). Voor naadloze compatibiliteit gebruikt u de nieuwste versies van de 4.x iOS SDK&#39;s. Voor meer informatie over de recentste versie, zie [versienota&#39;s](/help/ios/rel-notes.md).

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze recentste documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar Adobe Experience Platform Launch om aan de slag te gaan.
* Ga naar [Github om te zien wat er in de SDK-opslagruimten van het Experience Platform staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

Enkele informatie die u moet onthouden:

* iOS 8 of hoger wordt ondersteund

   Voor iOS 11 of hoger hebt u **must** SDK versie 4.13.8 of hoger.

* In versie 4.2 van deze SDK en hoger worden nu alle hits verzonden via HTTP-POST.

   Dit heeft geen invloed op de gegevens die worden verzameld of gerapporteerd, maar u moet een pakketanalysator gebruiken die het inspecteren van de gegevens van de POST aan meningsklappen steunt.

* Als u een upgrade uitvoert vanaf een vorige versie (2.x of 3.x), raadpleegt u de [4.x-migratiehandleiding](/help/ios/getting-started/migration-v3.md).

## Adobe mobiele gebruikersdocumentatie {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile-services bieden een nieuwe gebruikersinterface waarin mobiele marketingmogelijkheden voor mobiele toepassingen uit de hele Adobe Experience Cloud worden samengebracht. Aanvankelijk biedt de Mobile-service een naadloze integratie van analysemogelijkheden voor apps en doelgerichte functionaliteit van de Adobe Analytics-, Adobe Audience Manager- en Adobe Target-oplossingen en Adobe Experience Platform Identity Service.

Zie [Mobiele services Adobe](/help/using/home.md) voor meer informatie over de gebruikersinterface voor mobiele services en de gebruikersdocumentatie.

## Bloedhond gebruiken

>[!IMPORTANT]
>
>Vanaf **30 april 2017** is Adobe Bloodhound zonsondergang. Vanaf 1 mei 2017 worden er geen aanvullende verbeteringen aangebracht en wordt er geen extra ondersteuning voor Engineering of Adobe Expert Care geboden.
