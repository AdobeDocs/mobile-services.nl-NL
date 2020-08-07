---
description: Deze informatie helpt u in-app overseinen problemen op te lossen.
keywords: mobile
seo-description: Deze informatie helpt u in-app overseinen problemen op te lossen.
seo-title: Problemen met In-app-berichten oplossen
solution: Marketing Cloud,Analytics
title: Problemen met In-app-berichten oplossen
topic: Metrics
uuid: 58533aa3-2eb2-4597-8525-77e4e5975e56
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 0%

---


# Problemen met in-app messaging oplossen{#troubleshooting-in-app-messaging}

Deze informatie helpt u in-app overseinen problemen op te lossen.

Als u alle vereisten voor Berichten in de app voltooide, maar de berichten tonen niet, controleer de volgende punten:

## Zet u de nieuwe configuratie en de nieuwe SDK in de app?

Controleer of de SDK versie 4.2 of hoger is en correct is geconfigureerd. Zorg ervoor dat u een `Messages` sectie in uw configuratie (gedownload JSON dossier) hebt, of een ver eindpunt van Berichten hebt, zodat het van dynamisch markeringsbeheer kan worden teruggewonnen.

## Mijn volledige-schermbericht in Android wordt niet weergegeven. Ik gebruik correcte SDK, configuratie, en mijn trekkers worden ontmoet.

Hebt u het manifestbestand bijgewerkt om de volledige schermactiviteit te definiëren?

## Mijn lokale meldingsbericht in Android werkt niet.

Zorg ervoor dat de lokale ontvanger van de berichtuitzending in uw manifest wordt verklaard. Zie stap 2 in [In-app berichten](/help/android/messaging-main/messaging/messaging.md)inschakelen voor meer informatie.

## Is het bericht live?

Schakel de lijstweergave op de pagina Bericht in de app beheren in de kolom Status in en controleer of deze live is.

## Kijk eens *tonen eens*, *tonen altijd*, *tonen off-line* montages op het lusje van het Publiek.

Controleer of deze instellingen op de gewenste manier zijn ingesteld. Controleer op het **[!UICONTROL Audience]** tabblad de **[!UICONTROL Trigger]** opties waarmee u kunt opgeven hoe vaak het bericht wordt weergegeven.

## Bij gebruik van de gebeurtenis launch als trigger...

Hiermee wordt alleen een nieuwe sessie gestart. Zie de `lifecycleTimeout` rij in het bestand JSON Config voor meer informatie over het begin van een sessie. Zie [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md)voor meer informatie.

## Ik heb mijn bericht op afstand bijgewerkt, maar mijn app geeft nog steeds het oude bericht weer.

Voer een van de volgende taken uit:

* Het dynamische markeringsbeheer kan een paar notulen nemen om zijn eindpunt met uw nieuwe definitie bij te werken.

   Wacht even en probeer het opnieuw.

* De config zal slechts op een nieuwe lancering bijwerken.
Als de app opnieuw is gestart tijdens de sessietime-out van de levenscyclus, is de nieuwe configuratie mogelijk niet gedownload.

   Zie [Levenscyclusstatistieken](/help/ios/metrics.md)voor meer informatie.

## Mijn afbeelding past niet precies in de ruimte die de sjabloon biedt.

De sjabloon Berichten in de app op volledig scherm ondersteunt het weergeven van een afbeelding van een externe server (afbeeldings-URL) of van de app-bundel (gebundelde afbeelding). De afbeelding moet een standaardafbeeldingsindeling hebben, zoals JPG, GIF of PNG.

Aangezien apparaatschermen vele verschillende afmetingen hebben, past de afbeelding hoogstwaarschijnlijk niet precies in de ruimte die de sjabloon biedt. De sjabloon is gericht op het weergeven van het middelpunt van de afbeelding en op het uitsnijden (staand) of vervagen (liggend) van de zijden als de afbeelding niet past.

Hier volgen de exacte plaatsings- en grootteregels voor elke richting:

* **Staand**:
   * Een hoogte van 195px voor telefoons
   * Een hoogte van 529 px voor tabletten
   * Gecentreerd als de afbeeldingsbreedte kleiner is dan de apparaatbreedte.
   * Uitgesneden als de afbeeldingsbreedte groter is dan de apparaatbreedte.

* **Liggend**:
   * De afbeelding wordt geschaald naar 100% van de hoogte van het apparaat.
   * De breedte is 75% van het apparaat, met een uitfade aan het recht.

Als u problemen hebt met de sjabloon Volledig scherm, kunt u de aangepaste HTML-sjabloon downloaden en gebruiken. Deze sjabloon biedt meer flexibiliteit voor afbeeldingen en biedt volledige controle over de sjabloon.

## In-app berichten op een iPhone X worden niet in de modus Volledig scherm weergegeven.

In-app berichten weergeven in de modus Volledig scherm op een iPhone X:

1. Voeg toe `viewport-fit=cover` in de metatag.

   ```html
   <meta name="viewport" content="viewport-fit=cover">
   ```

1. Stel de juiste opvulling in de CSS in voor het bovenste UI-element, zoals:

   ```html
    topelement {
      padding-top:20px;
      /*Status bar height on iOS 11.0*/
      padding-top:constant(safe-area-inset-top);
      /*Status bar height on iOS 11+ */
      padding-top:env(safe-area-inset-top);
      } 
   ```

   Deze instellingen verhinderen dat de UI-elementen botsen met de statusbalk.
