---
description: Met deze insteekmodule kunt u Android AppMeasurement-aanroepen verzenden vanuit uw PhoneGap-project.
keywords: android;bibliotheek;mobile;sdk
seo-description: Met deze insteekmodule kunt u Android AppMeasurement-aanroepen verzenden vanuit uw PhoneGap-project.
seo-title: Overzicht van de PhoneGap-plug-in
solution: Experience Cloud,Analytics
title: Overzicht van de PhoneGap-plug-in
topic-fix: Developer and implementation
uuid: c5c32357-d8df-458a-b0e8-e0c56040241d
exl-id: ecd756ca-e333-4d28-bd1e-a75ffc6ebe22
source-git-commit: bb2459e57274183e55c1facd1a510cf55a83ddb4
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 1%

---

# Overzicht van de insteekmodule PhoneGap {#phonegap-plug-in}

Met deze insteekmodule kunt u Android AppMeasurement-aanroepen verzenden vanuit uw PhoneGap-project. Zie [PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html) om een PhoneGap-project te maken.

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze recentste documentatie.

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

1. Sleep het `ADBMobile_PhoneGap.java` dossier aan uw `src` omslag.

   Klik op **[!UICONTROL OK]** om dit bestand te verplaatsen.

1. Sleep het `ADB_Helper.js`-bestand naar de map die het `index.html`-bestand bevat

   Klik op **[!UICONTROL OK]** om dit bestand te verplaatsen.

1. Open in de map `res/xml` het bestand `config.xml` en registreer een nieuwe plug-in door het volgende toe te voegen:

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   Als uw pakket bijvoorbeeld de naam `com.example.phonegaptest` heeft, is de waarde `android-package` als volgt:

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## De bibliotheek AppMeturement opnemen

1. Zie [SDK](/help/android/getting-started/dev-qs.md) ophalen om de AppMeturement-bibliotheek te downloaden.
1. Sleep het `adobeMobileLibrary.jar` dossier aan uw `src` omslag.

   Klik op **[!UICONTROL OK]** om dit bestand te verplaatsen.

1. Klik met de rechtermuisknop op het `adobeMobileLibrary.jar`-bestand en selecteer **[!UICONTROL Add as Library]**.
1. Gebaseerd op de vereisten van uw project, ga de naam, het niveau, en de plaats voor de bibliotheek in.
1. Sleep het `ADBMobileConfig.json` dossier aan uw `assets` omslag in de toepassingswortel.
1. Bevestig dat u de hoofdtoepassing en **not** een toepassing in een toepassing hebt geselecteerd.

   Klik op **[!UICONTROL OK]** om dit bestand te verplaatsen.

## Toepassingsmachtigingen toevoegen

De bibliotheek AppMeturement vereist de volgende toestemmingen om gegevens te verzenden en offline het volgen vraag op te nemen:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

Om deze toestemmingen toe te voegen, voeg de volgende lijnen aan uw `AndroidManifest.xml` dossier toe, dat in de folder van het toepassingsproject is:

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

Voeg in `html` bestanden het volgende toe aan de `<head>`-tag waarin u reeksspatiëring wilt gebruiken:

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```
