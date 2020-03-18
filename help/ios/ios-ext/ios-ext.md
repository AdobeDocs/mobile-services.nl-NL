---
description: Met de iOS-extensie kunt u gebruiksgegevens verzamelen van uw Apple Watch Apps (WatchOS 1), Today Widgets, Photo Editing widgets en andere iOS-extensies.
seo-description: Met de iOS-extensie kunt u gebruiksgegevens verzamelen van uw Apple Watch Apps (WatchOS 1), Today Widgets, Photo Editing widgets en andere iOS-extensies.
seo-title: iOS-extensie-implementatie
solution: Marketing Cloud,Analytics
title: iOS-extensie-implementatie
topic: Developer and implementation
uuid: 8afc03fe-403e-4643-ada1-30e403ede238
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# iOS-extensie-implementatie {#ios-extension-implementation}

Met de iOS-extensie kunt u gebruiksgegevens verzamelen van uw Apple Watch Apps (WatchOS 1), Today Widgets, Photo Editing widgets en andere iOS-extensies.

## Nieuwe release van Adobe Experience Platform Mobile SDK

Op zoek naar informatie en documentatie over de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via het [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga om aan de slag te gaan naar Adobe Experience Platform Launch.
* Ga naar [Github om te zien wat er in de repositories van Experience Platform SDK staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Aanbevelingen voor het gebruik van de iOS SDK in plaats van de wrapper {#section_97577331FD9E4FFBBE05D402C67AEE69}

>[!IMPORTANT]
>
>We raden u ten zeerste aan de iOS SDK te gebruiken in plaats van de wrapper.

Apple biedt een set API&#39;s waarmee de controletoepassing kan communiceren met de bevattende app door aanvragen naar de bevattende app te verzenden en de reacties te ontvangen. Hoewel u trackinggegevens als een woordenboek van de app van het Horloge naar de bevattende app kunt verzenden en elke trackingmethode op de bevattende app kunt aanroepen om de gegevens te verzenden, zijn er beperkingen ten aanzien van deze oplossing.

In de meeste gevallen wanneer een gebruiker de controletoepassing gebruikt, wordt de bevattende app op de achtergrond uitgevoerd en is het alleen veilig om te bellen `TrackActionInBackground`, `TrackLocation`en `TrackBeacon`. Het aanroepen van andere traceringsmethoden heeft invloed op de levenscyclusgegevens. U moet daarom alleen deze drie methoden gebruiken om de gegevens vanuit de controleapp te verzenden.

Zelfs als deze drie traceringsmethoden aan uw vereisten voldoen, gebruikt u de iOS SDK, omdat de SDK voor de app Watch alle mobiele functies bevat, behalve in-app messaging.

## Aan de slag {#section_D0BE4F780C9C4CD8ADD2AD4EE0BD5FD4}

>[!IMPORTANT]
>
>Zorg ervoor dat u een project hebt met minstens de volgende doelstellingen:
>
>* Eén doel dat de app moet bevatten.
>* Eén doel voor de extensie.
>



Als u aan een toepassing WatchKit werkt, moet u een derde doel hebben. Zie [Developing for Apple Watch](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/index.html#//apple_ref/doc/uid/TP40014969-CH8-SW1)voor meer informatie over het ontwikkelen voor Apple Watch.

## De bevattende app configureren {#section_0BAB0842E4C04A62B5E03DFC4BA77851}

Voer de volgende stappen uit in uw Xcode-project:

1. Sleep de map AdobeMobileLibrary naar uw project.
1. Zorg ervoor dat het `ADBMobileConfig.json` bestand lid is van het doel van de bevattende app.
1. On the **[!UICONTROL Build Phases]** tab of your containing app&#39;s target, expand the **[!UICONTROL Link Binary with Libraries]** section and add the following libraries:

   * `AdobeMobileLibrary.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Open het **[!UICONTROL Capabilities]** tabblad van het doel van de bevattende app, schakel **[!UICONTROL App Groups]** deze in en voeg een nieuwe toepassingsgroep toe (bijvoorbeeld `group.com.adobe.testAp`).

1. Stel in uw gedelegeerde toepassing de toepassingsgroep in `application:didFinishLaunchingWithOptions` voordat u interacties uitvoert met de Adobe Mobile-bibliotheek:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Bevestig dat uw app zonder onverwachte fouten wordt gemaakt.

## De extensie configureren {#section_28C994B7892340AC8D1F07AF26FF3946}

1. Zorg ervoor dat het `ADBMobileConfig.json` bestand lid is van het doel van de extensie.
1. On the **[!UICONTROL Build Phases]** tab of your extension’s target, expand the **[!UICONTROL Link Binary with Libraries]** section and add the following libraries:

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Open het **[!UICONTROL Capabilities]** tabblad van het doel van de extensie, schakel de app-groep in die u hebt toegevoegd in stap 4 van de bovenstaande **[!UICONTROL App Groups]** Inhoudsapp ** configureren.

1. Stel in uw InterfaceController de toepassingsgroep in `awakeWithContext:` voordat u andere interacties uitvoert met de Adobe Mobile-bibliotheek:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Bevestig dat uw app zonder onverwachte fouten wordt gemaakt.

## Aanvullende opmerkingen {#section_21497E81231549CB9F164DEECFF5BA0D}

Hier volgt een aantal informatie die u moet onthouden:

* Er `a.RunMode` is een extra waarde voor contextgegevens toegevoegd om aan te geven of de gegevens afkomstig zijn van de bevattende app of van uw extensie:

   * `a.RunMode = Application`

      Deze waarde betekent dat de hit afkomstig is van de bevattende app.
   * `a.RunMode = Extension`

      Deze waarde betekent dat de hit afkomstig is van de extensie.

* Als u een upgrade uitvoert van een oudere versie van de SDK en de bevattende app wordt gestart, migt Adobe automatisch alle standaardinstellingen van de gebruiker en in de cache opgeslagen bestanden van de map van de bevattende app naar de gedeelde map van de toepassingsgroep.
* Als de bevattende app nooit wordt gestart, worden hits van de extensie genegeerd.
* Het versienummer en het buildnummer moeten hetzelfde zijn tussen de bevattende app en de extensie-app.
* Er wordt geen levenscyclusaanroep gestart voor iOS-extensie-apps.

