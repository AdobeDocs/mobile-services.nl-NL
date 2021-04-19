---
description: Met deze informatie kunt u Apple TV implementeren met tvOS.
seo-description: Met deze informatie kunt u Apple TV implementeren met tvOS.
seo-title: Apple TV-implementatie met tvOS
solution: Experience Cloud,Analytics
title: Apple TV-implementatie met tvOS
topic-fix: Developer and implementation
uuid: d1571ea2-a5de-4b96-a527-72abbf51fab8
exl-id: 35b7f02d-ae48-4c6f-9a3a-6d106a1026ad
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 1%

---

# Apple TV-implementatie met tvOS {#apple-tv-implementation-with-tvos}

Met deze informatie kunt u Apple TV implementeren met tvOS.

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze recentste documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar Adobe Experience Platform Launch om aan de slag te gaan.
* Ga naar [Github om te zien wat er in de SDK-opslagruimten van het Experience Platform staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Overzicht

Met Apple TV kunt u nu toepassingen maken die worden uitgevoerd in de systeemeigen tvOS-omgeving. U kunt een native app maken met behulp van verschillende frameworks in iOS, of u kunt uw app maken met XML-sjablonen en JavaScript.

>[!TIP]
>
>tvOS-ondersteuning is beschikbaar vanaf `AdobeMobileLibrary` versie 4.7.0.

## Aan de slag {#section_CAB40A5B5FC745068C8A5DF8F9AB6199}

>[!TIP]
>
>We gaan ervan uit dat uw project een doel heeft dat een Apple TV-app is die zich richt op tvOS. Zie [tvOS](https://developer.apple.com/tvos/documentation/) voor meer informatie.

## Een native app voor tvOS configureren {#section_5095F19B3C4545F68E8C1E37A7E303AE}

Voer de volgende stappen uit in uw Xcode-project:

1. Sleep de map AdobeMobileLibrary naar uw project.
1. Zorg ervoor dat het `ADBMobileConfig.json`-bestand lid is van uw doel.
1. Vouw op het tabblad **[!UICONTROL Build Phases]** van het doel van uw tvOS-app de sectie **[!UICONTROL Link Binary with Libraries]** uit en voeg de volgende bibliotheken toe:

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

Raadpleeg de documentatie bij iOS op [iOS](https://developer.apple.com/ios/resources/) voor meer informatie.

## Een TVML/TVJS-app voor tvOS configureren {#section_AB2EC8C326654F3387658EBBD990BB12}

1. Sleep de `AdobeMobileLibrary` omslag in uw project.
1. Zorg ervoor dat het `ADBMobileConfig.json`-bestand lid is van uw doel.
1. Vouw op het tabblad **[!UICONTROL Build Phases]** van het doel van uw tvOS-app de sectie **[!UICONTROL Link Binary with Libraries]** uit en voeg de volgende bibliotheken toe:

   * `AdobeMobileLibrary_TV.a`
   * `libsqlite3.0.tbd`
   * `SystemConfiguration.framework`

1. Importeer de SDK in het implementatiebestand van de klasse `TVApplicationControllerDelegate`.

   ```objective-c
   #import “ADBMobile.h"
   ```

1. Geef in de `application:didFinishLaunchWithOptions:`-methode van uw `TVApplicationControllerDelegate`-klasse uw `TVApplicationController`-object door aan de SDK met de methode `installTVMLHooks:`.

   De Adobe SDK heeft toegang nodig tot `TVApplicationController` van uw app om zich te registreren bij de JSContext van uw app. Met deze stap kunt u de native methoden in de Adobe SDK aanroepen vanuit uw JavaScript-bestanden.

   ```objective-c
   [ADBMobile installTVMLHooks:appController];
   ```

1. In uw JavaScript-bestanden gebruikt u het object `ADBMobile` om toegang te krijgen tot de native methoden van de Adobe SDK.

   Zie [TVJS-methoden](/help/ios/apple-tv-implementation-tvos/tvjs-methods.md) voor een volledig overzicht van de beschikbare methoden.
