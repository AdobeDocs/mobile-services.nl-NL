---
description: Met deze plug-in kunt u Adobe Analytics-aanroepen vanuit uw eenheidstoepassingen verzenden.
keywords: Eenheid
solution: Experience Cloud Services
title: Insteekmodule Unity voor de iOS en Android 4.x SDK's
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
exl-id: fdb012d0-64f5-4c63-96d7-508fef01041f
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 4%

---

# Insteekmodule Unity voor de iOS en Android 4.x SDK&#39;s {#unity-plug-in-for-the-ios-and-android-x-sdks}

Met deze plug-in kunt u Adobe Analytics-aanroepen vanuit uw eenheidstoepassingen verzenden.

Laatste update: **10 maart 2020**
* [Unity-v4.19.0](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases/tag/v4.19.0-Unity)

## Aan de slag {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

Download het bestand ADBMobile.unitypackage van GitHub.

Hieronder vindt u de inhoud van het `ADBMobile.unitypackage` bestand:

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


**Optionele mappen**: De *Demo* map bevat Unity-scènes en voorbeeldcode.

## De insteekmodule ADBMobile importeren in uw project Unity {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Open uw project van de Eenheid.
1. Dubbelklikken **[!UICONTROL ADBMobile.unitypackage]**.
1. Selecteer de mappen die u wilt importeren.
