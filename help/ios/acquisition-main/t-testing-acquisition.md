---
description: Met de volgende informatie kunt u een koppeling naar een verouderde acquisitiecampagne die is gebaseerd op een vingerafdruk van een apparaat, routeren.
solution: Experience Cloud Services,Analytics
title: Verouderde overname testen
uuid: e0591f4a-e26b-4fe4-97c1-a6831a926fa5
exl-id: 431dc400-952a-4515-9d14-ba2efef4b2c4
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Verouderde overname testen {#testing-legacy-acquisition}

Met de volgende informatie kunt u een koppeling naar een verouderde acquisitiecampagne die is gebaseerd op een vingerafdruk van een apparaat, routeren.

Als de mobiele app zich nog niet in Google Play bevindt, kunt u elke mobiele app als doel selecteren wanneer u de koppeling voor de campagne maakt. Dit heeft alleen invloed op welke app de acquisitieserver u omleidt, nadat u op de acquisitie-koppeling hebt geklikt, en niet op de mogelijkheid om de acquisitie-koppeling te testen.

1. Navigeren naar **[!UICONTROL Use Legacy Acquisition Links]** in Adobe Mobile Services en genereren een aankoopcampagne-URL.

   Zie voor meer informatie [Koppelingen voor verouderde overname gebruiken](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).

1. Klik op de gegenereerde koppeling van het mobiele apparaat waarop u de toepassing wilt installeren.

   Adobe`c00.adobe.com`) de vingerafdruk op te slaan en vervolgens om te leiden naar de App Store. De app hoeft niet te worden gedownload om te testen.

1. Start de toepassing voor het eerst op hetzelfde mobiele apparaat als dat u in stap 2 hebt gebruikt.

   U kunt dit het gemakkelijkst doen door de toepassing te verwijderen en opnieuw te installeren.

De volgende informatie onthouden:

* De verwervingsserver biedt een toewijzingsovereenkomst die is gebaseerd op IP-adres en gebruikersagent-informatie die is opgenomen in de koppelingsklik (stap 2) en wanneer de app wordt gestart (stap 3).
* Met de HTTP-controleprogramma&#39;s kunt u hits die vanuit de app worden verzonden controleren om de acquisitie-toewijzing te controleren.

>[!TIP]
>
>De variaties in verzonden user-agent zouden attributie kunnen veroorzaken om te ontbreken.
