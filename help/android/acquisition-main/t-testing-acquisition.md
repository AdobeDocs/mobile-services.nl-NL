---
description: Met de volgende informatie kunt u een koppeling naar een verouderde acquisitiecampagne uitvoeren op een Android-apparaat.
keywords: android;library;mobile;sdk
seo-description: Met de volgende informatie kunt u een koppeling naar een verouderde acquisitiecampagne uitvoeren op een Android-apparaat.
seo-title: Verouderde overname testen
solution: Marketing Cloud,Analytics
title: Verouderde overname testen
topic: Developer and implementation
uuid: bb7ace96-68eb-4f43-b3cf-af80730b9cee
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Verouderde overname testen {#testing-legacy-acquisition}

Met de volgende informatie kunt u een koppeling naar een verouderde acquisitiecampagne uitvoeren op een Android-apparaat.

Als de mobiele app nog niet in Google Play is, kunt u elke mobiele app als doel selecteren wanneer u de koppeling voor de campagne maakt. Dit is alleen van invloed op de app waarnaar de verwervingsserver u omleidt, nadat u op de verwervingskoppeling klikt en niet op de mogelijkheid om de verwervingskoppeling te testen. Parameters van de queryreeks worden doorgegeven aan de Google Play-winkel, die tijdens de installatie worden doorgegeven aan de app als onderdeel van een campagne-uitzending. Voor het testen van het aanschaffen van mobiele apps voor Roundtrip is de simulatie van dit type uitzending vereist.

Telkens wanneer een test wordt uitgevoerd, moet de app opnieuw zijn geïnstalleerd of moeten gegevens worden gewist **[!UICONTROL Settings]**. Dit zorgt ervoor dat de aanvankelijke levenscyclusmetriek die met de de koordparameters van de campagnerequery wordt geassocieerd worden verzonden wanneer app voor het eerst wordt gelanceerd.

1. In Mobiele Diensten UI, produceer een verouderde aanschafcampagne URL.

   Zie Koppelingen [voor oudere overnames](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md)gebruiken voor meer informatie.
1. Sluit het apparaat aan een computer aan, lanceer ADB Shell, en lanceer de toepassing op het apparaat.
1. Verzend een uitzending in de volgende indeling:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.example.adobetesttapp/com.google.analytics.tracking.android.CampaignTrackingReceiver --es "referrer" "utm_source=testSource&utm_medium=testMedium&utm_term=testTerm&utm_content=testContent&utm_campaign=testCampaign&trackingcode=trackingvalue"
   ```

1. Voer de volgende stappen uit:
   1. Vervangen `com.example.adobetesttapp.com` met omgekeerde DNS-invoer van uw toepassing.
   1. Werk de ontvangerverwijzing bij met de locatie-referentie voor het bijhouden van de campagne in uw app.
   1. Vervang waarden die zijn gekoppeld aan `utm_source`, `utm_medium`, `utm_term`, `utm_content`, `utm_campaign`, enzovoort, door de juiste waarden.

Als de uitzending is gelukt, wordt een reactie weergegeven die lijkt op de onderstaande reactie:

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

Er wordt ook een verzoek om een afbeelding verzonden naar de gegevensverzamelingsservers van Adobe. Als de SDK wacht op de volledige duur van de verwijzingsonderbreking, die u instelt in stap 1, met een afbeeldingsverzoek dat geen campagneparameters bevat, is de uitzending mislukt.
