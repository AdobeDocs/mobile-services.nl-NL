---
description: Met deze informatie kunt u Apple TV implementeren met tvOS.
solution: Experience Cloud Services,Analytics
title: Apple TV-implementatie met tvOS
topic-fix: Developer and implementation
uuid: d1571ea2-a5de-4b96-a527-72abbf51fab8
exl-id: 35b7f02d-ae48-4c6f-9a3a-6d106a1026ad
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 1%

---

# Apple TV-implementatie met tvOS {#apple-tv-implementation-with-tvos}

Met deze informatie kunt u Apple TV implementeren met tvOS.

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de SDK van Adobe Experience Platform Mobile? Klikken [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar Adobe Experience Platform Launch om aan de slag te gaan.
* Ga naar [Github: Adobe Experience Platform SDK&#39;s](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Overzicht

Met Apple TV kunt u nu toepassingen maken die worden uitgevoerd in de native tvOS-omgeving. U kunt een native app maken met behulp van verschillende frameworks in iOS, of u kunt uw app maken met XML-sjablonen en JavaScript.

>[!TIP]
>
>tvOS-ondersteuning is beschikbaar vanaf `AdobeMobileLibrary` versie 4.7.0.

## Aan de slag {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>We gaan ervan uit dat uw project een doel heeft dat een Apple TV-app is die zich richt op tvOS. Zie voor meer informatie [tvOS](https://developer.apple.com/tvos/documentation/).

## Een native app voor tvOS configureren {#section_5095F19B3C4545F68E8C1E37A7E303AE}

Voer de volgende stappen uit in uw Xcode-project:

1. Sleep de map AdobeMobileLibrary naar uw project.
1. Zorg ervoor dat de `ADBMobileConfig.json` is een lid van uw doel.
1. Op de **[!UICONTROL Build Phases]** tabblad van het doel van uw tvOS-app, vouwt u de **[!UICONTROL Link Binary with Libraries]** en voeg de volgende bibliotheken toe:

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

Raadpleeg de documentatie bij iOS over [iOS](https://developer.apple.com/ios/resources/).

## Een TVML/TVJS-app voor tvOS configureren {#section_AB2EC8C326654F3387658EBBD990BB12}

1. Sleep de `AdobeMobileLibrary` in uw project.
1. Zorg ervoor dat de `ADBMobileConfig.json` is een lid van uw doel.
1. Op de **[!UICONTROL Build Phases]** tabblad van het doel van uw tvOS-app, vouwt u de **[!UICONTROL Link Binary with Libraries]** en voeg de volgende bibliotheken toe:

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. In het implementatiebestand van uw `TVApplicationControllerDelegate` -klasse, importeert u de SDK.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. In de `application:didFinishLaunchWithOptions:` van uw `TVApplicationControllerDelegate` klasse, geef uw `TVApplicationController` object naar de SDK met de `installTVMLHooks:` methode.

   De Adobe SDK heeft toegang nodig tot de `TVApplicationController` om zich te registreren bij de JSContext van uw app. Met deze stap kunt u de native methoden in de Adobe SDK aanroepen vanuit uw JavaScript-bestanden.

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. Gebruik in uw JavaScript-bestanden de opdracht `ADBMobile` -object voor toegang tot de native methoden van de Adobe SDK.

   Voor een volledig overzicht van de beschikbare methoden raadpleegt u [TVJS-methoden](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md).
