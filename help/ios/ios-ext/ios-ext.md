---
description: Met de iOS-extensie kunt u gebruiksgegevens verzamelen van uw Apple Watch Apps (WatchOS 1), Today Widgets, Photo Editing widgets en andere iOS-extensies.
solution: Experience Cloud,Analytics
title: iOS-extensie-implementatie
topic-fix: Developer and implementation
uuid: 8afc03fe-403e-4643-ada1-30e403ede238
exl-id: 741b0cd5-6245-480a-b5bf-a33a1f82a425
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# iOS-extensie-implementatie {#ios-extension-implementation}

Met de iOS-extensie kunt u gebruiksgegevens verzamelen van uw Apple Watch Apps (WatchOS 1), Today Widgets, Photo Editing widgets en andere iOS-extensies.

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze recentste documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar Adobe Experience Platform Launch om aan de slag te gaan.
* Ga naar [Github om te zien wat er in de SDK-opslagruimten van het Experience Platform staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Recommendations voor het gebruik van de iOS SDK in plaats van uw wrapper {#section_97577331FD9E4FFBBE05D402C67AEE69}

>[!IMPORTANT]
>
>We raden u ten zeerste aan de iOS SDK te gebruiken in plaats van de wrapper.

Apple biedt een set API&#39;s waarmee de controletoepassing kan communiceren met de bevattende app door aanvragen naar de bevattende app te verzenden en de reacties te ontvangen. Hoewel u trackinggegevens als een woordenboek van de app van het Horloge naar de bevattende app kunt verzenden en elke trackingmethode op de bevattende app kunt aanroepen om de gegevens te verzenden, zijn er beperkingen ten aanzien van deze oplossing.

In de meeste gevallen wanneer een gebruiker de controletoepassing gebruikt, wordt de bevattende app op de achtergrond uitgevoerd en is het alleen veilig om `TrackActionInBackground`, `TrackLocation` en `TrackBeacon` aan te roepen. Het aanroepen van andere traceringsmethoden heeft invloed op de levenscyclusgegevens. U moet daarom alleen deze drie methoden gebruiken om de gegevens vanuit de controleapp te verzenden.

Zelfs als deze drie traceringsmethoden aan uw vereisten voldoen, gebruikt u de iOS SDK, omdat de SDK voor de app Watch alle mobiele functies bevat, behalve in-app messaging.

## Aan de slag {#section_D0BE4F780C9C4CD8ADD2AD4EE0BD5FD4}

>[!IMPORTANT]
>
>Zorg ervoor dat u een project hebt met minstens de volgende doelstellingen:
>
>* Eén doel dat de app moet bevatten.
>* Eén doel voor de extensie.

>


Als u aan een toepassing WatchKit werkt, moet u een derde doel hebben. Zie [Ontwikkelen voor Apple Watch](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/index.html#//apple_ref/doc/uid/TP40014969-CH8-SW1) voor meer informatie over het ontwikkelen voor Apple Watch.

## De bevattende app configureren {#section_0BAB0842E4C04A62B5E03DFC4BA77851}

Voer de volgende stappen uit in uw Xcode-project:

1. Sleep de map AdobeMobileLibrary naar uw project.
1. Zorg ervoor dat het `ADBMobileConfig.json`-bestand lid is van het doel van de bevattende app.
1. Vouw op het tabblad **[!UICONTROL Build Phases]** van het doel van de bevattende app de sectie **[!UICONTROL Link Binary with Libraries]** uit en voeg de volgende bibliotheken toe:

   * `AdobeMobileLibrary.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Open het tabblad **[!UICONTROL Capabilities]** van het doel van de bevattende app, schakel **[!UICONTROL App Groups]** in en voeg een nieuwe toepassingsgroep toe (bijvoorbeeld `group.com.adobe.testAp`).

1. Stel in uw gedelegeerde toepassing de toepassingsgroep in `application:didFinishLaunchingWithOptions` in voordat u interacties maakt met de mobiele Adobe-bibliotheek:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Bevestig dat uw app zonder onverwachte fouten wordt gemaakt.

## De extensie configureren {#section_28C994B7892340AC8D1F07AF26FF3946}

1. Zorg ervoor dat het `ADBMobileConfig.json`-bestand lid is van het doel van de extensie.
1. Vouw op het tabblad **[!UICONTROL Build Phases]** van het doel van de extensie de sectie **[!UICONTROL Link Binary with Libraries]** uit en voeg de volgende bibliotheken toe:

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Open het **[!UICONTROL Capabilities]** lusje van het doel van de uitbreiding, laat **[!UICONTROL App Groups]** toe, en selecteer de toepassingsgroep die u in stap 4 van *het Vormen van het Bevatten App* hierboven toevoegde.

1. In uw InterfaceController, plaats de toepassingsgroep in `awakeWithContext:` alvorens om het even welke andere interactie met de Mobiele bibliotheek van Adobe te maken:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Bevestig dat uw app zonder onverwachte fouten wordt gemaakt.

## Aanvullende opmerkingen {#section_21497E81231549CB9F164DEECFF5BA0D}

Hier volgt een aantal informatie die u moet onthouden:

* Er is een extra waarde voor contextgegevens toegevoegd, `a.RunMode` om aan te geven of de gegevens afkomstig zijn van de bevattende app of van uw extensie:

   * `a.RunMode = Application`

      Deze waarde betekent dat de hit afkomstig is van de bevattende app.
   * `a.RunMode = Extension`

      Deze waarde betekent dat de hit afkomstig is van de extensie.

* Als u een upgrade uitvoert van een oudere versie van de SDK en de bevattende app wordt gestart, migt Adobe automatisch alle standaardinstellingen van de gebruiker en in de cache opgeslagen bestanden van de map van de bevattende app naar de gedeelde map van de toepassingsgroep.
* Als de bevattende app nooit wordt gestart, worden hits van de extensie genegeerd.
* Het versienummer en het buildnummer moeten hetzelfde zijn tussen de bevattende app en de extensie-app.
* Er wordt geen levenscyclusaanroep gestart voor iOS-extensie-apps.
