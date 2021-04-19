---
description: 'null'
seo-description: 'null'
seo-title: Snelle start voor ontwikkelaars
solution: Experience Cloud,Analytics
title: Snelle start voor ontwikkelaars
topic-fix: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
exl-id: 28fc2a96-907e-41fc-a798-3e8d43fc7616
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 1%

---

# Snelle start voor ontwikkelaars{#developer-quick-start}

Hier is wat informatie over hoe te om de Universele bibliotheek van het Platform van Vensters uit te voeren.

>[!IMPORTANT]
>
>Om SDK uit te voeren, hebt u Visual Studio 2013 of recenter nodig.

## SDK {#section_99FE1A17A36D4A2C943939023CF6265C} ophalen

Nadat u het [SDK-download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)-bestand hebt uitgepakt, hebt u een aparte map voor elke ondersteunde architectuur- en platformcombinatie. U zult ook een `ADBMobileConfig.json` dossier hebben. Zie [ADBMobileConfig.json config-bestand](/help/universal-windows/c-configuration/c.json.md) voor meer informatie over dit bestand.

## Selecteer de juiste versie {#section_E53C5AA7D5474824A89BB32C003865A1}

Voor elke ondersteunde architectuur (x86, x64, ARM) zijn verschillende `.dll/.winmd`-bestanden beschikbaar.

>[!IMPORTANT]
>
>De versie van `ADBMobile.winmd` weerspiegelt niet de versie van de bibliotheek. Het `.winmd`-bestand bevat alleen metagegevens en heeft een versienummer van `255.255.255.255`, dat volgens Microsoft wordt geaccepteerd. Voor meer informatie, zie [Hoe voeg ik assemblageinformatie voor een WinRT C++ / CX componentendll toe?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). Om de versie van de bibliotheek te controleren u gebruikt, controleer de versie van het onderliggende `ADBMobile.dll` dossier.

## Syntaxisverschillen {#section_A02DE120B6D240F5AFFE7509755C4F14}

De Universal Windows Platform-bibliotheek kan in verschillende programmeertalen worden gebruikt. De voorbeelden in deze gids zijn in WinJS (JavaScript), als u een verschillende taal gebruikt, zou kunnen moeten worden gewijzigd. Wanneer u winde methodes van winJS gebruikt, hebben alle methodes automatisch hun eerste brief verminderd.

Het belangrijkste verschil tussen de implementaties is de gegevensstructuur die wordt gebruikt voor contextgegevens. Bovendien, wanneer het gebruiken van SDK in een project van WinJS, gebruik een lege koord ( `""` of `''`) in plaats van `null` voor lege koordwaarden.

## Voeg de bibliotheek en config Dossier aan uw project toe - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Start Visual Studio en open uw oplossing.
1. Klik in **[!UICONTROL Solution Explorer]** met de rechtermuisknop op **[!UICONTROL References]** en selecteer **[!UICONTROL Add Reference]**.

1. Selecteer de juiste versie van de bibliotheek en blader naar het bijbehorende bestand ADBMobile.winmd.

   Zie *De juiste versie* op deze pagina voor meer informatie.

1. Klik **Add**.

1. Controleer of het bestand ADBMobile.winmd is ingeschakeld in het venster **[!UICONTROL Reference Manager]** en klik op **[!UICONTROL OK]**.

1. Klik in **[!UICONTROL Solution Explorer]** met de rechtermuisknop op **[!UICONTROL References]** en selecteer **[!UICONTROL Add Reference]**.

   Als u ook een C++ project in uw oplossing hebt, sla deze stap over.

1. Selecteer **[!UICONTROL Extensions]** op het tabblad **[!UICONTROL Windows]** aan de linkerkant en selecteer **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]** en voeg  toe.

1. Voeg de volgende regel toe aan de klasse:

   ```csharp
   using ADBMobile;
   ```

1. Klik met de rechtermuisknop op uw project en klik op **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Blader naar het `ADBMobileConfig.json`-bestand en klik op **[!UICONTROL Add]**.

1. Klik met de rechtermuisknop op het `ADBMobileConfig.json`-bestand in de oplossing en selecteer **[!UICONTROL Properties]**.

1. Wijzig **[!UICONTROL Build Action]** in **[!UICONTROL Content]**.

## Voeg de bibliotheek en config dossier aan uw project toe - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Start Visual Studio en open uw oplossing.
1. Klik in **[!UICONTROL Solution Explorer]** met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL References]**.

1. Selecteer de juiste versie van de bibliotheek en voeg een verwijzing naar het bijbehorende bestand ADBMobile.winmd toe.

   Zie *De juiste versie* op deze pagina voor meer informatie.

1. Klik op **[!UICONTROL Add]**.

1. Controleer of `ADBMobile.winmd` is ingeschakeld in het venster **[!UICONTROL Reference Manager]** en klik op **[!UICONTROL OK]**.

1. Voeg de volgende regel toe aan de klasse:

   ```c++
   using namespace ADBMobile;
   ```

1. Klik met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Blader naar `ADBMobileConfig.json` bestand en klik op **[!UICONTROL Add]**.

1. Klik met de rechtermuisknop op het `ADBMobileConfig.json`-bestand in de oplossing en selecteer **[!UICONTROL Properties]**.

1. Wijzig **[!UICONTROL Content]** in **[!UICONTROL Yes]** op het tabblad **[!UICONTROL General]** en klik op **[!UICONTROL OK]**.

## Voeg de bibliotheek en config dossier aan uw project toe - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Start Visual Studio en open uw oplossing.

1. Klik in **[!UICONTROL Solution Explorer]** met de rechtermuisknop op **[!UICONTROL References]** en selecteer **[!UICONTROL Add Reference]**.

1. Selecteer de juiste versie van de bibliotheek en blader naar het bijbehorende bestand ADBMobile.winmd.

1. Klik op **[!UICONTROL Add]**.

1. Controleer of het bestand ADBMobile.winmd is ingeschakeld in het venster **[!UICONTROL Reference Manager]** en klik op **[!UICONTROL OK]**.

1. Klik in **[!UICONTROL Solution Explorer]** met de rechtermuisknop op **[!UICONTROL References]** en selecteer **[!UICONTROL Add Reference]**.

   Als u ook een C++ project in uw oplossing hebt, sla deze stap over.

1. Selecteer op het tabblad **[!UICONTROL Windows]** aan de linkerkant **[!UICONTROL Extensions]** en selecteer en voeg **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]** toe.

1. Klik met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Blader naar het `ADBMobileConfig.json`-bestand en klik op **[!UICONTROL Add]**.

1. Klik met de rechtermuisknop op het `ADBMobileConfig.json`-bestand in de oplossing en selecteer **[!UICONTROL Properties]**.

1. Selecteer **[!UICONTROL File Properties]** en zorg ervoor dat **[!UICONTROL Package Action]** is ingesteld op **[!UICONTROL Content]**.

   Voor JavaScript-projecten wordt het bestand standaard ingesteld op Inhoud.

## Het configuratiebestand ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE} bijwerken

Het `ADBMobileConfig.json` dossier bevat globale montages van SDK en wordt gevestigd bij uw projectwortel nadat u de stappen in *voeg de bibliotheek en configuratiedossier aan uw project* sectie toe. Als uw `ADBMobileConfig.json` dossier niet vooraf door de Mobiele Diensten van Adobe werd gevormd, moet u een paar waarden bijwerken om aan de slag te gaan.

Hier volgt een voorbeeld van een `ADBMobileConfig.json`-bestand:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
        "privacyDefault" : "optedin", 
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 1 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```

Werk minimaal de volgende waarden bij voor de oplossingen die u gebruikt:

* **Adobe Analytics**:  `rsids` en  `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

Zie [SDK-methoden](/help/universal-windows/c-configuration/methods.md) voor meer informatie.

## Foutopsporing {#section_3A10376A60394A15BEE483323E0CD4AA}

Om het zuiveren voor SDK toe te laten, roep `ADBMobile.Config.setDebugLogging(true);`.

Voor C Sharp- en JavaScript-toepassingen moet u foutopsporing in native code inschakelen door de volgende stappen uit te voeren (native foutopsporing in code is de standaardinstelling voor C++-toepassingen):

### C Sharp

1. Klik met de rechtermuisknop op het project en klik op **[!UICONTROL Properties]** > **[!UICONTROL Debug tab]**.

1. Wijzig de vervolgkeuzelijst van het foutopsporingstype in **Alleen native**.

### JavaScript

1. Klik met de rechtermuisknop op het project en klik op **[!UICONTROL Properties]** > **[!UICONTROL Configuration Properties]** > **[!UICONTROL Debug tab]**.

1. Wijzig de vervolgkeuzelijst van het foutopsporingstype in **[!UICONTROL Native Only]**.

Dat is het! U bent nu klaar om Analytics, Doel, en het Beheer van het Publiek in uw Universal Windows Platform app uit te voeren.
