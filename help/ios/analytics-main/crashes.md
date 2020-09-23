---
description: Deze informatie helpt u begrijpen hoe de neerstortingen worden gevolgd en de beste praktijken om valse neerstortingen te behandelen.
seo-description: Deze informatie helpt u begrijpen hoe de neerstortingen worden gevolgd en de beste praktijken om valse neerstortingen te behandelen.
seo-title: App vastlopen bijhouden
solution: Experience Cloud,Analytics
title: App vastlopen bijhouden
topic: Developer and implementation
uuid: 4f81988b-198a-4ba9-ad53-78af90e43856
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---


# Toepassingscrashes bijhouden {#track-app-crashes}

Deze informatie helpt u begrijpen hoe de neerstortingen worden gevolgd en de beste praktijken om valse neerstortingen te behandelen.

>[!IMPORTANT]
>
>U moet een upgrade uitvoeren naar iOS SDK versie 4.8.6. Deze bevat belangrijke wijzigingen die voorkomen dat false vastlopen wordt gemeld.

## Wanneer rapporteert Adobe een crash?

Als uw toepassing wordt beëindigd zonder eerst achtergrond te hebben, meldt de SDK dat de toepassing de volgende keer dat de app wordt gestart, vastloopt.

## Hoe werkt een melding van een ongeluk?

iOS gebruikt systeemmeldingen waarmee ontwikkelaars verschillende statussen en gebeurtenissen in de levenscyclus van de toepassing kunnen volgen en erop kunnen reageren.

De AdobeMobile iOS SDK heeft een meldingshandler die reageert op het `UIApplicationDidEnterBackgroundNotification` bericht. In deze code wordt een waarde ingesteld die aangeeft dat de gebruiker een achtergrond voor de toepassing heeft ingesteld. Als die waarde niet kan worden gevonden bij een volgende keer starten, wordt een crash gerapporteerd.

## Waarom crasht Adobe zo?

Deze methode voor het meten van crashes biedt een antwoord op hoog niveau op de vraag *Heeft de gebruiker mijn app opzettelijk afgesloten?*

Crash reporting libraries door bedrijven als Apteligent (voorheen Crittercisme) gebruiken een global `NSException` handler voor gedetailleerdere crashrapportage. Uw app mag niet meer dan een van deze handlers hebben. Adobe besloot geen globale `NSException` manager uit te voeren om bouwstijlfouten te verhinderen, wetend dat onze klanten andere botsingsrapporteringsleveranciers zouden kunnen gebruiken.

## Wat kan ertoe leiden dat een fout wordt gemeld?

Van de volgende scenario&#39;s is bekend dat ze er ten onrechte toe leiden dat de SDK een crash meldt:

* Als u foutopsporing uitvoert met Xcode en de toepassing opnieuw start terwijl deze zich op de voorgrond bevindt, loopt de toepassing vast.

   >[!TIP]
   >
   >U kunt voorkomen dat de toepassing vastloopt door de toepassing te achtergronderen voordat u de app opnieuw vanuit Xcode start.

* Als uw app op de achtergrond wordt uitgevoerd en Analytics via een andere oproep dan `trackActionFromBackground`, `trackLocation`of `trackBeacon`, wordt de app beëindigd (handmatig of door het besturingssysteem) terwijl deze op de achtergrond wordt uitgevoerd en de volgende keer dat de app wordt gestart, vastloopt.

   >[!TIP]
   >
   >Achtergrondactiviteit die zich buiten de `lifecycleTimeout` drempelwaarde voordoet, kan ook resulteren in een extra valse start.

* Als uw app op de achtergrond wordt gestart als gevolg van een ophaalbewerking op de achtergrond, een update van de locatie, enzovoort, en door het besturingssysteem wordt beëindigd zonder naar de voorgrond te gaan, resulteert de volgende opstart (achtergrond of voorgrond) in een crash.
* Als u programmatisch de pauzekarkering van Adobe verwijdert `NSUserDefaults`, terwijl de app op de achtergrond wordt uitgevoerd, loopt de volgende keer dat u de app start of hervat, vast.

## Hoe kan ik voorkomen dat valse crashes worden gemeld?

De volgende werkwijzen kunnen u helpen voorkomen dat valse crashes worden gemeld:

* In iOS SDK 4.8.6 werd code toegevoegd om beter te bepalen of een nieuwe levenscyclussessie eigenlijk wordt gewild.

   Deze code corrigeert de fout crashes #2 en #3 in de vorige sectie.

* Zorg ervoor dat u uw ontwikkeling tegen niet-productie rapportsuites uitvoert, die valse crash #1 zou moeten verhinderen voor te komen.
* Verwijder of wijzig geen waarden die door de AdobeMobile SDK worden ingevoerd `NSUserDefaults`.

   Als deze waarden buiten de SDK worden gewijzigd, zijn de gerapporteerde gegevens ongeldig.

