---
description: De verwerkingsregels worden gebruikt om de gegevens te kopiëren die u in contextgegevensvariabelen naar gebeurtenissen, steunen, en andere variabelen voor het melden verzendt.
seo-description: De verwerkingsregels worden gebruikt om de gegevens te kopiëren die u in contextgegevensvariabelen naar gebeurtenissen, steunen, en andere variabelen voor het melden verzendt.
seo-title: Verwerkingsregels en contextgegevens
solution: Experience Cloud,Analytics
title: Verwerkingsregels en contextgegevens
topic-fix: Developer and implementation
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
exl-id: 543201fd-8118-485f-8235-26ec8f9bbb11
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 3%

---

# Regels en contextgegevens verwerken {#processing-rules-and-context-data}

De verwerkingsregels worden gebruikt om de gegevens te kopiëren die u in contextgegevensvariabelen naar gebeurtenissen, steunen, en andere variabelen voor het melden verzendt. Zie [Verwerkingsregels](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html) voor meer informatie.

Houd rekening met de volgende informatie wanneer u werkt met verwerkingsregels:

* Groepeer de variabelen van uw contextgegevens door naamruimten te gebruiken, omdat u hiermee een logische volgorde kunt behouden. Als u bijvoorbeeld informatie over een product wilt verzamelen, kunt u de volgende variabelen definiëren:

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

   Dit zou het *slightly* gemakkelijker kunnen maken wanneer u de éénmalige afbeelding in verwerkingsregels voltooit, maar u verliest leesbaarheid tijdens het zuiveren en toekomstige codeupdates, wat moeilijker kan zijn. In plaats daarvan raden we u sterk aan beschrijvende namen te gebruiken voor sleutels en waarden:

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
>Adobe behoudt de naamruimte `"a."`. Om botsingen te vermijden, is het enige andere vereiste dat de variabelen van contextgegevens in uw login bedrijf uniek zijn.
