---
description: Als uw app mobiele webinhoud opent, moet u ervoor zorgen dat bezoekers niet afzonderlijk worden geïdentificeerd wanneer ze van het ene naar het andere mobiele web gaan.
solution: Experience Cloud,Analytics
title: Bezoeker bijhouden tussen een app en een mobiel web
topic-fix: Developer and implementation
uuid: 073572e4-4c55-4b27-b4a7-e4349ccde7bf
exl-id: 7ca98572-138d-48f8-aa2a-d376eebb0b2c
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Bezoekerspatiëring tussen een app en het mobiele web {#visitor-tracking-between-an-app-and-mobile-web}

Als uw app mobiele webinhoud opent, moet u ervoor zorgen dat bezoekers niet afzonderlijk worden geïdentificeerd wanneer ze van het ene naar het andere mobiele web gaan.

## Bezoeker-id&#39;s in apps

De Android-SDK genereert een unieke bezoeker-id wanneer een toepassing wordt geïnstalleerd. Deze id wordt opgeslagen in permanent geheugen op het mobiele apparaat, wordt bij elke hit verzonden en wordt alleen verwijderd wanneer de gebruiker de app verwijdert.

>[!TIP]
>
>Id&#39;s van App-bezoekers blijven aanwezig via upgrades.

## Bezoeker-id&#39;s op het mobiele web

Voor mobiele webimplementaties worden doorgaans dezelfde standaard Analytics `s_code.js` of `AppMeasurement.js` gebruikt als voor desktopsites. De JavaScript-bibliotheken beschikken over eigen methoden voor het genereren van unieke bezoeker-id&#39;s, waardoor een andere bezoeker-id wordt gegenereerd wanneer u mobiele webinhoud opent vanuit uw app.

## Controleren van bezoekers tussen een app en het mobiele web implementeren {#section_1755BCCFD42D456EB2319141030FDDFF}

Dezelfde bezoekers-id gebruiken in de app en op het mobiele web:

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Voor meer informatie, zie *Voeg het dossier SDK en Config aan uw Project IntelliJ IDEA of Eclipse* in [de implementatie van de Kern en levenscyclus](/help/android/getting-started/dev-qs.md) toe.

1. Als u bezoekersinformatie wilt toevoegen aan de URL waarmee de webweergave wordt geopend, roept u `visitorAppendToURL`:

   ```java
   String urlString = "https://www.mydomain.com/index.php"; 
   String urlStringWithVisitorData = Visitor.appendToURL(urlString); 
   Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
   startActivity(browserIntent);
   ```

   U kunt `Visitor.getUrlVariablesAsync` ook aanroepen en uw eigen URL genereren, te beginnen met SDK versie 4.16.0:

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

De de dienstcode van identiteitskaart op het bestemmingsdomein haalt MID uit URL in plaats van het verzenden van een verzoek naar Adobe voor een nieuwe identiteitskaart. De code gebruikt de doorgegeven MID om de bezoeker bij te houden.

Bij hits van de mobiele webinhoud controleert u of de parameter `mid` bij elke treffer aanwezig is en of deze waarde overeenkomt met de parameter `mid` die door de toepassingscode wordt verzonden.

## Problemen met het bijhouden van bezoekers oplossen {#section_9B641F8569E34A089C52AA28EA4C891D}

### Ik zie `Visitor.appendToURL` niet.

Controleer of de Adobe-SDK die in de bovenliggende toepassing is gebundeld, versie 4.12.0 of hoger is.

**Ik zie geen Adobe-id&#39;s in mijn URL.**

* Controleer het volgende:
   * De URL-tekenreeks waarmee de webweergave wordt geopend, is gegenereerd door `Visitor.appendToURL(urlString)`.
   * De Adobe-id&#39;s worden gecodeerd.
Om ervoor te zorgen dat IDs die aan URL worden toegevoegd die wordt geopend, verifieer dat de `adobe_mc` vraagparameter in URL verschijnt.

### Mijn `mid` is in mijn app niet identiek aan mijn webweergave.

* Controleer het volgende:

   * De URL-tekenreeks die wordt gebruikt om de webweergave te openen, is gegenereerd door `Visitor.appendToURL(urlString)`.
   * De URL-tekenreeks bevat Adobe-parameters.

      De tekenreeks moet `adobe_mc="SAMPLE_ID_DATA"` bevatten waarin `"SAMPLE_ID_DATA"` de id&#39;s bevat die worden gegenereerd in de SDK van Adobe Mobile.
   * De `VisitorAPI.js` is versie 1.7.0 of hoger.

Neem contact op met de Adobe Experience Care als deze stappen voor het oplossen van problemen uw problemen niet oplossen.

>[!IMPORTANT]
>
>Als Adobe de implementatie kan valideren, moet u een voorbeeldtoepassing en de bijbehorende site delen.
