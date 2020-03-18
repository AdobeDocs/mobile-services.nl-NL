---
description: U kunt interessante punten maken en beheren, waarmee u geografische locaties kunt definiëren die u kunt gebruiken voor correlatiedoeleinden, u kunt richten op berichten in de app, enzovoort. Wanneer een treffer wordt verzonden in een belangenpunt, wordt het aandachtspunt verbonden aan de treffer.
keywords: mobile
seo-description: U kunt interessante punten maken en beheren, waarmee u geografische locaties kunt definiëren die u kunt gebruiken voor correlatiedoeleinden, u kunt richten op berichten in de app, enzovoort. Wanneer een treffer wordt verzonden in een belangenpunt, wordt het aandachtspunt verbonden aan de treffer.
seo-title: Belangenpunten beheren
solution: Marketing Cloud,Analytics
title: Belangenpunten beheren
topic: Metrics
uuid: 7b362534-54fb-43a3-b6b2-dfc8f45ff7c6
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Belangenpunten beheren {#manage-points-of-interest}

U kunt POI&#39;s maken en beheren, waarmee u geografische locaties kunt definiëren die u kunt gebruiken voor correlatiedoeleinden, als doel kunt instellen voor berichten in de app, enzovoort. Wanneer een hit wordt verzonden in een POI, wordt de POI aan de hit gekoppeld.

Controleer voordat u Locatie kunt gebruiken de volgende vereisten:

* U moet beschikken over Analytics: Mobile Apps of Analytics Premium.
* U moet inschakelen **[!UICONTROL Location Reports]** voor de app.
* Als u een versie van de iOS SDK of de Android SDK ouder dan versie 4.2 gebruikt, moet u na het toevoegen van een nieuw configuratiebestand een nieuw configuratiebestand downloaden en dit aan de ontwikkelaars van de app overhandigen. **[!UICONTROL Points of Interest]**

   Als u de iOS SDK of Android SDK versie 4.2 of hoger gebruikt, hoeft u geen app-update naar de winkel te verzenden om uw **[!UICONTROL Points of Interest]** versie bij te werken. Wanneer u op de pagina Punten van interesse beheren klikt, worden de wijzigingen in de **[!UICONTROL Save]****[!UICONTROL Points of Interest]** lijst opgenomen en wordt het configuratiebestand voor de live app bijgewerkt. Wanneer u de lijst met punten in uw app opslaat op de gebruikersapparaten, werkt u deze ook bij zolang de app de bijgewerkte SDK en de configuratie met een externe POI-URL gebruikt.

Als een treffer op het apparaat van de gebruiker aan een **[!UICONTROL Points of Interest]** geluid wordt toegewezen, moet de locatie voor de toepassing zijn ingeschakeld.

Voer de volgende taken uit om Locatie te gebruiken:

1. Klik op de naam van de toepassing om naar de pagina Toepassingsinstellingen beheren te gaan.
1. Klik op **[!UICONTROL Location]** > **[!UICONTROL Manage Points of Interest]**.

   ![Stap resultaat](assets/poi.png)

1. Typ de informatie in elk van de volgende velden:

   * **[!UICONTROL Point Name]**

      Typ de **[!UICONTROL Point of Location]** naam.

      Dit kan de naam zijn van een stad, provincie of regio. U kunt ook een **[!UICONTROL Point of Location]** site maken rond specifieke locaties, zoals stadions of bedrijven.

   * **[!UICONTROL Latitude ]**

      Typ de breedtegraad van de **[!UICONTROL Point of Location]** afbeelding. U kunt deze informatie uit andere bronnen, met inbegrip van Internet vinden.

   * **[!UICONTROL Longitude]**

      Typ de lengtegraad van de **[!UICONTROL Point of Location]** afbeelding. U kunt deze informatie uit andere bronnen, met inbegrip van Internet vinden.

   * **[!UICONTROL Radius (Meters)]**

      Typ de straal (in meters) rondom de straal **[!UICONTROL Point of Location]** die u wilt opnemen. Als u bijvoorbeeld een POI maakt voor Denver, Colorado, kunt u een straal opgeven die groot genoeg is om de stad Denver en de omliggende gebieden op te nemen, maar Colorado Springs niet.

   * **[!UICONTROL Map Icon]**

      Selecteer een pictogram dat op het [Overzicht](/help/using/location/c-location-overview.md) en de rapporten van de [Kaart](/help/using/location/c-map-points.md) zal tonen.

1. Voeg zo nodig aanvullende POI&#39;s toe.

   We raden u aan niet meer dan 5000 POI&#39;s toe te voegen. Als u meer dan 5000 toevoegt, kunt u de punten opslaan, maar ontvangt u een waarschuwingsbericht waarin u wordt gewaarschuwd dat volgens de aanbevolen procedures minder dan 5000 punten moeten zijn.

1. Klik op **[!UICONTROL Save]**.

Als u een of meer POI&#39;s wilt verwijderen, schakelt u de desbetreffende selectievakjes in en klikt u **[!UICONTROL Remove Selected]** op OK.

Klik **[!UICONTROL Import]** of **[!UICONTROL Export]** om met de gegevens te werken door een `.csv` bestand te gebruiken in plaats van de Adobe Mobile-gebruikersinterface.
