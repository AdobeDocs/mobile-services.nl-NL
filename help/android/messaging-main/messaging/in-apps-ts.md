---
description: Deze informatie helpt u in-app overseinen problemen op te lossen.
keywords: mobiel
solution: Experience Cloud Services,Analytics
title: In-app-berichten oplossen
topic-fix: Metrics
uuid: 39c3a21d-92c2-4004-b00f-99b6f91d3696
exl-id: 6c7d97ed-3b0a-48ff-b761-1485aea5e96d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# In-app-berichten oplossen{#troubleshooting-in-app-messaging}

Deze informatie helpt u in-app overseinen problemen op te lossen.

Controleer de volgende items als u alle vereisten voor In-App-berichten hebt voltooid, maar de berichten niet worden weergegeven:

## Zet u de nieuwe configuratie en de nieuwe SDK in de app?

Zorg ervoor dat u een [In-app berichten](/help/android/messaging-main/messaging/messaging.md) in uw configuratie (gedownload JSON- dossier) of hebben een ver eindpunt van Berichten, zodat het van dynamisch markeringsbeheer kan worden teruggewonnen.

## Mijn volledige-schermbericht in Android wordt niet weergegeven. Ik gebruik correcte SDK, configuratie, en mijn trekkers worden ontmoet.

Hebt u het manifestbestand bijgewerkt om de volledige schermactiviteit te definiëren?

## Mijn lokale meldingsbericht in Android werkt niet.

Zorg ervoor dat de lokale ontvanger van de berichtuitzending in uw manifest wordt verklaard. Zie stap 2 voor meer informatie *In-app-berichten inschakelen* in [In-app berichten](/help/android/messaging-main/messaging/messaging.md).

## Is het bericht live?

Als u wilt controleren of uw bericht live is, gaat u op de pagina Bericht in de app beheren op de knop **[!UICONTROL Status]** kolom, controleer de lijst van berichten.

## Kijk naar *eenmaal tonen*, *altijd tonen*, *offline tonen*  instellingen op het tabblad Publiek.

Controleer of deze instellingen op de gewenste manier zijn ingesteld. Op de **[!UICONTROL Audience]** tabblad, bekijk uw **[!UICONTROL Trigger]** opties, waarmee u kunt opgeven hoe vaak het bericht wordt weergegeven.

## Als u een startgebeurtenis als trigger gebruikt...

Hiermee wordt alleen een nieuwe sessie gestart. Voor meer informatie over wanneer een zitting begint, zie `lifecycleTimeout` rij in [JSON Config](/help/android/configuration/json-config/json-config.md).

## Ik heb mijn bericht op afstand bijgewerkt, maar mijn app toont nog steeds het oude bericht.

De volgende informatie onthouden:

* Het dynamische markeringsbeheer kan een paar notulen nemen om zijn eindpunt met uw nieuwe definitie bij te werken. Wacht even en probeer het opnieuw.
* De config zal slechts op een nieuwe lancering bijwerken. Als de app opnieuw is gestart tijdens de sessietime-out van de levenscyclus, is de nieuwe configuratie mogelijk niet gedownload.

Zie voor meer informatie [Levenscycluscijfers](/help/android/metrics.md).

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
   Als u problemen hebt met de sjabloon Volledig scherm, kunt u de sjabloon Aangepast HTML downloaden en gebruiken. Deze sjabloon biedt meer flexibiliteit voor afbeeldingen en biedt volledige controle over de sjabloon.
