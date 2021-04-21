---
description: iOS-projecten maken
keywords: Eenheid
solution: Experience Cloud
title: Uw project maken
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
exl-id: 9da99392-b34e-4e36-b255-f3787e26015c
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 3%

---

# Uw project maken{#building-your-project}

## iOS

Wanneer u voor iOS bouwt, wordt een Project van Xcode gecreeerd. Standaard bevinden de `ADBMobileWrapper.mm`- en `AdobeMobileLibrary.a`-bestanden zich in de groep Bibliotheken van uw nieuwe project. Voer de volgende handmatige stappen uit die u nodig hebt om uw app te maken:

1. Voeg uw `ADBMobileConfig.json` dossier aan het project toe.

   Ervoor zorgen dat het lid is van de bouw van eventueel noodzakelijke doelen.

1. Voeg op het tabblad **[!UICONTROL Build Phases]** van uw project een koppeling toe naar de volgende bibliotheken:

   * `SystemConfiguration.framework`
(Deze bibliotheek is mogelijk al gekoppeld.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>Als u lokale berichten voor meldingen in de app van de SDK wilt gebruiken, moet u `ADBMobile.EnableLocalNotifications();` vanuit de methode Start in de eerste Unity-scène aanroepen.

## Android

Wanneer u voor Android bouwt, omvat het `apk` dossier reeds `ADBMobileConfig.json` dossier in de correcte plaats. Standaard wordt ook het `AndroidManifest.xml`-bestand in de map `/Plugins/Android` gebruikt.

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
