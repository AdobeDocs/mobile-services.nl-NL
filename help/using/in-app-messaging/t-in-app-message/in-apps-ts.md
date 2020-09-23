---
description: Deze informatie kan u helpen uw in-app overseinenkwesties oplossen.
keywords: mobile
seo-description: Deze informatie kan u helpen uw in-app overseinenkwesties oplossen.
seo-title: Problemen met In-app-berichten oplossen
solution: Experience Cloud,Analytics
title: Problemen met In-app-berichten oplossen
topic: Metrics
uuid: 8813e8d8-bb1e-46ad-83cd-98ae68f73ce6
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---


# Problemen met in-app messaging oplossen{#troubleshooting-in-app-messaging}

Deze informatie kan u helpen uw in-app overseinenkwesties oplossen.

Als u alle vereisten voor Overseinen in-App voltooide, maar de berichten verschijnen niet, verifieer de volgende punten:

## Zet u de nieuwe configuratie en de nieuwe SDK in de app?

* Controleer of de SDK versie 4.2 of hoger is en correct is geconfigureerd.

* Zorg ervoor dat u een sectie van het [Overseinen](/help/using/in-app-messaging/in-app-messaging.md) in uw configuratie (het gedownloade JSON- dossier) hebt of een ver eindpunt van Berichten hebt, zodat het van dynamisch markeringsbeheer kan worden teruggewonnen.

## Mijn volledige-schermbericht in Android wordt niet weergegeven. Ik gebruik correcte SDK, configuratie, en mijn trekkers worden ontmoet.

Hebt u het manifestbestand bijgewerkt om de volledige schermactiviteit te definiëren?

## Mijn lokale meldingsbericht in Android werkt niet.

Verifieer dat de lokale ontvanger van de berichtuitzending in uw manifest wordt verklaard. Zie stap 1 in [In-app messaging](/help/android/messaging-main/messaging/messaging.md)voor meer informatie.

## Is het bericht live?

Controleer de lijstmening in de **[!UICONTROL Status]** kolom op de Manage In-App pagina van het Bericht en verifieer of het bericht live is.

## Kijk eens *tonen eens*, *tonen altijd*, *tonen off-line* montages op de pagina van het Publiek.

Controleer of deze instellingen correct zijn. Controleer op de pagina Publiek de opties op het **[!UICONTROL Trigger]** tabblad, waar u kunt opgeven hoe vaak het bericht wordt weergegeven.

## Bij gebruik van de gebeurtenis launch als trigger...

Hiermee wordt alleen een nieuwe sessie gestart. Voor informatie over wanneer een zitting begint, zie `lifecycleTimeout` in het [JSON config](/help/ios/configuration/json-config/json-config.md) dossier ADBMobile.

## Ik heb mijn bericht op afstand bijgewerkt, maar mijn app geeft nog steeds het oude bericht weer.

Voer een van de volgende taken uit:

* Dynamisch tagbeheer kan enkele minuten duren om het eindpunt van het beheer bij te werken met uw nieuwe definitie.

   Geef het wat tijd en probeer het opnieuw.

* De config zal slechts op een nieuwe lancering bijwerken.

   Als de app opnieuw is gestart in de sessietime-out van de levenscyclus, is de nieuwe configuratie mogelijk niet gedownload.

## Mijn afbeelding past niet precies in de ruimte die de sjabloon biedt.

De sjabloon Berichten in de app op volledig scherm ondersteunt het weergeven van een afbeelding van een externe server (afbeeldings-URL) of van de app-bundel (Gebundelde afbeelding). De afbeelding moet een standaardafbeeldingsindeling hebben, bijvoorbeeld JPG, GIF of PNG.

Vanwege apparaatschermen met veel verschillende afmetingen past de afbeelding waarschijnlijk niet precies in de ruimte die de sjabloon biedt. De sjabloon is altijd gericht op het weergeven van het midden van de afbeelding en het uitsnijden (staand) of vervagen (liggend) van de zijden als de afbeelding niet past.

Hier volgen de exacte plaatsings- en grootteregels voor elke richting:

* **Staand**, waarbij de afbeelding wordt geschaald naar een hoogte van 195 px voor telefoons, 529 px voor tablets, gecentreerd als de afbeeldingsbreedte kleiner is dan de apparaatbreedte, en bijgesneden als de afbeeldingsbreedte groter is dan de apparaatbreedte.

* **Liggend**, waarbij de afbeelding wordt geschaald naar 100% van de hoogte van het apparaat, is de breedte 75% van het apparaat en met een uitfade aan de rechterkant.

   Als u problemen hebt met de sjabloon Volledig scherm, kunt u de aangepaste HTML-sjabloon downloaden en gebruiken. De sjabloon Aangepaste HTML biedt meer flexibiliteit voor afbeeldingen en biedt volledige controle over de sjabloon.

## Mijn berichten weerspiegelen geen veranderingen/updates die ik in UI heb gemaakt.

De SDK haalt nieuwe/bijgewerkte berichten op op het moment dat de levenscyclus wordt gestart. Dit is alleen het geval als de toepassing wordt gesloten/achtergrond voor een langere periode dan de time-outwaarde van de levenscyclus en vervolgens opnieuw wordt geopend.

Voer de volgende stappen uit:

1. Koop de URL van uw berichten in uw configuratiebestand om te controleren of het externe bericht is bijgewerkt (bijvoorbeeld `curl "https://assets.adobedtm.com/b213090c5204bf94318f4ef0539a38b487d10368/scripts/satellite-542c62859662383b1a0008f4.json"`)
1. Sluit de toepassing.
1. Wacht op een tijdspanne die langer is dan `lifecycleTimeout` in het config- dossier.
1. Open de app, navigeer naar de locatie waar het bericht moet worden weergegeven en controleer of deze is bijgewerkt.