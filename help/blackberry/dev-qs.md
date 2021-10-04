---
title: Snel starten voor ontwikkelaar
description: Met de BlackBerry Developer Quick Start Guide krijgt u inzicht in het proces voor het implementeren van de BlackBerry-bibliotheek voor Adobe Mobile Services.
exl-id: 65f39667-541a-4bbd-af9b-823638aa6f42
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 1%

---

# Snelle start voor ontwikkelaars

Deze informatie helpt u het proces begrijpen om de BlackBerry bibliotheek uit te voeren.

## De SDK ophalen

**De SDK vereist BlackBerry 10 of hoger.**

Nadat u de gedownloade SDK hebt uitgepakt, controleert u of de volgende bestanden aanwezig zijn in de map `AdobeMobile`:

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
1. Klik **[!UICONTROL Browse]** naast het **[!UICONTROL Device library]** gebied.
1. Navigeer naar de map `ADBMobile-4.0.0BETA-BlackBerry`.
1. Selecteer `Device-Debug` in de map `libADBMobileShared.so` en klik op **[!UICONTROL Open]**.
1. Klik **[!UICONTROL Browse]** naast het **[!UICONTROL Simulator library]** gebied.
1. Navigeer naar de map `ADBMobile-4.0.0BETA-BlackBerry`.
1. Selecteer `Device-Debug` in de map `libADBMobileShared.so` en klik op **[!UICONTROL Open]**.
1. Klik **[!UICONTROL Add]** naast het **[!UICONTROL Include folders]** gebied.
1. Navigeer naar de map `ADBMobile-4.0.0BETA-BlackBerry`.
1. Voeg de map `public` toe aan uw include-bestanden.
1. In de `ADBMobile-4.0.0BETA-BlackBerry` omslag, is er een `.json` configuratiedossier genoemd `ADBMobileConfig.json`.

   Kopieer dat bestand naar de hoofdmap van uw project.
1. Klik met de rechtermuisknop op uw project en selecteer **[!UICONTROL Refresh]**.

   Het `.json` bestand moet nu zichtbaar zijn in uw **[!UICONTROL Project Explorer]**.
1. Open het `bar-descriptor.xml` dossier voor uw project.
1. Selecteer onder aan het venster het tabblad **[!UICONTROL Assets]**.
1. Bevestig dat **[!UICONTROL (All Configurations)]** wordt geselecteerd, dan klik **[!UICONTROL Add Files]** in **[!UICONTROL Assets]** sectie van het venster.
   >[!TIP]
   >
   >Er is een probleem in QNX Momentics IDE dat soms voorkomt dat die knoppen zichtbaar zijn. Als u de knoppen niet kunt zien, wijzigt u de grootte van de vensters totdat deze worden weergegeven.

1. Klik op **[!UICONTROL Workspace]**.
1. Zoek het `ADBMobileConfig.json` dossier in uw project en klik **[!UICONTROL OK]**.

Uw toepassing kan de klassen/interfaces van de `adobeMobileLibrary.jar` bibliotheek invoeren door `#include <ADBMobile.hpp>` te gebruiken.

## Toepassingsmachtigingen toevoegen

Voeg in `bar-descriptor.xml` in de projectdirectory de regel `<permission>access_internet</permission>` toe, of selecteer in de QNX Momentics IDE de doos **[!UICONTROL Internet]** op de toestemmingensectie van **[!UICONTROL Application]** tabel.

## Het configuratiebestand `ADBMobileConfig.json` bijwerken

Het `ADBMobileConfig.json`-bestand bevat algemene SDK-instellingen. U moet een paar waarden bijwerken om aan de slag te gaan.

Hieronder ziet u een voorbeeld van een `ADBMobileConfig.json`-bestand:

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

U moet ten minste de parameters `rsids` en `server` bijwerken. Zie [Adobe Mobile-klasse en -methodereferentie](/help/blackberry/methods.md) voor meer informatie.

U kunt Analytics nu implementeren in uw BlackBerry 10-app.
