---
description: Opmerkingen bij de release en bekende problemen met Android SDK 4.x voor Experience Cloud Solutions.
seo-description: Opmerkingen bij de release en bekende problemen met Android SDK 4.x voor Experience Cloud Solutions.
seo-title: Opmerkingen bij de release
solution: Marketing Cloud,Analytics
title: Opmerkingen bij de release
topic: Developer and implementation
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
translation-type: tm+mt
source-git-commit: 712a1107b317f02216e4df8d75fddda67a6f1feb

---


# Opmerkingen bij de release {#release-notes}

Hier volgt een overzicht van de opmerkingen bij de release, bekende problemen en hotfix-informatie voor Android SDK 4.x voor Experience Cloud Solutions:

**16 januari 2020: 4.18.0.**

* Verwerving - Er is een nieuwe API toegevoegd `Analytics.processGooglePlayInstallReferrerUrl(final String url)`ter ondersteuning van de Google Play-API&#39;s van de installatieverwijzing.

   Voor meer informatie over Install Referrer APIs, zie [nog het Gebruiken van InstallBroadcast? Schakel tegen 1 maart 2020 over naar de Play Reference API](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html) .

**20 september 2019: Versie 4.17.10**

* Algemeen: Tekenreeks voor bepaalde regio&#39;s op Android API-niveau 21 of hoger is gemaakt.

**18 juli 2019: Versie 4.17.8**

* Adobe-doel: Alle verzoeken omvatten nu de cliënt en sessionId in de URL vraagparameters.
* Berichten in de app: Probleem verholpen waarbij Android-apps vastliepen toen een bericht werd gestart met een lege klikthrough-URL.
* Bezoeker-id-service: De `Visitor.appendToURL` API&#39;s en de API&#39; `Visitor.getUrlVariablesAsync` s coderen hun retourwaarden niet meer.

   Door de dubbele codering werden de geretourneerde waarden van deze API&#39;s gemarkeerd door bepaalde beveiligingsrevisies.

**6 juni 2019: Versie 4.17.7**

* Algemeen - Voor netwerkaanroepen op minder dan 20 Android-API-niveaus wordt nu TLS 1.1 of TLS 1.2 gebruikt.
* Analyse - De status &#39;push-in&#39; is toegevoegd aan de gegevens van de levenscyclus wanneer pushberichten zijn ingeschakeld.

**24 mei 2019: Versie 4.17.6**

* Bezoekersidentiteitsservice - De
   `setPushIdentifier` De API vraag verzendt nu asynchrone vraag naar de Dienst van identiteitskaart van de Bezoeker telkens als het wordt geroepen.

* De Dienst van identiteitskaart van de bezoeker - verhoogde verbind en lezingonderbreking van 2 seconden tot 5 seconden.


Zie Opmerkingen bij de release van [Adobe Experience Cloud voor meer informatie over de opmerkingen bij de huidige en vorige release voor alle oplossingen](https://marketing.adobe.com/resources/help/en_US/whatsnew/).
