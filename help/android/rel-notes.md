---
description: Opmerkingen bij de release en bekende problemen met Android SDK 4.x voor Experience Cloud Solutions.
solution: Experience Cloud Services,Analytics
title: Aanvullende informatie
topic-fix: Developer and implementation
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
exl-id: 5cc3d031-5952-4e9b-b551-9402d3c05ccb
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 1%

---

# Aanvullende informatie {#release-notes}

Hier volgt een overzicht van de opmerkingen bij de release, bekende problemen en hotfix-informatie voor Android SDK 4.x voor Experience Cloud Solutions:

## 3 april 2020: 4.18.2.

* In het Overseinen van de App - voor veiligheidsredenen, WebViews die door SDK nu wordt gecreeerd plaatste bezit `setAllowFileAccess` tot `false`.

## 12 maart 2020: 4.18.1.

* Doel - Doel-sessie-id wordt nu toegevoegd als een parameter voor contextgegevens `a.target.sessionId` in de interne hit Analytics-for-Target die naar Adobe Analytics is verzonden.

## 16 januari 2020: 4.18.0.

* Acquisitie - Een nieuwe API toegevoegd. `Analytics.processGooglePlayInstallReferrerUrl(final String url)`, om Google Play Install Referrer APIs te steunen.

   Zie voor meer informatie over de installatieverwijzing-API&#39;s [Wilt u InstallBroadcast nog steeds gebruiken? Schakel tegen 1 maart 2020 over naar de Play Reference API](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html).

## 20 september 2019: Versie 4.17.10

* Algemeen: Tekenreeks voor bepaalde regio&#39;s op Android API-niveau 21 of hoger is gemaakt.

## 18 juli 2019: Versie 4.17.8

* Adobe Target: Alle verzoeken omvatten nu de cliënt en sessionId in de URL vraagparameters.
* Berichten in de app: Probleem verholpen waarbij Android-apps vastliepen toen een bericht werd getriggerd met een lege klikthrough-URL.
* Bezoeker-id-service: De `Visitor.appendToURL` en `Visitor.getUrlVariablesAsync` API&#39;s coderen hun retourwaarden niet meer.

   Door de dubbele codering werden de geretourneerde waarden van deze API&#39;s gemarkeerd door bepaalde beveiligingsrevisies.

## 6 juni 2019: Versie 4.17.7

* Algemeen - Voor netwerkaanroepen op minder dan 20 Android-API-niveaus wordt nu TLS 1.1 of TLS 1.2 gebruikt.
* Analyse - De status &#39;push-in&#39; is toegevoegd aan de gegevens van de levenscyclus wanneer pushberichten zijn ingeschakeld.

## 24 mei 2019: Versie 4.17.6

* Bezoekersidentiteitsservice - De `setPushIdentifier` De API vraag verzendt nu een synchronisatievraag naar de Dienst van identiteitskaart van de Bezoeker telkens als het wordt geroepen.
* De Dienst van identiteitskaart van de bezoeker - verhoogde verbind en las onderbrekingen van 2 seconden aan 5 seconden.

Voor meer informatie over de huidige en vroegere versienota&#39;s voor alle oplossingen, zie [Opmerkingen bij de release van Adobe Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html).
