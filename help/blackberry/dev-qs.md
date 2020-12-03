---
title: Snel starten voor ontwikkelaar
seo-title: BlackBerry Developer Quick Start voor Adobe Mobile Services
description: Met de BlackBerry Developer Quick Start Guide krijgt u inzicht in het proces voor het implementeren van de BlackBerry-bibliotheek voor Adobe Mobile Services.
seo-description: Met de BlackBerry Developer Quick Start Guide krijgt u inzicht in het proces voor het implementeren van de BlackBerry-bibliotheek voor Adobe Mobile Services.
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 1%

---


# Snelle start voor ontwikkelaars

Deze informatie helpt u het proces begrijpen om de BlackBerry bibliotheek uit te voeren.

## De SDK ophalen

**De SDK vereist BlackBerry 10 of hoger.**

Nadat u de gedownloade SDK hebt uitgepakt, controleert u of de volgende bestanden in een `AdobeMobile` map staan:

* `Device-Coverage/libADBMobileShared.so`
* `Device-Debug/libADBMobileShared.so`
* `Device-Profile/libADBMobileShared.so`
* `Device-Release/libADBMobileShared.so`
* `public/ADBMediaAnalytics.hpp`
* `public/ADBMediaSharedHeader.hpp`
* `public/ADBMediaState.hpp`
* `public/ADBMobile.hpp`
* `Simulator-Coverage/libADBMobileShared.so`
* `Simulator-Debug/libADBMobileShared.so`
* `Simulator-Profile/libADBMobileShared.so`

## SDK&#39;s toevoegen aan uw project

1. Klik met de rechtermuisknop op uw project en selecteer **[!UICONTROL Configure]** > **[!UICONTROL Add Library]**.
1. Selecteer **[!UICONTROL External library]** en klik op **[!UICONTROL Next]**.
1. Klik **[!UICONTROL Browse]** naast het **[!UICONTROL Device library]** veld.
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. Selecteer in de `Device-Debug` map `libADBMobileShared.so` en klik op **[!UICONTROL Open]**.
1. Klik **[!UICONTROL Browse]** naast het **[!UICONTROL Simulator library]** veld.
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. Selecteer in de `Device-Debug` map `libADBMobileShared.so` en klik op **[!UICONTROL Open]**.
1. Klik **[!UICONTROL Add]** naast het **[!UICONTROL Include folders]** veld.
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. Voeg de `public` map toe aan uw include-bestanden.
1. In de `ADBMobile-4.0.0BETA-BlackBerry` omslag, is er een `.json` config dossier genoemd `ADBMobileConfig.json`.

   Kopieer dat bestand naar de hoofdmap van uw project.
1. Klik met de rechtermuisknop op uw project en selecteer **[!UICONTROL Refresh]**.

   Het `.json` bestand moet nu zichtbaar zijn in uw **[!UICONTROL Project Explorer]**.
1. Open het `bar-descriptor.xml` bestand voor uw project.
1. Selecteer onder aan het venster het **[!UICONTROL Assets]** tabblad.
1. Bevestig dat **[!UICONTROL (All Configurations)]** is geselecteerd en klik vervolgens op de knop **[!UICONTROL Add Files]** in het **[!UICONTROL Assets]** gedeelte van het venster.
   >[!TIP]
   >
   >Er is een probleem in QNX Momentics IDE dat soms voorkomt dat die knoppen zichtbaar zijn. Als u de knoppen niet kunt zien, wijzigt u de grootte van de vensters totdat deze worden weergegeven.

1. Klik op **[!UICONTROL Workspace]**.
1. Zoek het `ADBMobileConfig.json` bestand in uw project en klik op **[!UICONTROL OK]**.

Uw toepassing kan de klassen/interfaces van de `adobeMobileLibrary.jar` bibliotheek invoeren door te gebruiken `#include <ADBMobile.hpp>`.

## Toepassingsmachtigingen toevoegen

In `bar-descriptor.xml` de projectfolder, voeg de lijn toe `<permission>access_internet</permission>`, of in QNX Momentics winde, selecteer de **[!UICONTROL Internet]** doos op de toestemmingensectie van het **[!UICONTROL Application]** lusje.

## Het `ADBMobileConfig.json` configuratiebestand bijwerken

Het `ADBMobileConfig.json` bestand bevat algemene SDK-instellingen. U moet een paar waarden bijwerken om aan de slag te gaan.

Hieronder ziet u een voorbeeld van een `ADBMobileConfig.json` bestand:

```json
{
    "version" : "1.0",
    "analytics" : {
        "rsids" : "coolApp",
        "server" : "my.CoolApp.com",
        "charset" : "UTF-8",
        "ssl" : true,
        "offlineEnabled" : true,
        "lifecycleTimeout" : 5,
        "privacyDefault" : "optedin",
    }
}
```

U moet de parameters `rsids` en `server` parameters minstens bijwerken. Zie [Adobe Mobile-klasse en -methodeverwijzing](/help/blackberry/methods.md)voor meer informatie.

U kunt Analytics nu implementeren in uw BlackBerry 10-app.
