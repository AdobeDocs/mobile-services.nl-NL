---
description: Met de volgende informatie kunt u een koppeling naar een verouderde acquisitiecampagne op een Android-apparaat routeren.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Verouderde overname testen
topic-fix: Developer and implementation
uuid: bb7ace96-68eb-4f43-b3cf-af80730b9cee
exl-id: 43e3b24e-e8bc-407c-b788-5ab85e459a90
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Verouderde overname testen {#testing-legacy-acquisition}

Met de volgende informatie kunt u een koppeling naar een verouderde acquisitiecampagne op een Android-apparaat routeren.

Als de mobiele app zich nog niet in Google Play bevindt, kunt u elke mobiele app als doel selecteren wanneer u de koppeling voor de campagne maakt. Dit is alleen van invloed op de app waarnaar de verwervingsserver u omleidt, nadat u op de verwervingskoppeling klikt en niet op de mogelijkheid om de verwervingskoppeling te testen. Parameters van de queryreeks worden doorgegeven aan de Google Play-winkel. Deze worden tijdens de installatie doorgegeven aan de app als onderdeel van een campagneuitzending. Voor het testen van het aanschaffen van mobiele apps voor Roundtrip is de simulatie van dit type uitzending vereist.

De app moet nieuw zijn geïnstalleerd of gegevens moeten zijn gewist **[!UICONTROL Settings]**, elke keer dat een test wordt uitgevoerd. Dit zorgt ervoor dat de aanvankelijke levenscyclusmetriek die met de de koordparameters van de campagnerequery wordt geassocieerd worden verzonden wanneer app voor het eerst wordt gelanceerd.

1. In de gebruikersinterface van Mobile Services genereert u een URL voor een verouderde acquisitiecampagne.

   Zie voor meer informatie [Koppelingen voor verouderde overname gebruiken](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).
1. Sluit het apparaat aan een computer aan, lanceer ADB Shell, en lanceer de toepassing op het apparaat.
1. Verzend een uitzending in de volgende indeling:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.example.adobetesttapp/com.google.analytics.tracking.android.CampaignTrackingReceiver --es "referrer" "utm_source=testSource&utm_medium=testMedium&utm_term=testTerm&utm_content=testContent&utm_campaign=testCampaign&trackingcode=trackingvalue"
   ```

1. Voer de volgende stappen uit:
   1. Vervangen `com.example.adobetesttapp.com` met omgekeerde DNS-invoer van uw toepassing.
   1. Werk de ontvangerverwijzing bij met de locatie-referentie voor het bijhouden van de campagne in uw app.
   1. Waarden vervangen die zijn gekoppeld aan `utm_source`, `utm_medium`, `utm_term`, `utm_content`, `utm_campaign`, enzovoort, met de juiste waarden.

Als de uitzending is gelukt, wordt een reactie weergegeven die lijkt op de onderstaande reactie:

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

U zult ook een verzoek dat naar de servers van de beeldinzameling van Adobe wordt verzonden zien. Als de SDK wacht op de volledige duur van de verwijzingsonderbreking, die u instelt in stap 1, met een afbeeldingsverzoek dat geen campagneparameters bevat, is de uitzending mislukt.
