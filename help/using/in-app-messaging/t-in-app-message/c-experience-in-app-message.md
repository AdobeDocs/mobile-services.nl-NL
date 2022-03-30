---
description: Configureer ervaringsopties voor in-app berichten, zoals tekst (volledig scherm, waarschuwing of melding) en weergave-, tekst- en knopopties.
keywords: mobiel
solution: Experience Cloud Services,Analytics
title: Bericht over ervaring in de app
topic-fix: Metrics
uuid: 4c6d6756-47fb-4f1b-8338-0b0c9b0fceb0
exl-id: eeb1527d-c546-4951-9947-db810fdb8eee
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---

# Ervaring: bericht in de app {#experience-in-app-message}

Configureer ervaringsopties voor in-app berichten, zoals tekst (volledig scherm, waarschuwing of melding) en weergave-, tekst- en knopopties.

1. Klik in uw app op **[!UICONTROL Messaging]** > **[!UICONTROL Manage Messages]** > **[!UICONTROL Create Message]** > **[!UICONTROL Create In-App]**.
1. Typ op de pagina Experience een naam voor het bericht.
1. Vul de velden in het dialoogvenster **[!UICONTROL Type]** sectie:

   * **[!UICONTROL Type]**
Selecteer het berichttype voor uw in-app berichtcampagne:

      * **[!UICONTROL Full Screen]**
      * **[!UICONTROL Alert]**
      * **[!UICONTROL Local Notification]**
   * **[!UICONTROL Template]**

      Pas een antwoordberichtensjabloon voor thema&#39;s aan voor uw inhoud.

      >[!TIP]
      >
      >Deze optie wordt alleen weergegeven wanneer u **[!UICONTROL Full Screen]** berichttype.

   * **[!UICONTROL Custom]**

      Laad uw aangepaste HTML-inhoud (alleen volledig scherm). U moet een doorklikkoppeling en een annuleringskoppeling opgeven.

      1. Klikken **[!UICONTROL Browse]** en download een HTML-bestand of sleep een HTML-document naar het venster.
      1. Klikken **[!UICONTROL Download Example]** als u aangepaste HTML-inhoud wilt weergeven.

      >[!TIP]
      >
      >Deze optie wordt alleen weergegeven wanneer u **[!FVolledig scherm]** berichttype.



1. Vul de velden in het dialoogvenster **[!UICONTROL Display]** sectie:

   * **[!UICONTROL Theme]**

   Selecteer een thema voor uw bericht.

   * **[!UICONTROL Layout]**

      Selecteer de lay-out van de app op het apparatenscherm.

   * **[!UICONTROL Image URL]**

      De URL voor een afbeelding. Als u formaatproblemen hebt bij het gebruik van de sjabloon Volledig scherm, raadpleegt u *Mijn afbeelding past niet precies in de ruimte die wordt geboden door de sjabloon* in [Problemen met in-app messaging oplossen](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).

   * **[!UICONTROL Bundled Image]**

      Pad naar een afbeelding in de codebundel van de app. Deze optie wordt gebruikt als er geen afbeelding is. of de afbeelding niet beschikbaar is. Stel dat het apparaat niet beschikbaar is als het bijvoorbeeld offline is. Als u formaatproblemen hebt bij het gebruik van de sjabloon Volledig scherm, raadpleegt u *Mijn afbeelding past niet precies in de ruimte die wordt geboden door de sjabloon* in [Problemen met in-app messaging oplossen](/help/using/in-app-messaging/t-in-app-message/in-apps-ts.md).


1. Vul de velden in het dialoogvenster **[!UICONTROL Text]** sectie:

   * **[!UICONTROL Header]**

      Typ de tekst voor de koptekst van het bericht.

   * **[!UICONTROL Content]**

      Typ de tekst voor de inhoud van het bericht.

1. Vul de velden in het dialoogvenster **[!UICONTROL Buttons]** sectie:

   * **[!UICONTROL Click-Through Button]**

      Label voor de **[!UICONTROL Click-Through]** knop. Tikken op deze knop telt als een geslaagde doorklikken. De gebruiker wordt opnieuw gericht aan de bestemming.

   * **[!UICONTROL Destination]**

      Selecteer een specifieke bestemming, zoals een web-, diepe of hybride koppeling, om gebruikers te verzenden wanneer zij op het bericht klikken. De omleidings-URL voor een geslaagde doorklik.

      Deze URL kan de volgende informatie bevatten:

      * `{userId}`, die wordt vervangen door de gebruikers-id of leeg is wanneer de gebruikers-id niet is ingesteld.
      * `{trackingId}`, die door de steun wordt vervangen (correleert met *s_vi* cookie).
      * `{messageId}`, die wordt vervangen door de unieke id voor het bericht in de app.
      * `{lifetimeValue}`, die door de levenwaarde of 0 wordt vervangen als geen levenwaarde bestaat.

      Hier volgt een voorbeeld van het bijhouden van de gebruikersnaam: `https://www.mysite.com?uid={userId}`.

      Als de doorklikkings-URL wordt gebruikt `https://` of `https://`, wordt de URL geopend in de apparaatbrowser buiten de app. Anders ondersteunt elk platform schema&#39;s waarmee u uw app kunt openen of ernaar kunt verwijzen als de app is ontwikkeld ter ondersteuning van het aangepaste schema.

      >[!TIP]
      >
      >Wanneer u de **[!UICONTROL Web Link]** of **[!UICONTROL Custom Link]** doeltypen, wordt het doeltype niet bijgehouden. Alleen **[!UICONTROL Deep Links]** worden bijgehouden. Zie voor meer informatie [Doelen](/help/using/acquisition-main/c-create-destinations.md).


1. (Optioneel) Klik op de volgende pictogrammen om een voorvertoning van de lay-out van het bericht weer te geven:

   * **[!UICONTROL Summary]** Hiermee verbergt u het voorvertoningsvenster.

      Klikken ![voorvertoning](assets/icon_preview.png) om het voorvertoningsvenster opnieuw weer te geven.

   * **[!UICONTROL Change the orientation]**

      Als u de richting van de voorvertoning wilt wijzigen van Staand in Liggend, klikt u op ![oriëntatie](assets/icon_orientation.png). Voor stalen verandert de oriëntatie van een rond in een vierkant horlogevlak.

   * **[!UICONTROL Preview on a user's watch]**

      Klik op ![horlogepictogram](assets/icon_watch.png).

   * **[!UICONTROL Preview on a user's mobile phone]**

      Klik op ![telefoonpictogram](assets/icon_phone.png).

   * **[!UICONTROL Preview on a user's tablet]**

      Als u een voorvertoning van uw bericht wilt weergeven op de tablet van de gebruiker, klikt u op ![tabletpictogram](assets/icon_tablet.png).

      Onder aan het voorvertoningsvenster kunt u een beschrijving weergeven van het publiek dat u in de vorige stap hebt geselecteerd. U kunt ook een beschrijving bekijken van het publiek dat u in de vorige stap onder aan het voorvertoningsvenster hebt geselecteerd.

1. Configureren [Planningsopties](/help/using/in-app-messaging/t-in-app-message/c-schedule-in-app-message.md).
