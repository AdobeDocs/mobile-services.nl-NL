---
description: In dit onderwerp wordt beschreven hoe u aan de slag kunt met de Xamarin-componenten voor mobiele oplossingen 4.x SDK.
keywords: Xamarine
solution: Experience Cloud
title: Xamarin-componenten voor Experience Cloud Solutions 4.x SDK
uuid: e7a48107-bd0e-47d6-b49c-dfdae189ac37
exl-id: 39628548-5787-4022-8792-86b78214a1c0
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 4%

---

# Xamarin-componenten voor Experience Cloud Solutions 4.x SDK {#xamarin-components-for-experience-cloud-solutions-x-sdk}

In dit onderwerp wordt beschreven hoe u aan de slag kunt met de Xamarin-componenten voor mobiele oplossingen 4.x SDK.

Laatst bijgewerkt: **10 januari 2019**

## Aan de slag {#section_59D434C30C8F4765A7DEFE877D5268D0}

>[!IMPORTANT]
>
>Adobe Mobile SDK is niet meer beschikbaar in de Xamarin Components Store of in de NuGet Gallery. Om de componenten te downloaden Xamarin, ga naar [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services).

## Android {#section_9CAE1BFD359242568D8288C12A4B7A7D}

Importeer de component ADBMobile naar het project Xamarin.Android:

1. Uw Xamarin-project openen
1. Open **[!UICONTROL References]** en klik **[!UICONTROL .Net Assembly]** tabel.
1. Selecteer `ADBMobile.XamarinAndroidBinding.dll` in de map **[!UICONTROL lib/Android]**.
1. Voeg uw `ADBMobileConfig.json` dossier aan **[!UICONTROL Assets]** omslag van uw project toe.
1. Machtigingen toevoegen voor:

   * `INTERNET`
   * `ACCESS_NETWORK_STATE`

   ```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   ```

1. Als u in-app overseinen gebruikt, voeg de volgende activiteit en ontvanger toe:

   ```java
    <activity 
    android:name="com.adobe.mobile.MessageFullScreenActivity" 
    android:theme="@android:style/Theme.Translucent.NoTitleBar" />
    <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. Als u verwerving gebruikt, voegt u de volgende ontvanger toe:

   ```java
    <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true">
    <intent-filter>
        <action android:name="com.android.vending.INSTALL_REFERRER" />
    </intent-filter>
    </receiver>
   ```

## iOS {#section_1531928DDE904D769B3987BF927D0E02}

Importeer de ADBMobile-component naar het Xamarin.iOS-project:

1. Open uw Xamarin-project.
1. Open **[!UICONTROL References]** en klik **[!UICONTROL .Net Assembly]** tabel.
1. Selecteer `ADBMobile.XamarinIOSBinding.dll` in de map **[!UICONTROL lib/ios-unified]**.
1. Voeg uw `ADBMobileConfig.json` dossier aan het project toe.
