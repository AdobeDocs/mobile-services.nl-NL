---
description: Met deze insteekmodule kunt u Android AppMeasurement-aanroepen verzenden vanuit uw PhoneGap-project.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Overzicht van de PhoneGap-plug-in
topic-fix: Developer and implementation
uuid: c5c32357-d8df-458a-b0e8-e0c56040241d
exl-id: ecd756ca-e333-4d28-bd1e-a75ffc6ebe22
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 1%

---

# Overzicht van de PhoneGap-plug-in {#phonegap-plug-in}

Met deze insteekmodule kunt u Android AppMeasurement-aanroepen verzenden vanuit uw PhoneGap-project. Als u een PhoneGap-project wilt maken, raadpleegt u [PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html).

## Nieuwe Adobe Experience Platform Mobile SDK-release

Op zoek naar informatie en documentatie met betrekking tot de SDK van Adobe Experience Platform Mobile? Klikken [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar Adobe Experience Platform Launch om aan de slag te gaan.
* Ga naar [Github: Adobe Experience Platform SDK&#39;s](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## De insteekmodule installeren met npm {#section_43229E57C16944C0B51531CB92089189}

Voer de volgende opdracht uit:

```java
cordova plugin add adobe-mobile-services
```

## De plug-in handmatig installeren {#section_EA1FD59C484D44878AB509954DEE6037}

## De plug-in opnemen

1. Sleep de `ADBMobile_PhoneGap.java` bestand naar uw `src` map.

   Als u dit bestand wilt verplaatsen, klikt u op **[!UICONTROL OK]**.

1. Sleep de `ADB_Helper.js` in de map met de `index.html` file

   Als u dit bestand wilt verplaatsen, klikt u op **[!UICONTROL OK]**.

1. In de `res/xml` map, opent u de `config.xml` een nieuwe plug-in te registreren en te registreren door het volgende toe te voegen:

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   Als uw pakket bijvoorbeeld een naam heeft `com.example.phonegaptest`, uw `android-package` de waarde zou als volgt zijn:

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## De bibliotheek AppMeturement opnemen

1. Zie voor informatie over het downloaden van de AppMeasurement-bibliotheek [De SDK ophalen](/help/android/getting-started/dev-qs.md).
1. Sleep de `adobeMobileLibrary.jar` bestand naar uw `src` map.

   Als u dit bestand wilt verplaatsen, klikt u op **[!UICONTROL OK]**.

1. Klik met de rechtermuisknop op de knop `adobeMobileLibrary.jar` bestand en selecteer **[!UICONTROL Add as Library]**.
1. Gebaseerd op de vereisten van uw project, ga de naam, het niveau, en de plaats voor de bibliotheek in.
1. Sleep de `ADBMobileConfig.json` bestand naar uw `assets` in de hoofdmap van de toepassing.
1. Bevestig dat u de hoofdtoepassing hebt geselecteerd en **niet** een toepassing in een toepassing.

   Als u dit bestand wilt verplaatsen, klikt u op **[!UICONTROL OK]**.

## Toepassingsmachtigingen toevoegen

De bibliotheek AppMeturement vereist de volgende toestemmingen om gegevens te verzenden en offline het volgen vraag op te nemen:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

Voeg de volgende regels toe aan uw `AndroidManifest.xml` bestand, dat zich in de projectmap van de toepassing bevindt:

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

In `html` bestanden, voeg het volgende toe aan de `<head>` -tag waar u reeksspatiëring wilt gebruiken:

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```
