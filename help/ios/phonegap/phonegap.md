---
description: Met deze insteekmodule kunt u iOS AppMeasurement-aanroepen vanuit uw PhoneGap-project verzenden.
keywords: fonegap
solution: Experience Cloud,Analytics
title: PhoneGap-plug-in
topic-fix: Developer and implementation
uuid: f88bcf10-1f9e-4c97-b348-40db797c9923
exl-id: c20b2f85-b8d4-47c7-8177-106c7ddfe083
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 2%

---

# PhoneGap-plug-in{#phonegap-plug-in}

Met deze insteekmodule kunt u iOS AppMeasurement-aanroepen vanuit uw PhoneGap-project verzenden.

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze recentste documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar Adobe Experience Platform Launch om aan de slag te gaan.
* Ga naar [Github om te zien wat er in de SDK-opslagruimten van het Experience Platform staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Een PhoneGap-project maken

Zie [PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html) om een PhoneGap-project te maken.

## De insteekmodule installeren met npm: {#section_43229E57C16944C0B51531CB92089189}

1. Voer de volgende opdracht uit:

   ```
   cordova plugin add adobe-mobile-services
   ```

## De plug-in handmatig installeren {#section_D53BA60D488C4DB8AD2BDF90439C180A}

### De bibliotheek AppMeturement opnemen

De AppMeasurement opnemen:

1. Sleep `ADBMobile_PhoneGap.h` en `ADBMobile_PhoneGap.m` in **[!UICONTROL Plugins]** omslag in uw project Xcode.
1. Voer de volgende instellingen in:

   1. Selecteer **[!UICONTROL Copy items into destination group's folder (if needed)]**.
   1. Selecteer de doelen waarvoor u de code AppMeasurement wilt gebruiken.

1. Sleep `ADB_Helper.js` in de `www` omslag in uw project.
1. Open `config.xml` in de map `res/xml` en registreer een nieuwe plug-in door het volgende toe te voegen:

   ```
   <feature name="ADBMobile_PhoneGap"> 
     <param name="ios-package" value="ADBMobile_PhoneGap" /> 
   </feature>
   ```

### Toepassingsmachtigingen toevoegen

De AppMeturement-bibliotheek vereist het volgende:

1. Start de Xcode-IDE en open uw app.
1. Sleep de map **[!UICONTROL AdobeMobile]** naar uw Xcode-project en voer de volgende instellingen in:

   1. Selecteer **[!UICONTROL Copy items into destination group's folder (if needed)]**.
   1. Selecteer **[!UICONTROL Create groups for any added folders]**.
   1. Selecteer de doelstellingen waar u code AppMeasurement wilt gebruiken en **[!UICONTROL Finish]** klikken.

   ![](assets/xcode-settings.png){width=&quot;672&quot;}

1. Vouw op het tabblad **[!UICONTROL Build Phases]** van het doel van het project de sectie **[!UICONTROL Link Binary with Libraries]** uit en voeg de volgende bibliotheken toe:

   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Bevestig dat uw app zonder onverwachte fouten wordt gemaakt.

## Aangepaste tracering implementeren {#section_FD102B3CDAA4492FB04E56BF17E28663}

Voeg in `html` bestanden waar u tracking wilt gebruiken het volgende toe aan de tag `<head>`:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```
