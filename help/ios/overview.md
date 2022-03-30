---
description: Met iOS SDK 4.x voor Experience Cloud Solutions kunt u native Apple iPhone- en iPad-toepassingen meten, gerichte inhoud leveren binnen uw apps en gegevens voor het publiek verzamelen en benutten via Audience Manager.
solution: Experience Cloud Services,Analytics
title: iOS SDK 4.x voor Experience Cloud Solutions
topic-fix: Developer and implementation
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
exl-id: d4dbddf7-c8be-4936-adfb-2f7aa07a0dd4
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# iOS SDK 4.x voor Experience Cloud Solutions{#ios-sdk-x-for-experience-cloud-solutions}

Met iOS SDK 4.x voor Experience Cloud Solutions kunt u native Apple iPhone- en iPad-toepassingen meten, gerichte inhoud leveren binnen uw apps en gegevens voor het publiek verzamelen en benutten via Audience Manager.

>[!IMPORTANT]
>
>Vanaf versie 4.21.0 heeft de iOS SDK een minimaal vereiste versie van Xcode 12. Als u Cocoapods gebruikt om afhankelijkheden in uw app te beheren, vereist de Adobe SDK versie 1.10.0 of hoger van Cocoapods.

Als u 4.21.0 of hoger gebruikt, leest u de documentatie met de volgende wijzigingen, rekening houdend met:

* Telkens wanneer een binair bibliotheekdossier wordt vermeld, zou zijn vervanging XCFraframework in plaats daarvan moeten worden gebruikt:
   * `AdobeMobileLibrary.a` > `AdobeMobile.xcframework`
   * `AdobeMobileLibrary_Extension.a` > `AdobeMobileExtension.xcframework`
   * `AdobeMobileLibrary_Watch.a` > `AdobeMobileWatch.xcframework`
   * `AdobeMobileLibrary_TV.a` > `AdobeMobileTV.xcframework`
* Als manueel het toevoegen van Adobe XCFrameworks aan uw project, zorg ervoor dat zij niet ingebed zijn.

>[!IMPORTANT]
>
>De Adobe Analytics Mobile Marketing Add-on SKU is vereist om Mobile Services toegang te geven tot mogelijkheden voor mobiele aanschaf, diepe koppelingen, geolocatie en mobiel berichtenverkeer. Neem voor meer informatie contact op met uw Adobe CSM.

>[!IMPORTANT]
>
>De iOS SDK 4.x for Experience Cloud Solutions wordt nu ondersteund [iOS 13 en Xcode 11](https://developer.apple.com/ios/). Voor naadloze compatibiliteit gebruikt u de nieuwste versies van de 4.x iOS SDK&#39;s. Voor meer informatie over de nieuwste versie raadpleegt u de [releaseopmerkingen](/help/ios/rel-notes.md).

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de SDK van Adobe Experience Platform Mobile? Klikken [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar Adobe Experience Platform Launch om aan de slag te gaan.
* Ga naar [Github: Adobe Experience Platform SDK&#39;s](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

Enkele informatie die u moet onthouden:

* iOS 8 of hoger wordt ondersteund

   Voor iOS 11 of hoger kunt u **moet** hebben SDK versie 4.13.8 of hoger.

* In versie 4.2 van deze SDK en hoger worden nu alle hits verzonden via HTTP-POST.

   Dit heeft geen invloed op de gegevens die worden verzameld of gerapporteerd, maar u moet een pakketanalysator gebruiken die het inspecteren van de gegevens van de POST aan meningsklappen steunt.

* Als u een upgrade uitvoert vanaf een eerdere versie (2.x of 3.x), raadpleegt u de [4.x-migratiegids](/help/ios/getting-started/migration-v3.md).

## Adobe Mobile-gebruikersdocumentatie {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile-services bieden een nieuwe gebruikersinterface waarin mobiele marketingmogelijkheden voor mobiele toepassingen vanuit heel Adobe Experience Cloud worden samengebracht. Aanvankelijk biedt de Mobile-service naadloze integratie van analysemogelijkheden voor apps en doelgerichte functionaliteit van de oplossingen Adobe Analytics, Adobe Audience Manager en Adobe Target, en Adobe Experience Platform Identity Service.

Ga voor meer informatie over de gebruikersinterface van Mobile Services en de gebruikersdocumentatie naar [Adobe mobiele services](/help/using/home.md).

## Bloedhond gebruiken

>[!IMPORTANT]
>
>Vanaf **30 april 2017**, Adobe Bloodhound is zonsondergang. Vanaf 1 mei 2017 worden er geen aanvullende verbeteringen aangebracht en wordt er geen extra ondersteuning voor Engineering of Adobe Expert Care geboden.
