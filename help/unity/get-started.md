---
description: Met deze plug-in kunt u Adobe Analytics-aanroepen vanuit uw eenheidstoepassingen verzenden.
keywords: Eenheid
solution: Experience Cloud
title: Insteekmodule Unity voor de SDK's van iOS en Android 4.x
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
exl-id: fdb012d0-64f5-4c63-96d7-508fef01041f
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 4%

---

# Insteekmodule Unity voor de SDK&#39;s van iOS en Android 4.x {#unity-plug-in-for-the-ios-and-android-x-sdks}

Met deze plug-in kunt u Adobe Analytics-aanroepen vanuit uw eenheidstoepassingen verzenden.

Laatste update: **10 maart 2020**
* [Unity-v4.19.0](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases/tag/v4.19.0-Unity)

## Aan de slag {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

Download het bestand ADBMobile.unitypackage van GitHub.

Hieronder ziet u de inhoud van het `ADBMobile.unitypackage`-bestand:

* Elementen (basis)

   * ADBMobile

   * Plug-ins

      * ADBMobile.cs
      * Android

         * adobeMobileLibrary-{version}.jar
         * AndroidManifest.xml
         * elementen

            * ADBMobileConfig.json
      * iOS

         * ADBMobile.h
         * ADBMobileConfig.json
         * ADBMobileWrapper.h
         * ADBMobileWrapper.mm
         * AdobeMobileLibrary.a


**Optionele mappen**: De  ** map Demofolder bevat de scènes van de Eenheid en steekproefcode.

## De insteekmodule ADBMobile importeren in uw project Unity {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Open uw project van de Eenheid.
1. Dubbelklik op **[!UICONTROL ADBMobile.unitypackage]**.
1. Selecteer de mappen die u wilt importeren.
