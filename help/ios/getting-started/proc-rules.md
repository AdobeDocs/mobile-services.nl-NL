---
description: De verwerkingsregels worden gebruikt om de gegevens te kopiëren die u in contextgegevensvariabelen naar gebeurtenissen, steunen, en andere variabelen voor het melden verzendt.
seo-description: De verwerkingsregels worden gebruikt om de gegevens te kopiëren die u in contextgegevensvariabelen naar gebeurtenissen, steunen, en andere variabelen voor het melden verzendt.
seo-title: Verwerkingsregels en contextgegevens
solution: Marketing Cloud,Analytics
title: Verwerkingsregels en contextgegevens
topic: Developer and implementation
uuid: 51338ccd-fa52-4d9c-97c4-947a4100465d
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Verwerkingsregels en contextgegevens{#processing-rules-and-context-data}

De verwerkingsregels worden gebruikt om de gegevens te kopiëren die u in contextgegevensvariabelen naar gebeurtenissen, steunen, en andere variabelen voor het melden verzendt.

Zie de volgende inhoud voor meer informatie:

* [Opleiding](https://tv.adobe.com/embed/1181/16506/) verwerkingsregels @ top 2013
* Word gemachtigd om verwerkingsregels te gebruiken

   Zie Overzicht [van](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)verwerkingsregels voor meer informatie over verwerkingsregels.

Houd rekening met de volgende informatie wanneer u werkt met verwerkingsregels:

* Groepeer de variabelen van uw contextgegevens door naamruimten te gebruiken, omdat u hiermee een logische volgorde kunt behouden.

   Als u bijvoorbeeld informatie over een product wilt verzamelen, kunt u de volgende variabelen definiëren:

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* Contextgegevensvariabelen worden alfabetisch gesorteerd in de interface met verwerkingsregels, zodat u snel kunt zien welke variabelen zich in dezelfde naamruimte bevinden.

   Gebruik het evar- of prop-nummer om contextgegevenssleutels niet een naam te geven:

   ```js
   "eVar1":"jimbo"
   ```

   Dit zou het *lichtjes* gemakkelijker kunnen maken wanneer u de éénmalige afbeelding in verwerkingsregels uitvoert, maar u verliest leesbaarheid tijdens het zuiveren en toekomstige codeupdates, wat moeilijker kan zijn. Gebruik in plaats daarvan beschrijvende namen voor sleutels en waarden:

   ```js
   "username":"jimbo"
   ```

* Contextvariabelen die tellergebeurtenissen definiëren, moeten op 1 worden ingesteld:

   ```js
   "logon":"1"
   ```

* Contextgegevensvariabelen die incrementele gebeurtenissen definiëren, kunnen de gebeurtenis hebben als de sleutel en de hoeveelheid die moet worden verhoogd als de waarde:

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe behoudt de naamruimte `a.`&quot;. Naast die beperking, om botsingen te vermijden, is het enige vereiste dat de variabelen van contextgegevens in uw login bedrijf uniek zijn.

