---
description: Met de volgende informatie kunt u een koppeling naar een verouderde acquisitiecampagne die is gebaseerd op een vingerafdruk van een apparaat, routeren.
seo-description: Met de volgende informatie kunt u een koppeling naar een verouderde acquisitiecampagne die is gebaseerd op een vingerafdruk van een apparaat, routeren.
seo-title: Verouderde overname testen
solution: Experience Cloud,Analytics
title: Verouderde overname testen
uuid: e0591f4a-e26b-4fe4-97c1-a6831a926fa5
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---


# Verouderde overname testen {#testing-legacy-acquisition}

Met de volgende informatie kunt u een koppeling naar een verouderde acquisitiecampagne die is gebaseerd op een vingerafdruk van een apparaat, routeren.

Als de mobiele app nog niet in Google Play is, kunt u elke mobiele app als doel selecteren wanneer u de koppeling voor de campagne maakt. Dit heeft alleen invloed op welke app de acquisitieserver u omleidt, nadat u op de acquisitie-koppeling hebt geklikt, en niet op de mogelijkheid om de acquisitie-koppeling te testen.

1. Navigeer naar **[!UICONTROL Use Legacy Acquisition Links]** in de Mobiele Diensten van Adobe en produceer een aanschafcampagne URL.

   Zie Koppelingen voor oudere [overnames](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md)gebruiken voor meer informatie.

1. Klik op de gegenereerde koppeling van het mobiele apparaat waarop u de toepassing wilt installeren.

   Adobe (`c00.adobe.com`) slaan de app op en leiden deze vervolgens om naar de App Store. De app hoeft niet te worden gedownload om te testen.

1. Start de toepassing voor het eerst op hetzelfde mobiele apparaat als dat u in stap 2 hebt gebruikt.

   U kunt dit het gemakkelijkst doen door de toepassing te verwijderen en opnieuw te installeren.

De volgende informatie onthouden:

* De verwervingsserver biedt een toewijzingsovereenkomst die is gebaseerd op IP-adres en gebruikersagent-informatie die is opgenomen in de koppelingsklik (stap 2) en wanneer de app wordt gestart (stap 3).
* Met de HTTP-controleprogramma&#39;s kunt u hits die vanuit de app worden verzonden controleren om de acquisitie-toewijzing te controleren.

>[!TIP]
>
>De variaties in verzonden user-agent zouden attributie kunnen veroorzaken om te ontbreken.
