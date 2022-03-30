---
description: Deze Uitbreidingen verstrekken u een veel gemakkelijkere manier om de verwijzing van de Vensters SDK van de Oplossingen 4.x van Experience Cloud in uw project toe te voegen.
solution: Experience Cloud Services,Analytics
title: Windows Visual Studio-extensies voor Experience Cloud Solutions 4.x SDK
topic-fix: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
exl-id: 63e9e5c7-2a12-47b3-a712-bf51e12821aa
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# Windows Visual Studio-extensies voor Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Deze Uitbreidingen verstrekken u een veel gemakkelijkere manier om de verwijzing van de Vensters SDK van de Oplossingen 4.x van Experience Cloud in uw project toe te voegen.

## De bibliotheek van GitHub installeren {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Download de Windows Universal SDK van [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Pak het gedownloade bestand lokaal uit.
1. Dubbelklik op het bestand ADBMobileWindowsStoreVSIX.vsix of ADBMobileWindowsPhoneVSIX.vsix om het installatieprogramma te openen.

1. Selecteren **[!UICONTROL Global Location]** en installeer de bibliotheek.

## Referenties toevoegen aan uw project {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Open uw Windows 8.1- of Windows Phone 8.1-project.
1. Open het dialoogvenster Reference Manager.

   ![](assets/ref_manager.png)

1. Op de **[!UICONTROL Extensions]** tabblad van Windows 8.1 of Windows Phone 8.1. Zoek en selecteer **[!UICONTROL Adobe Mobile SDK]**.
1. Klikken **[!UICONTROL OK]** om het op te slaan.

   De Adobe Mobile SDK wordt toegevoegd aan uw project en als dit nog niet is gebeurd, wordt de **[!UICONTROL Microsoft Visual C++ Runtime]** wordt ook toegevoegd.

1. Selecteer in Configuratiebeheer een type Platform en begin met het testen van de app.
