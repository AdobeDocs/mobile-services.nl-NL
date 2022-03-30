---
description: Informatie over hoe te om de Universele bibliotheek van het Platform van Vensters uit te voeren.
solution: Experience Cloud Services,Analytics
title: Snelle start voor ontwikkelaars
topic-fix: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
exl-id: 28fc2a96-907e-41fc-a798-3e8d43fc7616
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 1%

---

# Snelle start voor ontwikkelaars{#developer-quick-start}

Hier is wat informatie over hoe te om de Universele bibliotheek van het Platform van Vensters uit te voeren.

>[!IMPORTANT]
>
>Om SDK uit te voeren, hebt u Visual Studio 2013 of recenter nodig.

## De SDK ophalen {#section_99FE1A17A36D4A2C943939023CF6265C}

Nadat u de [SDK downloaden](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) , hebt u een aparte map voor elke ondersteunde architectuur- en platformcombinatie. U hebt ook een `ADBMobileConfig.json` bestand. Voor meer informatie over dit bestand raadpleegt u [ADBMobileConfig.json-configuratiebestand](/help/universal-windows/c-configuration/c.json.md).

## Selecteer de juiste versie {#section_E53C5AA7D5474824A89BB32C003865A1}

Verschil `.dll/.winmd` bestanden worden geleverd voor elke ondersteunde architectuur (x86, x64, ARM).

>[!IMPORTANT]
>
>De versie van `ADBMobile.winmd` geeft niet de versie van de bibliotheek weer. De `.winmd` bestand bevat alleen metagegevens en heeft een versienummer `255.255.255.255`, wat volgens Microsoft wordt geaccepteerd. Zie voor meer informatie [Hoe voeg ik assemblageinformatie voor een WinRT C++ / CX componentendll toe?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). Als u de versie van de bibliotheek die u gebruikt wilt controleren, controleert u de onderliggende versie `ADBMobile.dll` bestand.

## Syntaxisverschillen {#section_A02DE120B6D240F5AFFE7509755C4F14}

De Universal Windows Platform-bibliotheek kan in verschillende programmeertalen worden gebruikt. De voorbeelden in deze gids zijn in WinJS (JavaScript), als u een verschillende taal gebruikt, zou kunnen moeten worden gewijzigd. Wanneer u winde methodes van winJS gebruikt, hebben alle methodes automatisch hun eerste brief verminderd.

Het belangrijkste verschil tussen de implementaties is de gegevensstructuur die wordt gebruikt voor contextgegevens. Bovendien, wanneer het gebruiken van SDK in een project van WinJS, gebruik een leeg koord ( `""` of `''`) in plaats van `null` voor lege tekenreekswaarden.

## Voeg de bibliotheek en config Dossier aan uw project toe - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Start Visual Studio en open uw oplossing.
1. In de **[!UICONTROL Solution Explorer]**, klikt u met de rechtermuisknop **[!UICONTROL References]** en selecteert u **[!UICONTROL Add Reference]**.

1. Selecteer de juiste versie van de bibliotheek en blader naar het bijbehorende bestand ADBMobile.winmd.

   Zie voor meer informatie *Selecteer de juiste versie* op deze pagina.

1. Klikken **Toevoegen**.

1. Controleer of het bestand ADBMobile.winmd is ingecheckt in het dialoogvenster **[!UICONTROL Reference Manager]** venster en klik op **[!UICONTROL OK]**.

1. In de **[!UICONTROL Solution Explorer]**, klikt u met de rechtermuisknop **[!UICONTROL References]** en selecteert u **[!UICONTROL Add Reference]**.

   Als u ook een C++ project in uw oplossing hebt, sla deze stap over.

1. In de **[!UICONTROL Windows]** links, selecteert u **[!UICONTROL Extensions]**, selecteren en toevoegen **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**.

1. Voeg de volgende regel toe aan de klasse:

   ```csharp
   using ADBMobile;
   ```

1. Klik met de rechtermuisknop op uw project en klik op **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Bladeren naar de `ADBMobileConfig.json` bestand en klik op **[!UICONTROL Add]**.

1. Klik met de rechtermuisknop op de knop `ADBMobileConfig.json` bestand in uw oplossing en selecteer **[!UICONTROL Properties]**.

1. Wijzigen **[!UICONTROL Build Action]** tot **[!UICONTROL Content]**.

## Voeg de bibliotheek en config dossier aan uw project toe - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Start Visual Studio en open uw oplossing.
1. In de **[!UICONTROL Solution Explorer]**, klikt u met de rechtermuisknop op uw project en selecteert u **[!UICONTROL Add]** > **[!UICONTROL References]**.

1. Selecteer de juiste versie van de bibliotheek en voeg een verwijzing naar het bijbehorende bestand ADBMobile.winmd toe.

   Zie voor meer informatie *Selecteer de juiste versie* op deze pagina.

1. Klik op **[!UICONTROL Add]**.

1. Controleren of `ADBMobile.winmd` is ingecheckt in het dialoogvenster **[!UICONTROL Reference Manager]** venster en klik op **[!UICONTROL OK]**.

1. Voeg de volgende regel toe aan de klasse:

   ```c++
   using namespace ADBMobile;
   ```

1. Klik met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Bladeren naar `ADBMobileConfig.json` bestand en klik op **[!UICONTROL Add]**.

1. Klik met de rechtermuisknop op de knop `ADBMobileConfig.json` bestand in uw oplossing en selecteer **[!UICONTROL Properties]**.

1. Op de **[!UICONTROL General]** tab, wijzigen **[!UICONTROL Content]** tot **[!UICONTROL Yes]** en klik op **[!UICONTROL OK]**.

## Voeg de bibliotheek en config dossier aan uw project toe - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Start Visual Studio en open uw oplossing.

1. In de **[!UICONTROL Solution Explorer]**, klikt u met de rechtermuisknop **[!UICONTROL References]** en selecteert u **[!UICONTROL Add Reference]**.

1. Selecteer de juiste versie van de bibliotheek en blader naar het bijbehorende bestand ADBMobile.winmd.

1. Klik op **[!UICONTROL Add]**.

1. Controleer of het bestand ADBMobile.winmd is ingecheckt in het dialoogvenster **[!UICONTROL Reference Manager]** venster en klik op **[!UICONTROL OK]**.

1. In de **[!UICONTROL Solution Explorer]**, klikt u met de rechtermuisknop **[!UICONTROL References]** en selecteert u **[!UICONTROL Add Reference]**.

   Als u ook een C++ project in uw oplossing hebt, sla deze stap over.

1. In de **[!UICONTROL Windows]** links, selecteert u **[!UICONTROL Extensions]** en selecteren en toevoegen **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**.

1. Klik met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Bladeren naar de `ADBMobileConfig.json` bestand en klik op **[!UICONTROL Add]**.

1. Klik met de rechtermuisknop op de knop `ADBMobileConfig.json` bestand in uw oplossing en selecteer **[!UICONTROL Properties]**.

1. Met **[!UICONTROL File Properties]** geselecteerd, zorg ervoor **[!UICONTROL Package Action]** is ingesteld op **[!UICONTROL Content]**.

   Voor JavaScript-projecten wordt het bestand standaard ingesteld op Inhoud.

## Het configuratiebestand ADBMobileConfig.json bijwerken {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

De `ADBMobileConfig.json` Het bestand bevat algemene SDK-instellingen en bevindt zich in de hoofdmap van het project nadat u de stappen in het dialoogvenster *Voeg de bibliotheek en config dossier aan uw project toe* sectie. Als uw `ADBMobileConfig.json` Het bestand is niet vooraf geconfigureerd door Adobe Mobile Services. U moet een aantal waarden bijwerken om aan de slag te gaan.

Hier is een voorbeeld van een `ADBMobileConfig.json` bestand:

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

* **Adobe Analytics**: `rsids` en `server`

* **Adobe Target**: `clientCode`

* **Adobe Audience Manager**: `server`

Zie voor meer informatie [Methoden van SDK](/help/universal-windows/c-configuration/methods.md).

## Foutopsporing {#section_3A10376A60394A15BEE483323E0CD4AA}

Om het zuiveren voor SDK toe te laten, vraag `ADBMobile.Config.setDebugLogging(true);`.

Voor C Sharp- en JavaScript-toepassingen moet u foutopsporing in native code inschakelen door de volgende stappen uit te voeren (native foutopsporing in code is de standaardinstelling voor C++-toepassingen):

### C Sharp

1. Klik met de rechtermuisknop op het project en klik op  **[!UICONTROL Properties]** > **[!UICONTROL Debug tab]**.

1. De keuzelijst voor het foutopsporingstype wijzigen in **Alleen native**.

### JavaScript

1. Klik met de rechtermuisknop op het project en klik op **[!UICONTROL Properties]** > **[!UICONTROL Configuration Properties]** > **[!UICONTROL Debug tab]**.

1. De keuzelijst voor het foutopsporingstype wijzigen in **[!UICONTROL Native Only]**.

Dat is het! U bent nu klaar om Analytics, Doel, en het Beheer van het Publiek in uw Universal Windows Platform app uit te voeren.
