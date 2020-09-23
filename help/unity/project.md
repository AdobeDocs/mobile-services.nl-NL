---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Uw project maken
solution: Experience Cloud
title: Uw project maken
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 4%

---


# Uw project maken{#building-your-project}

## iOS

Wanneer u voor iOS bouwt, wordt een Project van Xcode gecreeerd. Standaard staan de bibliotheken `ADBMobileWrapper.mm` en `AdobeMobileLibrary.a` bestanden in de groep Bibliotheken van uw nieuwe project. Voer de volgende handmatige stappen uit die u nodig hebt om uw app te maken:

1. Voeg uw `ADBMobileConfig.json` dossier aan het project toe.

   Ervoor zorgen dat het lid is van de bouw van eventueel noodzakelijke doelen.

1. Voeg op het **[!UICONTROL Build Phases]** tabblad van uw project een koppeling toe naar de volgende bibliotheken:

   * `SystemConfiguration.framework`
(Deze bibliotheek is mogelijk al gekoppeld.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>Als u lokale berichten voor meldingen in de app van de SDK wilt gebruiken, moet u `ADBMobile.EnableLocalNotifications();` de methode Start in de eerste Unity-scène aanroepen.

## Android

Wanneer u voor Android ontwikkelt, bevat het `apk` bestand al het `ADBMobileConfig.json` bestand op de juiste locatie. Standaard wordt ook het `AndroidManifest.xml` bestand in uw `/Plugins/Android` map gebruikt.

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
