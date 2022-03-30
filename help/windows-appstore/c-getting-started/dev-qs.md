---
description: Snel startartikel voor ontwikkelaar
solution: Experience Cloud Services,Analytics
title: Snelle start voor ontwikkelaars
topic-fix: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
exl-id: dd3262b1-e211-4758-9b4a-9dc7c4920c10
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---

# Snelle start voor ontwikkelaars {#developer-quick-start}

U zult Visual Studio 2013 of recenter nodig hebben om SDK uit te voeren.

## De SDK ophalen {#section_99FE1A17A36D4A2C943939023CF6265C}

Nadat u de [SDK downloaden](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases), hebt u een aparte map voor elke ondersteunde architectuur- en platformcombinatie. U hebt ook een `ADBMobileConfig.json` bestand dat verderop in deze handleiding wordt uitgelegd.

## Selecteer de juiste versie {#section_E53C5AA7D5474824A89BB32C003865A1}

Verschil `.dll`/ `.winmd` bestanden worden geleverd voor elk doelplatform (Windows 8.1, Windows Phone 8.1) en de ondersteunde architectuur (x86, x64, ARM). De bestanden worden als volgt in een mapstructuur gescheiden:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>De versie van `ADBMobile.winmd` geeft niet de versie van de bibliotheek weer. De `.winmd` bestand bevat alleen metagegevens en heeft daarom een versienummer van `255.255.255.255` die volgens Microsoft wordt geaccepteerd (zie [Hoe voeg ik assemblageinformatie voor een WinRT C++ / CX componentendll toe?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). Als u de versie van de bibliotheek die u gebruikt wilt controleren, controleert u de onderliggende versie `ADBMobile.dll` bestand.

## Syntaxisverschillen {#section_A02DE120B6D240F5AFFE7509755C4F14}

De Windows 8.1 Universal App Store-bibliotheek kan in verschillende programmeertalen worden gebruikt. De voorbeelden in deze gids zijn in WinJS (JavaScript), en zouden kunnen moeten worden gewijzigd als u een verschillende taal gebruikt. Wanneer u winde-methoden gebruikt vanuit winJS (JavaScript), wordt de eerste letter van alle methoden automatisch verlaagd.

Het belangrijkste verschil tussen de implementaties is de gegevensstructuur die wordt gebruikt voor contextgegevens.

Bovendien, wanneer het gebruiken van SDK in een project van WinJS, gebruik een leeg koord ( `""` of `''`) in plaats van `null` voor lege tekenreekswaarden.

## Voeg de bibliotheek en config dossier aan uw project toe - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Start Visual Studio en open uw oplossing.
1. In de **Solution Explorer**, klikt u met de rechtermuisknop **[!UICONTROL References]** en selecteert u **[!UICONTROL Add Reference]**.

1. Selecteer de juiste versie van de bibliotheek en blader naar de bijbehorende versie `ADBMobile.winmd` bestand.

   Zie voor meer informatie de *Selecteer de juiste versie* hieronder.

1. Klik op **[!UICONTROL Add]**.

1. Controleren of `ADBMobile.winmd` is geselecteerd in het dialoogvenster **[!UICONTROL Reference Manager]** venster en klik op **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Als u een verwijzing naar een Windows Phone-app toevoegt, selecteert u `ADBMobile.winmd`, wijzigt u het standaardbestandsfilter vanuit **[!UICONTROL Component Files]** tot **Alle bestanden**.

1. In de **[!UICONTROL Solution Explorer]**, klikt u met de rechtermuisknop **[!UICONTROL References]** en selecteert u **[!UICONTROL Add Reference]**.

   Sla deze stap over als u ook een C++ project in uw oplossing hebt.

1. In de **Windows** links, selecteert u **[!UICONTROL Extensions]**, selecteert en voegt **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Voeg de volgende regel toe aan de klasse:

   ```
   using ADBMobile;
   ```

1. Klik met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Bladeren naar uw `ADBMobileConfig.json` bestand en klik op **[!UICONTROL Add]**.

1. Klik met de rechtermuisknop op de knop `ADBMobileConfig.json` bestand in uw oplossing en selecteer **[!UICONTROL Properties]**.

1. Wijzigen **[!UICONTROL Build Action]** tot **[!UICONTROL Content]**.

## Voeg de bibliotheek en config dossier aan uw project toe - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Start Visual Studio en open uw oplossing.
1. In de **[!UICONTROL Solution Explorer]**, klikt u met de rechtermuisknop op uw project en selecteert u **[!UICONTROL Add]** > **[!UICONTROL References]**.

1. Selecteer de correcte versie van de bibliotheek en voeg dan een verwijzing naar bijbehorende toe `ADBMobile.winmd` bestand.

   Zie voor meer informatie de *De juiste versie selecteren* hieronder.

1. Klik op **[!UICONTROL Add]**.

1. In de **[!UICONTROL Reference Manager]** venster, controleer of `ADBMobile.winmd` is geselecteerd en klikt u op **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Als u een verwijzing naar een Windows Phone-app toevoegt, selecteert u `ADBMobile.winmd`, wijzigt u het standaardbestandsfilter vanuit **[!UICONTROL Component Files]** tot **Alle bestanden**.

1. Voeg de volgende regel toe aan de klasse:

   ```
   using namespace ADMS::Measurement;
   ```

1. Klik met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Bladeren naar de `ADBMobileConfig.json` bestand en klik op **[!UICONTROL Add]**.

1. Klik met de rechtermuisknop op de knop `ADBMobileConfig.json` bestand in uw oplossing en selecteer **[!UICONTROL Properties]**.

1. Op de **[!UICONTROL General]** tab, wijzigen **[!UICONTROL Content]** tot **[!UICONTROL Yes]** en klik op **[!UICONTROL OK]**.

## Voeg de bibliotheek en config dossier aan uw project toe - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Start Visual Studio en open uw oplossing.
1. In de **Solution Explorer**, klikt u met de rechtermuisknop **[!UICONTROL References]** en selecteert u **[!UICONTROL Add Reference]**.

   Zie voor meer informatie *De juiste versie selecteren* hieronder.

1. Selecteer de juiste versie van de bibliotheek en blader naar de bijbehorende versie `ADBMobile.winmd` bestand.

1. Klik op **[!UICONTROL Add]**.

1. Controleren of `ADBMobile.winmd` is ingecheckt in het dialoogvenster **[!UICONTROL Reference Manager]** venster en klik op **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Als u een verwijzing naar een Windows Phone-app toevoegt, selecteert u `ADBMobile.winmd`, wijzigt u het standaardbestandsfilter vanuit **[!UICONTROL Component Files]** tot **Alle bestanden**.

1. In de **[!UICONTROL Solution Explorer]**, klikt u met de rechtermuisknop **[!UICONTROL References]** en selecteert u **[!UICONTROL Add Reference]**.

   Sla deze stap over als u ook een C++ project in uw oplossing hebt.

1. In de **[!UICONTROL Windows]** links, selecteert u **[!UICONTROL Extensions]** en selecteren en toevoegen **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Klik met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Bladeren naar de `ADBMobileConfig.json` bestand en klik op **[!UICONTROL Add]**.

1. Klik met de rechtermuisknop op de knop `ADBMobileConfig.json]` bestand in uw oplossing en selecteer **[!UICONTROL Properties]**.

1. Met **[!UICONTROL File Properties]** geselecteerd, zorg ervoor **[!UICONTROL Package Action]** is ingesteld op **[!UICONTROL Content]**.

   Voor JavaScript-projecten wordt het bestand ingesteld op **[!UICONTROL Content]** standaard.

## Het configuratiebestand ADBMobileConfig.json bijwerken {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

De `ADBMobileConfig.json` Het bestand bevat algemene SDK-instellingen en bevindt zich in de hoofdmap van het project nadat u de stappen in het dialoogvenster *Het bibliotheek- en configuratiebestand toevoegen aan uw project* sectie. Als uw `ADBMobileConfig.json` Het bestand is niet vooraf geconfigureerd door Adobe Mobile Services. U moet een aantal waarden bijwerken om aan de slag te gaan.

Hieronder ziet u een voorbeeld van een `ADBMobileConfig.json` bestand:

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

* **Analyse**: `rsids` en `server`
* **Target**: `clientCode`
* **Publiek beheer**: `server`

Zie voor meer informatie [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md).

## Foutopsporing {#section_3A10376A60394A15BEE483323E0CD4AA}

Wanneer u het zuiveren voor SDK wilt toelaten, moet u roepen `ADBMobile.Config.setDebugLogging(true);`.

Voor C Sharp- en JS-toepassingen moet u foutopsporing van native code inschakelen door de volgende stappen uit te voeren (native foutopsporing van code is de standaardinstelling voor C++-toepassingen):

### C Sharp

Klik met de rechtermuisknop op het project en selecteer **[!UICONTROL Properties]** > **[!UICONTROL Debug tab]**. Selecteer in de vervolgkeuzelijst met foutopsporing de optie **[!UICONTROL Native Only]**.

### JS

Klik met de rechtermuisknop op het project en selecteer  **[!UICONTROL Properties]** > **[!UICONTROL Configuration Properties]** > **[!UICONTROL Debug tab]**. De keuzelijst voor het foutopsporingstype wijzigen in **Alleen native**.

Dat is het! U kunt nu Analytics, Target en Audience Management implementeren in uw Windows 8.1 Universal App Store-app.
