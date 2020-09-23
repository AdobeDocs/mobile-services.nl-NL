---
description: Configureer ervaringsopties voor in-app berichten, zoals tekst (volledig scherm, waarschuwing of melding) en weergave-, tekst- en knopopties.
keywords: mobile
seo-description: Configureer ervaringsopties voor in-app berichten, zoals tekst (volledig scherm, waarschuwing of melding) en weergave-, tekst- en knopopties.
seo-title: Bericht over ervaring in de app
solution: Experience Cloud,Analytics
title: Bericht over ervaring in de app
topic: Metrics
uuid: 4c6d6756-47fb-4f1b-8338-0b0c9b0fceb0
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---


# Ervaring: bericht in de app {#experience-in-app-message}

Configureer ervaringsopties voor in-app berichten, zoals tekst (volledig scherm, waarschuwing of melding) en weergave-, tekst- en knopopties.

1. Klik in uw app op **[!UICONTROL Messaging]** > **[!UICONTROL Manage Messages]** > **[!UICONTROL Create Message]** > **[!UICONTROL Create In-App]**.
1. Typ op de pagina Experience een naam voor het bericht.
1. Vul de velden in de **[!UICONTROL Type]** sectie in:

   * **[!UICONTROL Type]**
Selecteer het berichttype voor uw in-app berichtcampagne:

      * **[!UICONTROL Full Screen]**
      * **[!UICONTROL Alert]**
      * **[!UICONTROL Local Notification]**
   * **[!UICONTROL Template]**

      Pas een antwoordberichtensjabloon voor thema&#39;s aan voor uw inhoud.

      >[!TIP]
      >
      >Deze optie wordt alleen weergegeven wanneer u het **[!UICONTROL Full Screen]** berichttype selecteert.

   * **[!UICONTROL Custom]**

      Laad uw aangepaste HTML-inhoud (alleen volledig scherm). U moet een doorklikkoppeling en een annuleringskoppeling opgeven.

      1. Klik op een HTML-bestand **[!UICONTROL Browse]** en download het of sleep een HTML-document naar het venster.
      1. Klik **[!UICONTROL Download Example]** om voorbeelden van aangepaste HTML-inhoud weer te geven.

      >[!TIP]
      >
      >Deze optie wordt alleen weergegeven wanneer u het berichttype **[!FVolledig scherm]** selecteert.



1. Vul de velden in de **[!UICONTROL Display]** sectie in:

   * **[!UICONTROL Theme]**

   Selecteer een thema voor uw bericht.

   * **[!UICONTROL Layout]**

      Selecteer de lay-out van de app op het apparatenscherm.

   * **[!UICONTROL Image URL]**

      De URL voor een afbeelding. Als u het rangschikken van kwesties wanneer het gebruiken van het volledig-schermmalplaatje hebt, zie *Mijn beeld niet precies in de ruimte past die door het malplaatje* in het overseinen [van het Oplossen van](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md)Problemen in-app past.

   * **[!UICONTROL Bundled Image]**

      Pad naar een afbeelding in de codebundel van de app. Deze optie wordt gebruikt als er geen afbeelding is. of de afbeelding niet beschikbaar is. Stel dat het apparaat niet beschikbaar is als het bijvoorbeeld offline is. Als u het rangschikken van kwesties wanneer het gebruiken van het volledig-schermmalplaatje hebt, zie *Mijn beeld niet precies in de ruimte past die door het malplaatje* in het overseinen [van het Oplossen van](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md)Problemen in-app past.


1. Vul de velden in de **[!UICONTROL Text]** sectie in:

   * **[!UICONTROL Header]**

      Typ de tekst voor de koptekst van het bericht.

   * **[!UICONTROL Content]**

      Typ de tekst voor de inhoud van het bericht.

1. Vul de velden in de **[!UICONTROL Buttons]** sectie in:

   * **[!UICONTROL Click-Through Button]**

      Label voor de **[!UICONTROL Click-Through]** knop. Tikken op deze knop telt als een geslaagde doorklikken. De gebruiker wordt opnieuw gericht aan de bestemming.

   * **[!UICONTROL Destination]**

      Selecteer een specifieke bestemming, zoals een web-, diepe of hybride koppeling, om gebruikers te verzenden wanneer zij op het bericht klikken. De omleidings-URL voor een geslaagde doorklik.

      Deze URL kan de volgende informatie bevatten:

      * `{userId}`, die wordt vervangen door de gebruikers-id of leeg is wanneer de gebruikers-id niet is ingesteld.
      * `{trackingId}`, die wordt vervangen door de steun (correleert met *s_vi* cookie).
      * `{messageId}`, die wordt vervangen door de unieke id voor het bericht in de app.
      * `{lifetimeValue}`, die door de levenwaarde of 0 wordt vervangen als geen levenwaarde bestaat.

      Hier volgt een voorbeeld van het bijhouden van de gebruikersnaam: `https://www.mysite.com?uid={userId}`.

      Als de doorklikkings-URL gebruikt `https://` of `https://`, opent URL in apparatenbrowser buiten app. Anders ondersteunt elk platform schema&#39;s waarmee u uw app kunt openen of ernaar kunt verwijzen als de app is ontwikkeld ter ondersteuning van het aangepaste schema.

      >[!TIP]
      >
      >Wanneer u de **[!UICONTROL Web Link]** of **[!UICONTROL Custom Link]** bestemmingstypes gebruikt, wordt het bestemmingstype niet gevolgd. Alleen **[!UICONTROL Deep Links]** worden bijgehouden. Zie [Doelen](/help/using/acquisition-main/c-create-destinations.md)voor meer informatie.


1. (Optioneel) Klik op de volgende pictogrammen om een voorvertoning van de lay-out van het bericht weer te geven:

   * **[!UICONTROL Summary]** Hiermee verbergt u het voorvertoningsvenster.

      Klik op ![Voorvertoning](assets/icon_preview.png) om het voorvertoningsvenster opnieuw weer te geven.

   * **[!UICONTROL Change the orientation]**

      Als u de richting van de voorvertoning wilt wijzigen van Staand in Liggend, klikt u op ![Richting](assets/icon_orientation.png). Voor stalen verandert de oriëntatie van een rond in een vierkant horlogevlak.

   * **[!UICONTROL Preview on a user's watch]**

      Als u een voorbeeld van uw bericht wilt bekijken zoals het wordt weergegeven in de gaten van de gebruiker, klikt u op het pictogram ![](assets/icon_watch.png)Controleren.

   * **[!UICONTROL Preview on a user's mobile phone]**

      Klik op het ![telefoonpictogram](assets/icon_phone.png)om een voorbeeld van uw bericht weer te geven zoals het op de mobiele telefoon van een gebruiker wordt weergegeven.

   * **[!UICONTROL Preview on a user's tablet]**

      Klik op ![tabletpictogram](assets/icon_tablet.png)om een voorvertoning van uw bericht weer te geven op het tablet van de gebruiker.

      Onder aan het voorvertoningsvenster kunt u een beschrijving weergeven van het publiek dat u in de vorige stap hebt geselecteerd. U kunt ook een beschrijving bekijken van het publiek dat u in de vorige stap onder aan het voorvertoningsvenster hebt geselecteerd.

1. Configureer de [planningsopties](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md).
