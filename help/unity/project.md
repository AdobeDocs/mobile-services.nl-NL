---
description: iOS-projecten maken
keywords: Eenheid
solution: Experience Cloud Services
title: Uw project maken
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
exl-id: 9da99392-b34e-4e36-b255-f3787e26015c
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 3%

---

# Uw project maken{#building-your-project}

## iOS

Wanneer u voor iOS bouwt, wordt een Project van Xcode gecreeerd. Standaard worden de `ADBMobileWrapper.mm` en  `AdobeMobileLibrary.a` De bestanden worden opgenomen in de groep Bibliotheken van uw nieuwe project. Voer de volgende handmatige stappen uit die u nodig hebt om uw app te maken:

1. Voeg uw `ADBMobileConfig.json` aan het project.

   Ervoor zorgen dat het lid is van de bouw van eventueel noodzakelijke doelen.

1. In de **[!UICONTROL Build Phases]** voegt u een koppeling toe aan de volgende bibliotheken:

   * `SystemConfiguration.framework`
(Deze bibliotheek is mogelijk al gekoppeld.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>Als u Lokale berichten van de SDK voor meldingen in de app wilt gebruiken, moet u `ADBMobile.EnableLocalNotifications();` van de methode van het Begin in uw eerste Scène van de Eenheid.

## Android

Wanneer u voor Android ontwikkelt, worden de `apk` het bestand bevat al het `ADBMobileConfig.json` bestand op de juiste locatie. Standaard worden de `AndroidManifest.xml` in uw `/Plugins/Android` wordt ook gebruikt.

Als u uw eigen douane manifestdossier moet gebruiken, zouden de volgende veranderingen moeten worden toegevoegd.

Machtigingen toevoegen voor:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

```java
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Als u in-app overseinen gebruikt, voeg de volgende activiteit en ontvanger toe:

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" />
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```
