---
description: De regels van de verwerking worden gebruikt om de gegevens te kopiëren die u in de variabelen van contextgegevens naar eVars, steunen, en andere variabelen voor het melden verzendt.
solution: Experience Cloud,Analytics
title: Verwerkingsregels en contextgegevens
topic-fix: Developer and implementation
uuid: 51338ccd-fa52-4d9c-97c4-947a4100465d
exl-id: a3968160-42c4-4671-b541-c14639b8a451
source-git-commit: 1fa6111d6bf1c2d36f15d2f037718646a035435a
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Verwerkingsregels en contextgegevens{#processing-rules-and-context-data}

De regels van de verwerking worden gebruikt om de gegevens te kopiëren die u in de variabelen van contextgegevens naar eVars, steunen, en andere variabelen voor het melden verzendt.

Voor meer informatie over verwerkingsregels, zie [Overzicht van de Regels van de Verwerking](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) in de documentatie van Adobe Analytics.

Houd rekening met de volgende informatie wanneer u werkt met verwerkingsregels:

* Groepeer de variabelen van uw contextgegevens door naamruimten te gebruiken, omdat u hiermee een logische volgorde kunt behouden.

   Als u bijvoorbeeld informatie over een product wilt verzamelen, kunt u de volgende variabelen definiëren:

   ```js
   "product.type":"hat";
   "product.team":"mariners";
   "product.color":"blue";
   ```

* Contextgegevensvariabelen worden alfabetisch gesorteerd in de interface met verwerkingsregels, zodat u snel kunt zien welke variabelen zich in dezelfde naamruimte bevinden.

   Gebruik het eVar- of propnummer om contextgegevenssleutels niet een naam te geven:

   ```js
   "eVar1":"jimbo";
   ```

   Dit zou het *slightly* gemakkelijker kunnen maken wanneer u de éénmalige afbeelding in verwerkingsregels uitvoert, maar u verliest leesbaarheid tijdens het zuiveren en toekomstige codeupdates, die moeilijker kunnen zijn. Gebruik in plaats daarvan beschrijvende namen voor sleutels en waarden:

   ```js
   "username":"jimbo";
   ```

* Contextvariabelen die tellergebeurtenissen definiëren, moeten op 1 worden ingesteld:

   ```js
   "logon":"1";
   ```

* Contextgegevensvariabelen die incrementele gebeurtenissen definiëren, kunnen de gebeurtenis hebben als de sleutel en de hoeveelheid die moet worden verhoogd als de waarde:

   ```js
   "levels completed":"6";
   ```

>[!TIP]
>
>Adobe behoudt de naamruimte &quot; `a.`&quot;. Naast die beperking, om botsingen te vermijden, is het enige vereiste dat de variabelen van contextgegevens in uw login bedrijf uniek zijn.
