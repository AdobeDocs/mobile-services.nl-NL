---
description: Deze informatie helpt u in-app overseinen problemen op te lossen.
keywords: mobiel
seo-description: Deze informatie helpt u in-app overseinen problemen op te lossen.
seo-title: In-app-berichten oplossen
solution: Experience Cloud,Analytics
title: In-app-berichten oplossen
topic-fix: Metrics
uuid: 39c3a21d-92c2-4004-b00f-99b6f91d3696
exl-id: 6c7d97ed-3b0a-48ff-b761-1485aea5e96d
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Problemen met in-app messaging oplossen{#troubleshooting-in-app-messaging}

Deze informatie helpt u in-app overseinen problemen op te lossen.

Controleer de volgende items als u alle vereisten voor In-App-berichten hebt voltooid, maar de berichten niet worden weergegeven:

## Zet u de nieuwe configuratie en de nieuwe SDK in de app?

Zorg ervoor dat u een [In-App Overseinen](/help/android/messaging-main/messaging/messaging.md) sectie in uw configuratie (gedownload JSON dossier) hebt of een verre eindpunt van Berichten hebt, zodat het van dynamisch markeringsbeheer kan worden teruggewonnen.

## Mijn volledige-schermbericht in Android wordt niet weergegeven. Ik gebruik correcte SDK, configuratie, en mijn trekkers worden ontmoet.

Hebt u het manifestbestand bijgewerkt om de volledige schermactiviteit te definiëren?

## Mijn lokale meldingsbericht in Android werkt niet.

Zorg ervoor dat de lokale ontvanger van de berichtuitzending in uw manifest wordt verklaard. Voor meer informatie, zie stap 2 in *In-App Overseinen toelaten* in [In-App Overseinen](/help/android/messaging-main/messaging/messaging.md).

## Is het bericht live?

Om te verifiëren of uw bericht live is, controleert u op de pagina Bericht in de app beheren in de kolom **[!UICONTROL Status]** de lijst met berichten.

## Bekijk *show eens*, *show altijd*, *show off-line* montages op het lusje van de Publiek.

Controleer of deze instellingen op de gewenste manier zijn ingesteld. Controleer op het tabblad **[!UICONTROL Audience]** de opties **[!UICONTROL Trigger]**, waarmee u kunt opgeven hoe vaak het bericht wordt weergegeven.

## Als u een startgebeurtenis als trigger gebruikt...

Hiermee wordt alleen een nieuwe sessie gestart. Voor meer informatie over wanneer een zitting begint, zie `lifecycleTimeout` rij in [JSON Config](/help/android/configuration/json-config/json-config.md).

## Ik heb mijn bericht op afstand bijgewerkt, maar mijn app toont nog steeds het oude bericht.

De volgende informatie onthouden:

* Het dynamische markeringsbeheer kan een paar notulen nemen om zijn eindpunt met uw nieuwe definitie bij te werken. Wacht even en probeer het opnieuw.
* De config zal slechts op een nieuwe lancering bijwerken. Als de app opnieuw is gestart tijdens de sessietime-out van de levenscyclus, is de nieuwe configuratie mogelijk niet gedownload.

Zie [Levenscyclusmetriek](/help/android/metrics.md) voor meer informatie.

## Mijn afbeelding past niet precies in de ruimte die de sjabloon biedt.

De sjabloon Berichten in de app op volledig scherm ondersteunt het weergeven van een afbeelding van een externe server (afbeeldings-URL) of van de app-bundel (gebundelde afbeelding). De afbeelding moet een standaardafbeeldingsindeling hebben, zoals JPG, GIF of PNG. Aangezien apparaatschermen vele verschillende afmetingen hebben, past de afbeelding hoogstwaarschijnlijk niet precies in de ruimte die de sjabloon biedt. De sjabloon is gericht op het weergeven van het midden van de afbeelding en, als de afbeelding niet past, op het uitsnijden (staand) of vervagen (liggend) van de zijden.

Hier volgen de exacte plaatsings- en grootteregels voor elke richting:

* **Staand**
   * Een hoogte van 195px voor telefoons.
   * Een hoogte van 529 px voor tabletten.
   * Gecentreerd als de afbeeldingsbreedte kleiner is dan de apparaatbreedte.
   * Uitgesneden als de afbeeldingsbreedte groter is dan de apparaatbreedte.

* **Liggend**
   * De afbeelding wordt geschaald naar 100% van de hoogte van het apparaat.
   * De breedte is 75% van het apparaat, met een uitfade aan het recht.
   Als u problemen hebt met de sjabloon Volledig scherm, kunt u de aangepaste HTML-sjabloon downloaden en gebruiken. Deze sjabloon biedt meer flexibiliteit voor afbeeldingen en biedt volledige controle over de sjabloon.
