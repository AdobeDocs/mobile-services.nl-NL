---
description: U kunt interessante punten maken en beheren, waarmee u geografische locaties kunt definiëren die u kunt gebruiken voor correlatiedoeleinden, u kunt richten op berichten in de app, enzovoort. Wanneer een treffer wordt verzonden in een belangenpunt, wordt het aandachtspunt verbonden aan de treffer.
keywords: mobiel
solution: Experience Cloud Services,Analytics
title: Belangenpunten beheren
topic-fix: Metrics
uuid: 7b362534-54fb-43a3-b6b2-dfc8f45ff7c6
exl-id: 9598b06b-fb6a-436c-811c-f74015cc2ab0
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 1%

---

# Belangenpunten beheren {#manage-points-of-interest}

U kunt POI&#39;s maken en beheren, waarmee u geografische locaties kunt definiëren die u kunt gebruiken voor correlatiedoeleinden, als doel kunt instellen voor berichten in de app, enzovoort. Wanneer een hit wordt verzonden in een POI, wordt de POI aan de hit gekoppeld.

Controleer voordat u Locatie kunt gebruiken de volgende vereisten:

* U moet beschikken over Analytics - Mobile Apps of Analytics Premium.
* U moet **[!UICONTROL Location Reports]** voor de app.
* Als u een versie van de SDK van iOS of Android gebruikt die ouder is dan versie 4.2, voegt u na het toevoegen van nieuwe **[!UICONTROL Points of Interest]**, moet u een nieuw configuratiebestand downloaden en dit aan de ontwikkelaars van uw app geven.

   Als u de iOS SDK of Android SDK versie 4.2 of hoger gebruikt, hoeft u geen app-update naar de winkel te verzenden om uw **[!UICONTROL Points of Interest]**. Klik op de pagina Punten beheren als u op **[!UICONTROL Save]**, worden de wijzigingen in het pakket opgenomen **[!UICONTROL Points of Interest]** en het configuratiebestand voor de live app wordt bijgewerkt. Wanneer u de lijst met punten in uw app opslaat op de gebruikersapparaten, werkt u deze ook bij zolang de app de bijgewerkte SDK en de configuratie met een externe POI-URL gebruikt.

Op het apparaat van de gebruiker, voor een klap die aan een **[!UICONTROL Points of Interest]**, moet de locatie voor de app zijn ingeschakeld.

Voer de volgende taken uit om Locatie te gebruiken:

1. Klik op de naam van de toepassing om naar de pagina Toepassingsinstellingen beheren te gaan.
1. Klik op **[!UICONTROL Location]** > **[!UICONTROL Manage Points of Interest]**.

   ![Stap Resultaat](assets/poi.png)

1. Typ de informatie in elk van de volgende velden:

   * **[!UICONTROL Point Name]**

      Typ de **[!UICONTROL Point of Location]** naam.

      Dit kan de naam zijn van een stad, provincie of regio. U kunt ook een **[!UICONTROL Point of Location]** rond specifieke locaties, zoals sportstadions of bedrijven.

   * **[!UICONTROL Latitude ]**

      Typ de breedtegraad van de **[!UICONTROL Point of Location]**. U kunt deze informatie uit andere bronnen, met inbegrip van Internet vinden.

   * **[!UICONTROL Longitude]**

      Typ de lengtegraad van de **[!UICONTROL Point of Location]**. U kunt deze informatie uit andere bronnen, met inbegrip van Internet vinden.

   * **[!UICONTROL Radius (Meters)]**

      Typ de straal (in meters) rond de **[!UICONTROL Point of Location]** die u wilt opnemen. Als u bijvoorbeeld een POI maakt voor Denver, Colorado, kunt u een straal opgeven die groot genoeg is om de stad Denver en de omliggende gebieden op te nemen, maar Colorado Springs niet.

   * **[!UICONTROL Map Icon]**

      Selecteer een pictogram dat wordt weergegeven op het tabblad [Overzicht](/help/using/location/c-location-overview.md) en [Kaart](/help/using/location/c-map-points.md) rapporten.

1. Voeg zo nodig aanvullende POI&#39;s toe.

   We raden u aan niet meer dan 5.000 POI&#39;s toe te voegen. Als u meer dan 5000 toevoegt, kunt u de punten opslaan, maar ontvangt u een waarschuwingsbericht waarin u wordt gewaarschuwd dat volgens de aanbevolen procedures minder dan 5000 punten moeten zijn.

1. Klik op **[!UICONTROL Save]**.

Als u een of meer POI&#39;s wilt verwijderen, schakelt u de toepasselijke selectievakjes in en klikt u op **[!UICONTROL Remove Selected]**.

Klikken **[!UICONTROL Import]** of **[!UICONTROL Export]** om met de gegevens te werken door `.csv` in plaats van de Adobe Mobile-gebruikersinterface te gebruiken.
