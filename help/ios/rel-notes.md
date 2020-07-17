---
description: Opmerkingen bij de release en bekende problemen met iOS SDK's 4.x voor Experience Cloud Solutions.
seo-description: Opmerkingen bij de release en bekende problemen met iOS SDK's 4.x voor Experience Cloud Solutions.
seo-title: Release-opmerkingen
solution: Marketing Cloud,Analytics
title: Release-opmerkingen
topic: Developer and implementation
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
translation-type: tm+mt
source-git-commit: 48c3addeb929f3356990ef55b44f93dd4bb2f728
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 3%

---


# Releaseopmerkingen {#release-notes}

Hier volgt een overzicht van de opmerkingen bij de release, bekende problemen en hotfix-informatie voor iOS SDK&#39;s 4.x voor Experience Cloud Solutions:

**16 juli 2020: Versie 4.19.3**

* Algemeen - Vaste een insect die zuiverde URLs met veelvoudige gelijken binnen vraagparam verhinderde worden behoorlijk behandeld.

**24 maart 2020: Versie 4.19.2**

* Algemeen - Bepaalde lekken in Target-code zijn gecorrigeerd.

**12 maart 2020: Versie 4.19.1**

* Algemeen - lost een potentiële die botsing op wanneer de Swift nummers in contextgegevens voor het volgen van vraag worden veroorzaakt.
* Target - Target Session ID wordt nu toegevoegd als een contextegegevensparameter &quot;a.target.sessionId&quot; in de interne hit Analytics for Target die naar Adobe Analytics wordt verzonden.

**4 februari 2020: Versie 4.19.0**

* Levenscyclus - Er is een nieuwe API toegevoegd, pauseCollectingLifecycleData, om de abnormale gegevens over de sessielengte te beperken die door sommige oude iOS-apparaten zijn gemeld.

**8 november 2019: Versie 4.18.9**

* In App Messaging - Probleem verholpen waarbij in cache opgeslagen of gebundelde afbeeldingen niet in de volledige-schermberichten konden worden geladen.

**20 september 2019: Versie 4.18.8**

* In App Messaging:

   * Op apparaten met iOS 10 of hoger wordt het `UserNotifications` framework nu gebruikt om lokale meldingen te plannen voor apps die zijn gekoppeld aan de `UserNotifications.framework`toepassing.
   * Volledig scherm berichten gebruiken nu WKWebViews van `WebKit.framework`, die in uw Xcode project moeten worden verbonden.
   * Probleem verholpen waarbij de aankliklading met één druk niet kon worden gebruikt als kenmerken voor In-App Overseinen.
   * Probleem met vastlopen verholpen.

* Algemeen - Het probleem waarbij SDK-gegevens werden gesynchroniseerd met de geparafeerde watchOS-app bij elke Analytics-aanroep is opgelost.

**2 augustus 2019: Versie 4.18.7**

* Een wijziging die werd geïntroduceerd in versie 4.18.6, die in sommige omgevingen tot een crash leidde op apparaten met een iOS-versie ouder dan 11.0.

* Adobe Target: De `requestLocationParameters` eigenschap is toegevoegd in `ADBTargetRequestObject`, waardoor de IMAPID kan worden verzonden bij Target-aanvragen.

**18 juli 2019: Versie 4.18.6**

* Adobe Target: Alle verzoeken omvatten nu de cliënt en `sessionId` in de URL vraagparameters.
* Adobe Target: Een geheugenlek verholpen.
* Bezoeker-id-service: De `visitorAppendToURL` API&#39;s en de API&#39; `visitorGetUrlVariablesAsync` s coderen hun retourwaarden niet meer.

   Door de dubbele codering werden de geretourneerde waarden van deze API&#39;s gemarkeerd door bepaalde beveiligingsrevisies.

**5 juni 2019: Versie 4.18.5**

* Analytics - Voeg de status &#39;push-in&#39; toe aan de gegevens van de levenscyclus wanneer pushberichten zijn ingeschakeld.

**24 mei 2019: Versie 4.18.4**

* Bezoekersidentiteitskaart de Dienst - verhoogde de terugkeeronderbreking voor
   `visitorGetUrlVariablesAsync` API tot 30 seconden.

* De Dienst van identiteitskaart van de bezoeker - de `setPushIdentifier` API vraag verzendt nu een synchronisatievraag naar de Dienst van identiteitskaart van de Bezoeker telkens als het wordt geroepen.

Zie Opmerkingen bij de release van [Adobe Experience Cloud voor meer informatie over de opmerkingen bij de huidige en vorige release voor alle oplossingen](https://docs.adobe.com/content/help/nl-NL/release-notes/experience-cloud/current.html).
