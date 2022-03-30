---
description: U kunt de extensie iOS gebruiken om gebruiksgegevens te verzamelen van uw Apple Watch-apps (WatchOS 1), Today-widgets, widgets voor fotobewerking en andere iOS-extensies.
solution: Experience Cloud Services,Analytics
title: iOS Extension Implementation
topic-fix: Developer and implementation
uuid: 8afc03fe-403e-4643-ada1-30e403ede238
exl-id: 741b0cd5-6245-480a-b5bf-a33a1f82a425
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# iOS-extensie-implementatie {#ios-extension-implementation}

U kunt de extensie iOS gebruiken om gebruiksgegevens te verzamelen van uw Apple Watch-apps (WatchOS 1), Today-widgets, widgets voor fotobewerking en andere iOS-extensies.

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de SDK van Adobe Experience Platform Mobile? Klikken [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar Adobe Experience Platform Launch om aan de slag te gaan.
* Ga naar [Github: Adobe Experience Platform SDK&#39;s](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Recommendations voor het gebruik van de iOS SDK in plaats van uw wrapper {#section_97577331FD9E4FFBBE05D402C67AEE69}

>[!IMPORTANT]
>
>We raden u ten zeerste aan de SDK van iOS te gebruiken in plaats van uw omslag.

Apple biedt een set API&#39;s waarmee de controletoepassing kan communiceren met de bevattende app door aanvragen naar de bevattende app te verzenden en de reacties te ontvangen. Hoewel u trackinggegevens als een woordenboek van de app van het Horloge naar de bevattende app kunt verzenden en elke trackingmethode op de bevattende app kunt aanroepen om de gegevens te verzenden, zijn er beperkingen ten aanzien van deze oplossing.

In de meeste gevallen wanneer een gebruiker de app Watch gebruikt, wordt de bevattende app op de achtergrond uitgevoerd en is het alleen veilig om te bellen `TrackActionInBackground`, `TrackLocation`, en `TrackBeacon`. Het aanroepen van andere traceringsmethoden heeft invloed op de levenscyclusgegevens. U moet daarom alleen deze drie methoden gebruiken om de gegevens vanuit de controleapp te verzenden.

Zelfs als deze drie traceringsmethoden aan uw vereisten voldoen, gebruikt u de SDK van iOS, omdat de SDK voor de app Watch alle Mobile-functies bevat, behalve in-app messaging.

## Aan de slag {#section_D0BE4F780C9C4CD8ADD2AD4EE0BD5FD4}

>[!IMPORTANT]
>
>Zorg ervoor dat u een project hebt met minstens de volgende doelstellingen:
>
>* Eén doel dat de app moet bevatten.
>* Eén doel voor de extensie.
>


Als u aan een toepassing WatchKit werkt, moet u een derde doel hebben. Ga voor meer informatie over het ontwikkelen voor Apple Watch naar [Ontwikkelen voor Apple Watch](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/index.html#//apple_ref/doc/uid/TP40014969-CH8-SW1).

## De bevattende app configureren {#section_0BAB0842E4C04A62B5E03DFC4BA77851}

Voer de volgende stappen uit in uw Xcode-project:

1. Sleep de map AdobeMobileLibrary naar uw project.
1. Zorg ervoor dat de `ADBMobileConfig.json` is een lid van het doel van de bevattende app.
1. Op de **[!UICONTROL Build Phases]** tabblad van het doel van de bevattende app uitvouwen **[!UICONTROL Link Binary with Libraries]** en voeg de volgende bibliotheken toe:

   * `AdobeMobileLibrary.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Open de **[!UICONTROL Capabilities]** tabblad van het doel van de bevattende app, inschakelen **[!UICONTROL App Groups]** en voeg een nieuwe toepassingsgroep toe (bijvoorbeeld `group.com.adobe.testAp`).

1. Stel in uw gedelegeerde toepassing de toepassingsgroep in `application:didFinishLaunchingWithOptions` voordat u interacties maakt met de Adobe Mobile-bibliotheek:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Bevestig dat uw app zonder onverwachte fouten wordt gemaakt.

## De extensie configureren {#section_28C994B7892340AC8D1F07AF26FF3946}

1. Zorg ervoor dat de `ADBMobileConfig.json` file is een lid van het doel van de uitbreiding.
1. Op de **[!UICONTROL Build Phases]** tabblad van het doel van de extensie, vouwt u de **[!UICONTROL Link Binary with Libraries]** en voeg de volgende bibliotheken toe:

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Open de **[!UICONTROL Capabilities]** tabblad van het doel van de extensie, inschakelen **[!UICONTROL App Groups]** en selecteer de toepassingsgroep die u hebt toegevoegd in stap 4 van *De bevattende app configureren* hierboven.

1. In uw InterfaceController, plaats de toepassingsgroep in `awakeWithContext:` voordat u andere interacties maakt met de Adobe Mobile-bibliotheek:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Bevestig dat uw app zonder onverwachte fouten wordt gemaakt.

## Aanvullende opmerkingen {#section_21497E81231549CB9F164DEECFF5BA0D}

Hier volgt een aantal informatie die u moet onthouden:

* Een extra waarde voor contextgegevens. `a.RunMode` is toegevoegd om aan te geven of de gegevens afkomstig zijn van uw bevattende app of uw extensie:

   * `a.RunMode = Application`

      Deze waarde betekent dat de hit afkomstig is van de bevattende app.
   * `a.RunMode = Extension`

      Deze waarde betekent dat de hit afkomstig is van de extensie.

* Als u een upgrade uitvoert van een oudere versie van de SDK en de bevattende app wordt gestart, migt Adobe automatisch alle standaardinstellingen van de gebruiker en in de cache opgeslagen bestanden van de map van de bevattende app naar de gedeelde map van de toepassingsgroep.
* Als de bevattende app nooit wordt gestart, worden hits van de extensie genegeerd.
* Het versienummer en het buildnummer moeten hetzelfde zijn tussen de bevattende app en de extensie-app.
* Er wordt geen levenscyclusaanroep gestart voor iOS-extensie-apps.
