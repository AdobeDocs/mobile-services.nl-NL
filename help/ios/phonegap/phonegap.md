---
description: Met deze insteekmodule kunt u iOS AppMeasurement-aanroepen vanuit uw PhoneGap-project verzenden.
keywords: phonegap
seo-description: Met deze insteekmodule kunt u iOS AppMeasurement-aanroepen vanuit uw PhoneGap-project verzenden.
seo-title: PhoneGap-plug-in
solution: Marketing Cloud,Analytics
title: PhoneGap-plug-in
topic: Developer and implementation
uuid: f88bcf10-1f9e-4c97-b348-40db797c9923
translation-type: tm+mt
source-git-commit: 517ae533864aebe9c6a20d877a9638d5d3e2a071

---


# PhoneGap-plug-in{#phonegap-plug-in}

Met deze insteekmodule kunt u iOS AppMeasurement-aanroepen vanuit uw PhoneGap-project verzenden.

## Nieuwe release van Adobe Experience Platform Mobile SDK

Op zoek naar informatie en documentatie over de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via het [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga om aan de slag te gaan naar Adobe Experience Platform Launch.
* Ga naar [Github om te zien wat er in de repositories van Experience Platform SDK staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Een PhoneGap-project maken

Zie [PhoneGap om een PhoneGap-project te maken](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html).

## De insteekmodule installeren met npm: {#section_43229E57C16944C0B51531CB92089189}

1. Voer de volgende opdracht uit:

   ```
   cordova plugin add adobe-mobile-services
   ```

## De plug-in handmatig installeren {#section_D53BA60D488C4DB8AD2BDF90439C180A}

### De bibliotheek AppMeturement opnemen

De AppMeasurement opnemen:

1. Sleep `ADBMobile_PhoneGap.h` en `ADBMobile_PhoneGap.m` naar de **[!UICONTROL Plugins]** map in uw Xcode-project.
1. Voer de volgende instellingen in:

   1. Selecteer **[!UICONTROL Copy items into destination group's folder (if needed)]**.
   1. Selecteer de doelen waarvoor u de code AppMeasurement wilt gebruiken.

1. Sleep `ADB_Helper.js` naar de `www` map in uw project.
1. Open in de `res/xml` `config.xml` map een nieuwe plug-in en registreer deze door het volgende toe te voegen:

   ```
   <feature name="ADBMobile_PhoneGap"> 
     <param name="ios-package" value="ADBMobile_PhoneGap" /> 
   </feature>
   ```

### Toepassingsmachtigingen toevoegen

De AppMeturement-bibliotheek vereist het volgende:

1. Start de Xcode-IDE en open uw app.
1. Sleep de **[!UICONTROL AdobeMobile]** map naar het Xcode-project en voer de volgende instellingen in:

   1. Selecteer **[!UICONTROL Copy items into destination group's folder (if needed)]**.
   1. Selecteer **[!UICONTROL Create groups for any added folders]**.
   1. Selecteer de doelen waar u de code AppMeasurement wilt gebruiken en klik **[!UICONTROL Finish]**.
   ![](assets/xcode-settings.png){width=&quot;672&quot;}

1. In the **[!UICONTROL Build Phases]** tab of your project’s target, expand the **[!UICONTROL Link Binary with Libraries]** section and add the following libraries:

   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Bevestig dat uw app zonder onverwachte fouten wordt gemaakt.

## Aangepaste tracering implementeren {#section_FD102B3CDAA4492FB04E56BF17E28663}

Voeg het volgende toe aan de `html` `<head>` tag in bestanden waar u tekstspatiëring wilt gebruiken:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

