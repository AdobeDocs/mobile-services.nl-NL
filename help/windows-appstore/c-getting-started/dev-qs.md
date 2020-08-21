---
description: 'null'
seo-description: 'null'
seo-title: Snelle start voor ontwikkelaars
solution: Marketing Cloud,Analytics
title: Snelle start voor ontwikkelaars
topic: Developer and implementation
uuid: b368959b-d985-436e-8b3e-97e355a97951
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 0%

---


# Snelle start voor ontwikkelaars {#developer-quick-start}

U zult Visual Studio 2013 of recenter nodig hebben om SDK uit te voeren.

## De SDK ophalen {#section_99FE1A17A36D4A2C943939023CF6265C}

Nadat u het downloaden [van de](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases)SDK hebt uitgerekt, beschikt u over een aparte map voor elke ondersteunde architectuur- en platformcombinatie. U hebt ook een `ADBMobileConfig.json` bestand dat later in deze handleiding wordt uitgelegd.

## Selecteer de juiste versie {#section_E53C5AA7D5474824A89BB32C003865A1}

Voor elk doelplatform (Windows 8.1, Windows Phone 8.1) en de ondersteunde architectuur (x86, x64, ARM) worden verschillende `.dll`/- `.winmd` bestanden geleverd. De bestanden worden als volgt in een mapstructuur gescheiden:

![](assets/folder-structure.png)

>[!IMPORTANT]
>
>De versie van de bibliotheek weerspiegelt `ADBMobile.winmd` niet de versie van de bibliotheek. Het `.winmd` dossier bevat slechts meta-gegevens, en als dusdanig zal een versieaantal hebben `255.255.255.255` waarvan gedrag volgens Microsoft wordt goedgekeurd (zie [hoe ik assemblageinformatie voor een WinRT C++ / CX componentendll voeg toe?](https://social.msdn.microsoft.com/Forums/windowsapps/en-US/6bcccaee-aa53-4770-bd5b-1205977f1ca7/how-do-i-add-assembly-information-for-a-winrt-c-cx-component-dll?forum=winappswithnativecode)). Controleer de versie van het onderliggende `ADBMobile.dll` bestand om de versie van de bibliotheek te controleren die u gebruikt.

## Syntaxisverschillen {#section_A02DE120B6D240F5AFFE7509755C4F14}

De Windows 8.1 Universal App Store-bibliotheek kan in verschillende programmeertalen worden gebruikt. De voorbeelden in deze gids zijn in WinJS (JavaScript), en zouden kunnen moeten worden gewijzigd als u een verschillende taal gebruikt. Wanneer u winde-methoden gebruikt vanuit winJS (JavaScript), wordt de eerste letter van alle methoden automatisch verlaagd.

Het belangrijkste verschil tussen de implementaties is de gegevensstructuur die wordt gebruikt voor contextgegevens.

Bovendien, wanneer het gebruiken van SDK in een project van WinJS, gebruik een leeg koord ( `""` of `''`) in plaats van `null` voor lege koordwaarden.

## Voeg de bibliotheek en config dossier aan uw project toe - C Sharp {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Start Visual Studio en open uw oplossing.
1. In de Ontdekkingsreiziger **van de** Oplossing, klik met de rechtermuisknop aan **[!UICONTROL References]** en selecteer **[!UIUCONTROL Voeg Verwijzing]** toe.

1. Selecteer de juiste versie van de bibliotheek en blader naar het bijbehorende `ADBMobile.winmd` bestand.

   Zie de sectie *Selecteer de juiste versie* hieronder voor meer informatie.

1. Klik op **[!UICONTROL Add]**.

1. Controleer of `ADBMobile.winmd` deze optie is geselecteerd in het **[!UICONTROL Reference Manager]** venster en klik op **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Als u een verwijzing naar een Windows Phone-toepassing toevoegt en deze selecteert, wijzigt u het standaardbestandsfilter van `ADBMobile.winmd`naar **[!UICONTROL Component Files]** Alle bestanden ****.

1. Klik in het **[!UICONTROL Solution Explorer]** dialoogvenster met de rechtermuisknop **[!UICONTROL References]** en selecteer **[!UICONTROL Add Reference]**.

   Sla deze stap over als u ook een C++ project in uw oplossing hebt.

1. Selecteer op het tabblad **Windows** aan de linkerkant de optie **[!UICONTROL Extensions]**, selecteer deze en voeg deze toe **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Voeg de volgende regel toe aan de klasse:

   ```
   using ADBMobile;
   ```

1. Klik met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Blader naar het `ADBMobileConfig.json` bestand en klik op **[!UICONTROL Add]**.

1. Klik met de rechtermuisknop op het `ADBMobileConfig.json` bestand in de oplossing en selecteer **[!UICONTROL Properties]**.

1. Wijzigen **[!UICONTROL Build Action]** in **[!UICONTROL Content]**.

## Voeg de bibliotheek en config dossier aan uw project toe - C++ {#section_A95C1D18F6144F37ADC8F51590F3983E}

1. Start Visual Studio en open uw oplossing.
1. Klik in het **[!UICONTROL Solution Explorer]** deelvenster met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL References]**.

1. Selecteer de juiste versie van de bibliotheek en voeg vervolgens een verwijzing naar het bijbehorende `ADBMobile.winmd` bestand toe.

   Zie de sectie *Selecteer de juiste versie* hieronder voor meer informatie.

1. Klik op **[!UICONTROL Add]**.

1. Controleer in het **[!UICONTROL Reference Manager]** venster of `ADBMobile.winmd` is geselecteerd en klik op **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Als u een verwijzing naar een Windows Phone-toepassing toevoegt en deze selecteert, wijzigt u het standaardbestandsfilter van `ADBMobile.winmd`naar **[!UICONTROL Component Files]** Alle bestanden ****.

1. Voeg de volgende regel toe aan de klasse:

   ```
   using namespace ADMS::Measurement;
   ```

1. Klik met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Blader naar het `ADBMobileConfig.json` bestand en klik op **[!UICONTROL Add]**.

1. Klik met de rechtermuisknop op het `ADBMobileConfig.json` bestand in de oplossing en selecteer **[!UICONTROL Properties]**.

1. Ga naar het **[!UICONTROL General]** tabblad en **[!UICONTROL Content]** klik op **[!UICONTROL Yes]****[!UICONTROL OK]**.

## Voeg de bibliotheek en config dossier aan uw project toe - WinJS {#section_FF83113EBF4742AFA929F4AC28F92DB5}

1. Start Visual Studio en open uw oplossing.
1. In de Ontdekkingsreiziger **van de** Oplossing, klik met de rechtermuisknop aan **[!UICONTROL References]** en selecteer **[!UICONTROL Add Reference]**.

   Zie *Selecteer de sectie Correcte versie* hieronder voor meer informatie.

1. Selecteer de juiste versie van de bibliotheek en blader naar het bijbehorende `ADBMobile.winmd` bestand.

1. Klik op **[!UICONTROL Add]**.

1. Controleer of `ADBMobile.winmd` is ingeschakeld in het **[!UICONTROL Reference Manager]** venster en klik op **[!UICONTROL OK]**.

   >[!TIP]
   >
   >Als u een verwijzing naar een Windows Phone-toepassing toevoegt en deze selecteert, wijzigt u het standaardbestandsfilter van `ADBMobile.winmd`naar **[!UICONTROL Component Files]** Alle bestanden ****.

1. Klik in het **[!UICONTROL Solution Explorer]** dialoogvenster met de rechtermuisknop **[!UICONTROL References]** en selecteer **[!UICONTROL Add Reference]**.

   Sla deze stap over als u ook een C++ project in uw oplossing hebt.

1. Selecteer op het **[!UICONTROL Windows]** tabblad links de optie **[!UICONTROL Extensions]** en selecteer deze **[!UICONTROL Microsoft Visual C++ 2013 Runtime Package for Windows]**.

1. Klik met de rechtermuisknop op uw project en selecteer **[!UICONTROL Add]** > **[!UICONTROL Existing Item]**.

1. Blader naar het `ADBMobileConfig.json` bestand en klik op **[!UICONTROL Add]**.

1. Klik met de rechtermuisknop op het `ADBMobileConfig.json]` bestand in de oplossing en selecteer **[!UICONTROL Properties]**.

1. Zorg dat deze optie is **[!UICONTROL File Properties]** geselecteerd en **[!UICONTROL Package Action]** dat deze is ingesteld op **[!UICONTROL Content]**.

   Voor JavaScript-projecten wordt het bestand standaard ingesteld op **[!UICONTROL Content]** .

## Het configuratiebestand ADBMobileConfig.json bijwerken {#section_0BC8CC0E4AAD4AC385FA0AEDC3C56AFE}

Het `ADBMobileConfig.json` bestand bevat algemene SDK-instellingen en bevindt zich in de hoofdmap van het project nadat u de stappen in het bestand Bibliotheek en Configuratie *toevoegen aan de sectie Project* hebt uitgevoerd. Als uw `ADBMobileConfig.json` bestand niet vooraf is geconfigureerd door Adobe Mobile Services, moet u een aantal waarden bijwerken om aan de slag te gaan.

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

Zie [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/methods.md)voor meer informatie.

## Foutopsporing {#section_3A10376A60394A15BEE483323E0CD4AA}

Wanneer u het zuiveren voor SDK wilt toelaten, moet u roepen `ADBMobile.Config.setDebugLogging(true);`.

Voor C Sharp- en JS-toepassingen moet u foutopsporing van native code inschakelen door de volgende stappen uit te voeren (native foutopsporing van code is de standaardinstelling voor C++-toepassingen):

### C Sharp

Klik met de rechtermuisknop op het project en selecteer **[!UICONTROL Properties]** > **[!UICONTROL Debug tab]**. Selecteer in de vervolgkeuzelijst met foutopsporing de optie **[!UICONTROL Native Only]**.

### JS

Klik met de rechtermuisknop op het project en selecteer **[!UICONTROL Properties]** > **[!UICONTROL Configuration Properties]** > **[!UICONTROL Debug tab]**. Wijzig de vervolgkeuzelijst van het foutopsporingstype in Alleen **** native.

Dat is het! U kunt nu Analytics, Target en Audience Management implementeren in uw Windows 8.1 Universal App Store-app.
