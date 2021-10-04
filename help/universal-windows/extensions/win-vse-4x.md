---
description: Deze Uitbreidingen verstrekken u een veel gemakkelijkere manier om de verwijzing van de Vensters SDK van de Oplossingen 4.x van Experience Cloud in uw project toe te voegen.
solution: Experience Cloud,Analytics
title: Windows Visual Studio-extensies voor Experience Cloud Solutions 4.x SDK
topic-fix: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
exl-id: 8ed91dc1-8f30-4788-8471-21bb54256b0b
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# Windows Visual Studio-extensies voor Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Deze uitbreiding verstrekt een veel gemakkelijkere manier om de verwijzing van de Vensters SDK van de Oplossingen 4.x van Experience Cloud in uw project toe te voegen.

## De bibliotheek van GitHub installeren {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Download de universele SDK van Vensters van [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Pak het gedownloade bestand lokaal uit.
1. Dubbelklik op het bestand **[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]** om het installatieprogramma te openen.
1. Selecteer **[!UICONTROL Global Location]** en installeer de bibliotheek.

## Referenties toevoegen aan uw project {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Open uw Windows 10-project.
1. Open het dialoogvenster Reference Manager.

   ![](assets/ref_manager.png)

1. Zoek en selecteer **[!UICONTROL Adobe Mobile SDK]** op het tabblad **[!UICONTROL Extensions]**.
1. Klik **[!UICONTROL OK]** om het te bewaren.

   De Adobe Mobile SDK wordt toegevoegd aan uw project. Als het **[!UICONTROL Microsoft Visual C++ Runtime]**-pakket nog niet is toegevoegd, wordt dit pakket ook toegevoegd aan uw project.

1. Selecteer in Configuratiebeheer een platformtype en begin met het testen van de app.
