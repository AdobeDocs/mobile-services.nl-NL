---
description: Met deze insteekmodule kunt u Android AppMeasurement-aanroepen verzenden vanuit uw PhoneGap-project.
keywords: android;library;mobile;sdk
seo-description: Met deze insteekmodule kunt u Android AppMeasurement-aanroepen verzenden vanuit uw PhoneGap-project.
seo-title: Overzicht van de PhoneGap-plug-in
solution: Experience Cloud,Analytics
title: Overzicht van de PhoneGap-plug-in
topic: Developer and implementation
uuid: c5c32357-d8df-458a-b0e8-e0c56040241d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 1%

---


# Overzicht van de PhoneGap-plug-in {#phonegap-plug-in}

Met deze insteekmodule kunt u Android AppMeasurement-aanroepen verzenden vanuit uw PhoneGap-project. Zie [PhoneGap om een PhoneGap-project te maken](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html).

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar Adobe Experience Platform Launch om aan de slag te gaan.
* Ga naar [Github om te zien wat er in de SDK-opslagruimten van het Experience Platform staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## De insteekmodule installeren met npm {#section_43229E57C16944C0B51531CB92089189}

Voer de volgende opdracht uit:

```java
cordova plugin add adobe-mobile-services
```

## De plug-in handmatig installeren {#section_EA1FD59C484D44878AB509954DEE6037}

## De plug-in opnemen

1. Sleep het `ADBMobile_PhoneGap.java` bestand naar de `src` map.

   Klik op dit bestand om het te verplaatsen **[!UICONTROL OK]**.

1. Sleep het `ADB_Helper.js` bestand naar de map met het `index.html` bestand

   Klik op dit bestand om het te verplaatsen **[!UICONTROL OK]**.

1. Open het `res/xml` bestand in de `config.xml` map en registreer een nieuwe insteekmodule door het volgende toe te voegen:

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   Als uw pakket bijvoorbeeld een naam krijgt, krijgt u de volgende `com.example.phonegaptest``android-package` waarde:

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## De bibliotheek AppMeturement opnemen

1. Zie De SDK [ophalen als u de bibliotheek AppMeasurement wilt downloaden](/help/android/getting-started/dev-qs.md).
1. Sleep het `adobeMobileLibrary.jar` bestand naar de `src` map.

   Klik op dit bestand om het te verplaatsen **[!UICONTROL OK]**.

1. Klik met de rechtermuisknop op het bestand ` adobeMobileLibrary.jar en selecteer **[!UICONTROL Add as Library]**.
1. Gebaseerd op de vereisten van uw project, ga de naam, het niveau, en de plaats voor de bibliotheek in.
1. Sleep het `ADBMobileConfig.json` bestand naar de `assets` map in de hoofdmap van de toepassing.
1. Bevestig dat u de hoofdtoepassing hebt geselecteerd en **niet** een toepassing in een toepassing.

   Klik op dit bestand om het te verplaatsen **[!UICONTROL OK]**.

## Toepassingsmachtigingen toevoegen

De bibliotheek AppMeturement vereist de volgende toestemmingen om gegevens te verzenden en offline het volgen vraag op te nemen:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

U voegt deze machtigingen toe door de volgende regels toe te voegen aan uw `AndroidManifest.xml` bestand, dat zich in de projectmap van de toepassing bevindt:

```xml
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

In-app berichten inschakelen:

Werk AndroidManifest.xml bij om de volledige het schermactiviteit te verklaren en de Handler van het Bericht toe te laten:

```java
<activity  
android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

Als u modale lay-out selecteert wanneer u een bericht maakt in mobiele Adobe-services, selecteert u een van de volgende thema&#39;s:

* `Theme.Translucent.NoTitleBar.Fullscreen`
* `Theme.Translucent.NoTitleBar`
* `Theme.Translucent`

Bijvoorbeeld:

```java
<activity 
android:name="com.adobe.mobile.MessageFullScreenActivity" 
android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

## Aangepaste tracering implementeren {#section_FD102B3CDAA4492FB04E56BF17E28663}

Voeg in `html` bestanden het volgende toe aan de `<head>` tag waarin u reeksspatiëring wilt gebruiken:

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

