---
description: 'null'
seo-description: 'null'
seo-title: Snelle start voor ontwikkelaars
solution: Marketing Cloud,Analytics
title: Snelle start voor ontwikkelaars
topic: Developer and implementation
uuid: 11c06fcf-d5e4-4858-9a4e-3bf66cdd2a48
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# Snelle start voor ontwikkelaars{#developer-quick-start}

Hier is wat informatie over hoe te om de Universele bibliotheek van het Platform van Vensters uit te voeren.

>[!IMPORTANT]
>
>Om SDK uit te voeren, hebt u Visual Studio 2013 of recenter nodig.

## De SDK ophalen {#section_99FE1A17A36D4A2C943939023CF6265C}

Nadat u het [SDK-downloadbestand](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) hebt uitgepakt, beschikt u over een aparte map voor elke ondersteunde architectuur- en platformcombinatie. U hebt ook een `ADBMobileConfig.json` bestand. Zie het configuratiebestand [](/help/universal-windows/c-configuration/c.json.md)ADBMobileConfig.json voor meer informatie over dit bestand.

## Selecteer de juiste versie {#section_E53C5AA7D5474824A89BB32C003865A1}

Er worden verschillende `.dll/.winmd` bestanden geleverd voor elke ondersteunde architectuur (x86, x64, ARM).

>[!IMPORTANT]
>
>De versie van de bibliotheek weerspiegelt `ADBMobile.winmd` niet de versie van de bibliotheek. Het `.winmd` bestand bevat alleen metagegevens en heeft een versienummer `255.255.255.255`, wat volgens Microsoft wordt geaccepteerd. Voor meer informatie, zie [hoe ik assemblageinformatie voor een WinRT C++ / CX componentendll toevoegt?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode). Controleer de versie van het onderliggende `ADBMobile.dll` bestand om de versie van de bibliotheek te controleren die u gebruikt.

## Syntaxisverschillen {#section_A02DE120B6D240F5AFFE7509755C4F14}

De Universal Windows Platform-bibliotheek kan in verschillende programmeertalen worden gebruikt. De voorbeelden in deze gids zijn in WinJS (JavaScript), als u een verschillende taal gebruikt, zou kunnen moeten worden gewijzigd. Wanneer u winde methodes van winJS gebruikt, hebben alle methodes automatisch hun eerste brief verminderd.

Het belangrijkste verschil tussen de implementaties is de gegevensstructuur die wordt gebruikt voor contextgegevens. Bovendien, wanneer het gebruiken van SDK in een project van WinJS, gebruik een leeg koord ( `""` of `''`) in plaats van `null` voor lege koordwaarden.

## Voeg de bibliotheek en config Dossier aan uw project toe - C# {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Start Visual Studio en open uw oplossing.
1. Klik in het **[!UICONTROL Solution Explorer]** dialoogvenster met de rechtermuisknop **[!UICONTROL References]** en selecteer **[!UICONTROL Add Reference]**.

1. Selecteer de juiste versie van de bibliotheek en blader naar het bijbehorende bestand ADBMobile.winmd.

   Zie *Selecteer de juiste versie* op deze pagina voor meer informatie.

1. Klik op **Toevoegen**.

1. Controleer of het bestand ADBMobile.winmd is ingeschakeld in het **[!UICONTROL Reference Manager]** venster en klik op **[!UICONTROL OK]**.

1. Klik in het **[!UICONTROL Solution Explorer]** dialoogvenster met de rechtermuisknop **[!UICONTROL References]** en selecteer **[!UICONTROL Add Reference]**.

   Als u ook een C++ project in uw oplossing hebt, sla deze stap over.

1. Selecteer op het **[!UICONTROL Windows]** tabblad links de optie **[!UICONTROL Extensions]**, selecteer deze en voeg deze toe **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**.

1. Voeg de volgende regel toe aan de klasse:

   ```csharp
   using ADBMobile;
   ```

1. Klik met de rechtermuisknop op uw project en klik op **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Blader naar het `ADBMobileConfig.json` bestand en klik op **[!UICONTROL Add]**.

1. Klik met de rechtermuisknop op het `ADBMobileConfig.json` bestand in de oplossing en selecteer **[!UICONTROL Properties]**.

1. Wijzigen **[!UICONTROL Build Action]** in **[!UICONTROL Content]**.

## Voeg de bibliotheek en config dossier aan uw project toe - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Start Visual Studio en open uw oplossing.
1. Klik in het **[!UICONTROL Solution Explorer]** deelvenster met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL References]**.

1. Selecteer de juiste versie van de bibliotheek en voeg een verwijzing naar het bijbehorende bestand ADBMobile.winmd toe.

   Zie *Selecteer de juiste versie* op deze pagina voor meer informatie.

1. Klik op **[!UICONTROL Add]**.

1. Controleer of `ADBMobile.winmd` is ingeschakeld in het **[!UICONTROL Reference Manager]** venster en klik op **[!UICONTROL OK]**.

1. Voeg de volgende regel toe aan de klasse:

   ```c++
   using namespace ADBMobile;
   ```

1. Klik met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Blader naar het `ADBMobileConfig.json` bestand en klik op **[!UICONTROL Add]**.

1. Klik met de rechtermuisknop op het `ADBMobileConfig.json` bestand in de oplossing en selecteer **[!UICONTROL Properties]**.

1. Ga naar het **[!UICONTROL General]** tabblad en **[!UICONTROL Content]** klik op **[!UICONTROL Yes]** **[!UICONTROL OK]**.

## Voeg de bibliotheek en config dossier aan uw project toe - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Start Visual Studio en open uw oplossing.

1. Klik in het **[!UICONTROL Solution Explorer]** dialoogvenster met de rechtermuisknop **[!UICONTROL References]** en selecteer **[!UICONTROL Add Reference]**.

1. Selecteer de juiste versie van de bibliotheek en blader naar het bijbehorende bestand ADBMobile.winmd.

1. Klik op **[!UICONTROL Add]**.

1. Controleer of het bestand ADBMobile.winmd is ingeschakeld in het **[!UICONTROL Reference Manager]** venster en klik op **[!UICONTROL OK]**.

1. Klik in het **[!UICONTROL Solution Explorer]** dialoogvenster met de rechtermuisknop **[!UICONTROL References]** en selecteer **[!UICONTROL Add Reference]**.

   Als u ook een C++ project in uw oplossing hebt, sla deze stap over.

1. Selecteer op het **[!UICONTROL Windows]** tabblad links de optie **[!UICONTROL Extensions]** en selecteer deze **[!UICONTROL Visual C++ 2015 Runtime for Universal Windows Platform Apps]**.

1. Klik met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Blader naar het `ADBMobileConfig.json` bestand en klik op **[!UICONTROL Add]**.

1. Klik met de rechtermuisknop op het `ADBMobileConfig.json` bestand in de oplossing en selecteer **[!UICONTROL Properties]**.

1. Zorg dat deze optie is **[!UICONTROL File Properties]** geselecteerd en **[!UICONTROL Package Action]** dat deze is ingesteld op **[!UICONTROL Content]**.

   Voor JavaScript-projecten wordt het bestand standaard ingesteld op Inhoud.

## Het configuratiebestand ADBMobileConfig.json bijwerken {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

Het `ADBMobileConfig.json` dossier bevat globale montages SDK en wordt gevestigd bij uw projectwortel nadat u de stappen in *voegt de bibliotheek en config dossier aan uw projectsectie* toe. Als uw `ADBMobileConfig.json` bestand niet vooraf is geconfigureerd door Adobe Mobile Services, moet u een aantal waarden bijwerken om aan de slag te gaan.

Hier volgt een voorbeeld van een `ADBMobileConfig.json` bestand:

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

* **Adobe-doel**: `clientCode`

* **Adobe Audience Manager**: `server`

Zie [SDK-methoden](/help/universal-windows/c-configuration/methods.md)voor meer informatie.

## Foutopsporing {#section_3A10376A60394A15BEE483323E0CD4AA}

Om het zuiveren voor SDK toe te laten, roep `ADBMobile.Config.setDebugLogging(true);`.

Voor C Sharp- en JavaScript-toepassingen moet u foutopsporing in native code inschakelen door de volgende stappen uit te voeren (native foutopsporing in code is de standaardinstelling voor C++-toepassingen):

### C Sharp

1. Klik met de rechtermuisknop op het project en klik op **[!UICONTROL Properties]** > **[!UICONTROL Debug tab]**.

1. Wijzig de vervolgkeuzelijst van het foutopsporingstype in Alleen **** native.

### JavaScript

1. Klik met de rechtermuisknop op het project en klik op **[!UICONTROL Properties]** > **[!UICONTROL Configuration Properties]** > **[!UICONTROL Debug tab]**.

1. Wijzig de vervolgkeuzelijst van het foutopsporingstype in **[!UICONTROL Native Only]**.

Dat is het! U kunt nu Analytics, Target en Audience Management implementeren in uw Universal Windows Platform-app.

