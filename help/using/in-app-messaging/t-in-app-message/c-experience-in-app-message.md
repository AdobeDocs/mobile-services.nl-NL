---
description: Configureer ervaringsopties voor in-app berichten, zoals tekst (volledig scherm, waarschuwing of melding) en weergave-, tekst- en knopopties.
keywords: mobiel
seo-description: Configureer ervaringsopties voor in-app berichten, zoals tekst (volledig scherm, waarschuwing of melding) en weergave-, tekst- en knopopties.
seo-title: Bericht over ervaring in de app
solution: Experience Cloud,Analytics
title: Bericht over ervaring in de app
topic-fix: Metrics
uuid: 4c6d6756-47fb-4f1b-8338-0b0c9b0fceb0
exl-id: eeb1527d-c546-4951-9947-db810fdb8eee
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# Ervaring: in-app-bericht {#experience-in-app-message}

Configureer ervaringsopties voor in-app berichten, zoals tekst (volledig scherm, waarschuwing of melding) en weergave-, tekst- en knopopties.

1. Klik in uw app op **[!UICONTROL Messaging]** > **[!UICONTROL Manage Messages]** > **[!UICONTROL Create Message]** > **[!UICONTROL Create In-App]**.
1. Typ op de pagina Experience een naam voor het bericht.
1. Vul de velden in de sectie **[!UICONTROL Type]** in:

   * **[!UICONTROL Type]**
Selecteer het berichttype voor uw in-app berichtcampagne:

      * **[!UICONTROL Full Screen]**
      * **[!UICONTROL Alert]**
      * **[!UICONTROL Local Notification]**
   * **[!UICONTROL Template]**

      Pas een antwoordberichtensjabloon voor thema&#39;s aan voor uw inhoud.

      >[!TIP]
      >
      >Deze optie wordt alleen weergegeven wanneer u het berichttype **[!UICONTROL Full Screen]** selecteert.

   * **[!UICONTROL Custom]**

      Laad uw aangepaste HTML-inhoud (alleen volledig scherm). U moet een doorklikkoppeling en een annuleringskoppeling opgeven.

      1. Klik op **[!UICONTROL Browse]** en download een HTML-bestand of sleep een HTML-document naar het venster.
      1. Klik **[!UICONTROL Download Example]** om voorbeeld van aangepaste HTML-inhoud weer te geven.

      >[!TIP]
      >
      >Deze optie wordt alleen weergegeven wanneer u het berichttype **[!FVolledig scherm]** selecteert.



1. Vul de velden in de sectie **[!UICONTROL Display]** in:

   * **[!UICONTROL Theme]**

   Selecteer een thema voor uw bericht.

   * **[!UICONTROL Layout]**

      Selecteer de lay-out van de app op het apparatenscherm.

   * **[!UICONTROL Image URL]**

      De URL voor een afbeelding. Zie *Mijn afbeelding past niet exact in de ruimte die wordt geboden door de sjabloon* in [Problemen met het in-app-messaging oplossen](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md) als er zich bij het gebruik van de sjabloon voor een groter formaat problemen voordoen.

   * **[!UICONTROL Bundled Image]**

      Pad naar een afbeelding in de codebundel van de app. Deze optie wordt gebruikt als er geen afbeelding is. of de afbeelding niet beschikbaar is. Stel dat het apparaat niet beschikbaar is als het bijvoorbeeld offline is. Zie *Mijn afbeelding past niet exact in de ruimte die wordt geboden door de sjabloon* in [Problemen met het in-app-messaging oplossen](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md) als er zich bij het gebruik van de sjabloon voor een groter formaat problemen voordoen.


1. Vul de velden in de sectie **[!UICONTROL Text]** in:

   * **[!UICONTROL Header]**

      Typ de tekst voor de koptekst van het bericht.

   * **[!UICONTROL Content]**

      Typ de tekst voor de inhoud van het bericht.

1. Vul de velden in de sectie **[!UICONTROL Buttons]** in:

   * **[!UICONTROL Click-Through Button]**

      Label voor de knop **[!UICONTROL Click-Through]**. Tikken op deze knop telt als een geslaagde doorklikken. De gebruiker wordt opnieuw gericht aan de bestemming.

   * **[!UICONTROL Destination]**

      Selecteer een specifieke bestemming, zoals een web-, diepe of hybride koppeling, om gebruikers te verzenden wanneer zij op het bericht klikken. De omleidings-URL voor een geslaagde doorklik.

      Deze URL kan de volgende informatie bevatten:

      * `{userId}`, die wordt vervangen door de gebruikers-id of leeg is wanneer de gebruikers-id niet is ingesteld.
      * `{trackingId}`, die wordt vervangen door de steun (correleert met  *s_* vicookie).
      * `{messageId}`, die wordt vervangen door de unieke id voor het bericht in de app.
      * `{lifetimeValue}`, die door de levenwaarde of 0 wordt vervangen als geen levenwaarde bestaat.

      Hier volgt een voorbeeld van het bijhouden van de gebruikersnaam: `https://www.mysite.com?uid={userId}`.

      Als de doorklikkings-URL `https://` of `https://` gebruikt, opent URL in apparatenbrowser buiten app. Anders ondersteunt elk platform schema&#39;s waarmee u uw app kunt openen of ernaar kunt verwijzen als de app is ontwikkeld ter ondersteuning van het aangepaste schema.

      >[!TIP]
      >
      >Wanneer u **[!UICONTROL Web Link]** of **[!UICONTROL Custom Link]** bestemmingstypes gebruikt, wordt het bestemmingstype niet gevolgd. Alleen **[!UICONTROL Deep Links]** worden bijgehouden. Zie [Doelen](/help/using/acquisition-main/c-create-destinations.md) voor meer informatie.


1. (Optioneel) Klik op de volgende pictogrammen om een voorvertoning van de lay-out van het bericht weer te geven:

   * **[!UICONTROL Summary]** Hiermee verbergt u het voorvertoningsvenster.

      Klik ![voorproef](assets/icon_preview.png) om de voorproefruit opnieuw te tonen.

   * **[!UICONTROL Change the orientation]**

      Als u de richting van de voorvertoning wilt wijzigen van Staand in Liggend, klikt u op ![orientation](assets/icon_orientation.png). Voor stalen verandert de oriëntatie van een rond in een vierkant horlogevlak.

   * **[!UICONTROL Preview on a user's watch]**

      Klik op ![watch icon](assets/icon_watch.png) om een voorvertoning van uw bericht weer te geven zoals het wordt weergegeven in de gaten van de gebruiker.

   * **[!UICONTROL Preview on a user's mobile phone]**

      Klik ![telefoonpictogram](assets/icon_phone.png) om een voorvertoning van uw bericht weer te geven zoals het op de mobiele telefoon van een gebruiker wordt weergegeven.

   * **[!UICONTROL Preview on a user's tablet]**

      Klik op ![tabletpictogram](assets/icon_tablet.png) om een voorvertoning van uw bericht weer te geven op het tablet van de gebruiker.

      Onder aan het voorvertoningsvenster kunt u een beschrijving weergeven van het publiek dat u in de vorige stap hebt geselecteerd. U kunt ook een beschrijving bekijken van het publiek dat u in de vorige stap onder aan het voorvertoningsvenster hebt geselecteerd.

1. Configureer [Planningsopties](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md).
