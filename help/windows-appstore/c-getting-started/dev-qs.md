---
description: Snel startartikel voor ontwikkelaar
solution: Experience Cloud,Analytics
title: Snelle start voor ontwikkelaars
topic-fix: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
exl-id: dd3262b1-e211-4758-9b4a-9dc7c4920c10
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---

# Snelle start voor ontwikkelaars {#developer-quick-start}

U zult Visual Studio 2013 of recenter nodig hebben om SDK uit te voeren.

## SDK {#section_99FE1A17A36D4A2C943939023CF6265C} ophalen

Nadat u de [SDK-download](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) hebt uitgepakt, hebt u een aparte map voor elke ondersteunde architectuur- en platformcombinatie. U zult ook een `ADBMobileConfig.json` dossier hebben dat later in deze gids wordt verklaard.

## Selecteer de juiste versie {#section_E53C5AA7D5474824A89BB32C003865A1}

Er worden verschillende `.dll`/ `.winmd` bestanden geleverd voor elk doelplatform (Windows 8.1, Windows Phone 8.1) en ondersteunde architectuur (x86, x64, ARM). De bestanden worden als volgt in een mapstructuur gescheiden:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>De versie van `ADBMobile.winmd` weerspiegelt niet de versie van de bibliotheek. Het `.winmd` dossier bevat slechts meta-gegevens, en als dusdanig zal een versieaantal `255.255.255.255` hebben dat volgens Microsoft (zie [hoe ik assemblageinformatie voor een WinRT C++/CX componentendll toevoegt wordt goedgekeurd.](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). Om de versie van de bibliotheek te controleren u gebruikt, controleer de versie van het onderliggende `ADBMobile.dll` dossier.

## Syntaxisverschillen {#section_A02DE120B6D240F5AFFE7509755C4F14}

De Windows 8.1 Universal App Store-bibliotheek kan in verschillende programmeertalen worden gebruikt. De voorbeelden in deze gids zijn in WinJS (JavaScript), en zouden kunnen moeten worden gewijzigd als u een verschillende taal gebruikt. Wanneer u winde-methoden gebruikt vanuit winJS (JavaScript), wordt de eerste letter van alle methoden automatisch verlaagd.

Het belangrijkste verschil tussen de implementaties is de gegevensstructuur die wordt gebruikt voor contextgegevens.

Bovendien, wanneer het gebruiken van SDK in een project van WinJS, gebruik een lege koord ( `""` of `''`) in plaats van `null` voor lege koordwaarden.

## Voeg de bibliotheek en config dossier aan uw project toe - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Start Visual Studio en open uw oplossing.
1. In **de Ontdekkingsreiziger van de Oplossing**, klik **[!UICONTROL References]** met de rechtermuisknop aan en selecteer **[!UICONTROL Add Reference]**.

1. Selecteer de juiste versie van de bibliotheek en blader naar het bijbehorende `ADBMobile.winmd`-bestand.

   Zie de sectie *Selecteer de juiste versie* hieronder voor meer informatie.

1. Klik op **[!UICONTROL Add]**.

1. Controleer of `ADBMobile.winmd` is geselecteerd in het venster **[!UICONTROL Reference Manager]** en klik op **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Wanneer u een verwijzing naar een Windows Phone-app toevoegt en `ADBMobile.winmd` selecteert, wijzigt u het standaardbestandsfilter van **[!UICONTROL Component Files]** in **Alle bestanden**.

1. Klik in **[!UICONTROL Solution Explorer]** met de rechtermuisknop op **[!UICONTROL References]** en selecteer **[!UICONTROL Add Reference]**.

   Sla deze stap over als u ook een C++ project in uw oplossing hebt.

1. Selecteer op het tabblad **Windows** aan de linkerkant **[!UICONTROL Extensions]**, selecteer **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]** en voeg  toe.

1. Voeg de volgende regel toe aan de klasse:

   ```
   using ADBMobile;
   ```

1. Klik met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Blader naar het `ADBMobileConfig.json`-bestand en klik op **[!UICONTROL Add]**.

1. Klik met de rechtermuisknop op het `ADBMobileConfig.json`-bestand in de oplossing en selecteer **[!UICONTROL Properties]**.

1. Wijzig **[!UICONTROL Build Action]** in **[!UICONTROL Content]**.

## Voeg de bibliotheek en config dossier aan uw project toe - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Start Visual Studio en open uw oplossing.
1. Klik in **[!UICONTROL Solution Explorer]** met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL References]**.

1. Selecteer de correcte versie van de bibliotheek en voeg dan een verwijzing naar het bijbehorende `ADBMobile.winmd` dossier toe.

   Voor meer informatie, zie *Selecteer de Correcte sectie van Versie* hieronder.

1. Klik op **[!UICONTROL Add]**.

1. Controleer in het venster **[!UICONTROL Reference Manager]** of `ADBMobile.winmd` is geselecteerd en klik op **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Wanneer u een verwijzing naar een Windows Phone-app toevoegt en `ADBMobile.winmd` selecteert, wijzigt u het standaardbestandsfilter van **[!UICONTROL Component Files]** in **Alle bestanden**.

1. Voeg de volgende regel toe aan de klasse:

   ```
   using namespace ADMS::Measurement;
   ```

1. Klik met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Blader naar het `ADBMobileConfig.json`-bestand en klik op **[!UICONTROL Add]**.

1. Klik met de rechtermuisknop op het `ADBMobileConfig.json`-bestand in de oplossing en selecteer **[!UICONTROL Properties]**.

1. Wijzig **[!UICONTROL Content]** in **[!UICONTROL Yes]** op het tabblad **[!UICONTROL General]** en klik op **[!UICONTROL OK]**.

## Voeg de bibliotheek en config dossier aan uw project toe - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Start Visual Studio en open uw oplossing.
1. In **de Ontdekkingsreiziger van de Oplossing**, klik **[!UICONTROL References]** met de rechtermuisknop aan en selecteer **[!UICONTROL Add Reference]**.

   Zie *De sectie Correcte versie* hieronder voor meer informatie.

1. Selecteer de juiste versie van de bibliotheek en blader naar het bijbehorende `ADBMobile.winmd`-bestand.

1. Klik op **[!UICONTROL Add]**.

1. Controleer of `ADBMobile.winmd` is ingeschakeld in het venster **[!UICONTROL Reference Manager]** en klik op **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Wanneer u een verwijzing naar een Windows Phone-app toevoegt en `ADBMobile.winmd` selecteert, wijzigt u het standaardbestandsfilter van **[!UICONTROL Component Files]** in **Alle bestanden**.

1. Klik in **[!UICONTROL Solution Explorer]** met de rechtermuisknop op **[!UICONTROL References]** en selecteer **[!UICONTROL Add Reference]**.

   Sla deze stap over als u ook een C++ project in uw oplossing hebt.

1. Selecteer op het tabblad **[!UICONTROL Windows]** aan de linkerkant **[!UICONTROL Extensions]** en selecteer en voeg **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]** toe.

1. Klik met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Blader naar het `ADBMobileConfig.json`-bestand en klik op **[!UICONTROL Add]**.

1. Klik met de rechtermuisknop op het `ADBMobileConfig.json]`-bestand in de oplossing en selecteer **[!UICONTROL Properties]**.

1. Selecteer **[!UICONTROL File Properties]** en zorg ervoor dat **[!UICONTROL Package Action]** is ingesteld op **[!UICONTROL Content]**.

   Voor JavaScript-projecten wordt het bestand standaard ingesteld op **[!UICONTROL Content]**.

## Het configuratiebestand ADBMobileConfig.json {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE} bijwerken

Het `ADBMobileConfig.json` dossier bevat globale montages van SDK, en wordt gevestigd bij uw projectwortel nadat u de stappen in *voeg het Dossier van de Bibliotheek en Config aan uw Project* sectie voltooit. Als uw `ADBMobileConfig.json` dossier niet vooraf door de Mobiele Diensten van Adobe werd gevormd, moet u een paar waarden bijwerken om aan de slag te gaan.

Hieronder ziet u een voorbeeld van een `ADBMobileConfig.json`-bestand:

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

* **Analyse**:  `rsids` en  `server`
* **Target**: `clientCode`
* **Publiek beheer**:  `server`

Zie [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md) voor meer informatie.

## Foutopsporing {#section_3A10376A60394A15BEE483323E0CD4AA}

Wanneer u het zuiveren voor SDK wilt toelaten, moet u `ADBMobile.Config.setDebugLogging(true);` roepen.

Voor C Sharp- en JS-toepassingen moet u foutopsporing van native code inschakelen door de volgende stappen uit te voeren (native foutopsporing van code is de standaardinstelling voor C++-toepassingen):

### C Sharp

Klik met de rechtermuisknop op het project en selecteer **[!UICONTROL Properties]** > **[!UICONTROL Debug tab]**. Selecteer **[!UICONTROL Native Only]** in de vervolgkeuzelijst met foutopsporing.

### JS

Klik met de rechtermuisknop op het project en selecteer **[!UICONTROL Properties]** > **[!UICONTROL Configuration Properties]** > **[!UICONTROL Debug tab]**. Wijzig de vervolgkeuzelijst van het foutopsporingstype in **Alleen native**.

Dat is het! U kunt nu Analytics, Target en Audience Management implementeren in uw Windows 8.1 Universal App Store-app.
