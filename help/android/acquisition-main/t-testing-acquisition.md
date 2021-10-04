---
description: Met de volgende informatie kunt u een koppeling naar een verouderde acquisitiecampagne op een Android-apparaat routeren.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud,Analytics
title: Verouderde overname testen
topic-fix: Developer and implementation
uuid: bb7ace96-68eb-4f43-b3cf-af80730b9cee
exl-id: 43e3b24e-e8bc-407c-b788-5ab85e459a90
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Verouderde overname testen {#testing-legacy-acquisition}

Met de volgende informatie kunt u een koppeling naar een verouderde acquisitiecampagne op een Android-apparaat routeren.

Als de mobiele app nog niet in Google Play is, kunt u elke mobiele app als doel selecteren wanneer u de koppeling voor de campagne maakt. Dit is alleen van invloed op de app waarnaar de verwervingsserver u omleidt, nadat u op de verwervingskoppeling klikt en niet op de mogelijkheid om de verwervingskoppeling te testen. Parameters van de queryreeks worden doorgegeven aan de Google Play-winkel, die tijdens de installatie worden doorgegeven aan de app als onderdeel van een campagne-uitzending. Voor het testen van het aanschaffen van mobiele apps voor Roundtrip is de simulatie van dit type uitzending vereist.

Telkens wanneer een test wordt uitgevoerd, moet de app vers zijn geïnstalleerd of moeten gegevens worden gewist in **[!UICONTROL Settings]**. Dit zorgt ervoor dat de aanvankelijke levenscyclusmetriek die met de de koordparameters van de campagnerequery wordt geassocieerd worden verzonden wanneer app voor het eerst wordt gelanceerd.

1. In Mobiele Diensten UI, produceer een verouderde aanschafcampagne URL.

   Zie [Koppelingen voor oudere overnames gebruiken](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md) voor meer informatie.
1. Sluit het apparaat aan een computer aan, lanceer ADB Shell, en lanceer de toepassing op het apparaat.
1. Verzend een uitzending in de volgende indeling:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.example.adobetesttapp/com.google.analytics.tracking.android.CampaignTrackingReceiver --es "referrer" "utm_source=testSource&utm_medium=testMedium&utm_term=testTerm&utm_content=testContent&utm_campaign=testCampaign&trackingcode=trackingvalue"
   ```

1. Voer de volgende stappen uit:
   1. Vervang `com.example.adobetesttapp.com` met omgekeerde DNS ingang van uw toepassing.
   1. Werk de ontvangerverwijzing bij met de locatie-referentie voor het bijhouden van de campagne in uw app.
   1. Vervang waarden die zijn gekoppeld aan `utm_source`, `utm_medium`, `utm_term`, `utm_content`, `utm_campaign` enzovoort, door de juiste waarden.

Als de uitzending is gelukt, wordt een reactie weergegeven die lijkt op de onderstaande reactie:

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

U zult ook een verzoek dat naar de servers van de beeldinzameling van Adobe wordt verzonden zien. Als de SDK wacht op de volledige duur van de verwijzingsonderbreking, die u instelt in stap 1, met een afbeeldingsverzoek dat geen campagneparameters bevat, is de uitzending mislukt.
