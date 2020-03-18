---
description: Als uw app mobiele webinhoud opent, moet u ervoor zorgen dat bezoekers niet afzonderlijk worden geïdentificeerd wanneer ze van het ene naar het andere mobiele web gaan.
seo-description: Als uw app mobiele webinhoud opent, moet u ervoor zorgen dat bezoekers niet afzonderlijk worden geïdentificeerd wanneer ze van het ene naar het andere mobiele web gaan.
seo-title: Bezoeker bijhouden tussen een app en een mobiel web
solution: Marketing Cloud,Analytics
title: Bezoeker bijhouden tussen een app en een mobiel web
topic: Developer and implementation
uuid: 073572e4-4c55-4b27-b4a7-e4349ccde7bf
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Bezoekerspatiëring tussen een app en het mobiele web {#visitor-tracking-between-an-app-and-mobile-web}

Als uw app mobiele webinhoud opent, moet u ervoor zorgen dat bezoekers niet afzonderlijk worden geïdentificeerd wanneer ze van het ene naar het andere mobiele web gaan.

## Bezoeker-id&#39;s in apps

De Android-SDK genereert een unieke bezoeker-id wanneer een toepassing wordt geïnstalleerd. Deze id wordt opgeslagen in permanent geheugen op het mobiele apparaat, wordt bij elke hit verzonden en wordt alleen verwijderd wanneer de gebruiker de app verwijdert.

>[!TIP]
>
>Id&#39;s van App-bezoekers blijven aanwezig via upgrades.

## Bezoeker-id&#39;s op het mobiele web

Voor mobiele webimplementaties wordt gebruikgemaakt van dezelfde standaard Analytics `s_code.js` of `AppMeasurement.js` die wordt gebruikt in desktopsites. De JavaScript-bibliotheken beschikken over eigen methoden voor het genereren van unieke bezoeker-id&#39;s, waardoor een andere bezoeker-id wordt gegenereerd wanneer u mobiele webinhoud opent vanuit uw app.

## Controleren van bezoekers tussen een app en het mobiele web implementeren {#section_1755BCCFD42D456EB2319141030FDDFF}

Dezelfde bezoekers-id gebruiken in de app en op het mobiele web:

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Voor meer informatie, zie *Voeg het Dossier SDK en Config aan uw IDEA IntelliJ of Project* Eclipse in de implementatie en de levenscyclus [van de](/help/android/getting-started/dev-qs.md)Kern toe.

1. Als u bezoekersinformatie wilt toevoegen aan de URL waarmee de webweergave wordt geopend, roept u `visitorAppendToURL`:

   ```java
   String urlString = "https://www.mydomain.com/index.php"; 
   String urlStringWithVisitorData = Visitor.appendToURL(urlString); 
   Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
   startActivity(browserIntent);
   ```

   U kunt ook uw eigen URL aanroepen `Visitor.getUrlVariablesAsync` en genereren, te beginnen met SDK versie 4.16.0:

   ```java
   final String urlString = "https://www.mydomain.com/index.php"; 
   Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
       @Override 
       public void call(String urlVariables) { 
           final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
           final Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
           startActivity(browserIntent); 
       } 
   });
   ```

De code van de dienst van identiteitskaart op het bestemmingsdomein haalt MID uit URL in plaats van het verzenden van een verzoek naar Adobe voor een nieuwe identiteitskaart. De code gebruikt de doorgegeven MID om de bezoeker bij te houden.

Controleer bij hits in de mobiele webinhoud of de `mid` parameter bij elke treffer aanwezig is en of deze waarde overeenkomt met de `mid` parameter die door de toepassingscode wordt verzonden.

## Problemen met het bijhouden van bezoekers oplossen {#section_9B641F8569E34A089C52AA28EA4C891D}

### Ik zie het niet `Visitor.appendToURL`.

Controleer of de Adobe SDK die in de bovenliggende toepassing is gebundeld, versie 4.12.0 of hoger is.

**Ik zie Adobe-id&#39;s niet in mijn URL.**

* Controleer het volgende:
   * De URL-tekenreeks waarmee de webweergave wordt geopend, is gegenereerd door `Visitor.appendToURL(urlString)`.
   * De Adobe-id&#39;s zijn gecodeerd.
Controleer of de `adobe_mc` queryparameter in de URL wordt weergegeven om ervoor te zorgen dat de id&#39;s die aan de URL worden toegevoegd, ook daadwerkelijk worden weergegeven.

### Mijn `mid` is in mijn app niet identiek aan mijn webweergave.

* Controleer het volgende:

   * De URL-tekenreeks waarmee de webweergave wordt geopend, is gegenereerd door `Visitor.appendToURL(urlString)`.
   * De URL-tekenreeks bevat Adobe-parameters.

      De tekenreeks moet `adobe_mc="SAMPLE_ID_DATA"` waar `"SAMPLE_ID_DATA"` de id&#39;s bevatten die in de Adobe Mobile SDK worden gegenereerd.
   * Het `VisitorAPI.js` is versie 1.7.0 of hoger.

Neem contact op met de Adobe Experience Care als deze stappen voor het oplossen van problemen uw problemen niet oplossen.

>[!IMPORTANT]
>
>Adobe kan de implementatie alleen valideren als u een voorbeeldtoepassing en de bijbehorende site deelt.

