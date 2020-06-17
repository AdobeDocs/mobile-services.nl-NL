---
description: U kunt berichtrapporten weergeven voor in-app- en pushberichten.
keywords: mobile
seo-description: U kunt berichtrapporten weergeven voor in-app- en pushberichten.
seo-title: Berichtenrapporten weergeven
solution: Marketing Cloud,Analytics
title: Berichtenrapporten weergeven
topic: Metrics
uuid: 0ac73a81-388f-4dfd-84d5-21b8db4b8c83
translation-type: tm+mt
source-git-commit: 3b6edc10d042658ef1ca17a203877b7ee09d999d
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---


# Berichtenrapporten weergeven{#view-message-reports}

U kunt berichtrapporten weergeven voor in-app- en pushberichten.

1. Klik ![rapportpictogram](assets/icon_report.png) in de **[!UICONTROL Report]** kolom voor een bericht.
1. (**Optioneel**) Maak een plakfilter voor het rapport of wijzig de tijdsperiode door op het **[!UICONTROL Calendar]** pictogram te klikken.

   Zie [Een plakfilter](/help/using/usage/reports-customize/t-sticky-filter.md)toevoegen voor meer informatie over het maken van een plakfilter.

>[!TIP]
>
>Afhankelijk van het type van bericht u bekijkt, zou het rapport kunnen variëren.

## In-app berichten {#section_90B79BA58E8141F78538C187EB1BF8C7}

Als u rapporten bekijkt voor een bericht in de app, ziet het rapport er ongeveer als volgt uit:

![rapportbericht](assets/report_message.png)

### Metrische gegevens van in-app-berichten

Hier volgt een lijst met de meetgegevens die beschikbaar zijn voor in-app berichten:

* **[!UICONTROL Impression]**, wanneer een bericht wordt geactiveerd.

* **[!UICONTROL Click through]**, wanneer een gebruiker op de **[!UICONTROL Click Through]** knop drukt in een waarschuwing of een bericht op een volledig scherm en wanneer een gebruiker de app opent vanuit een lokaal bericht.

* **[!UICONTROL Cancel]**, wanneer een gebruiker op de **[!UICONTROL Cancel]** knop drukt in een waarschuwing of een bericht op volledig scherm.

* **[!UICONTROL Engagement Rate]**, een berekende metrische waarde uit Adobe Analytics. Dit is het resultaat van het aantal klikdoorhalingen gedeeld door het aantal indrukken.

## Pushberichten {#section_BEAFD858CA194185B6F88903446058E9}

Als u rapporten voor een duwbericht bekijkt, kijkt het rapport gelijkaardig aan de volgende illustratie:

![pushbericht](assets/report_message_push.png)

In het diagram boven wordt het aantal gebruikers weergegeven dat het bericht heeft geopend.

### Metrische gegevens van pushberichten

Hier volgt een lijst met de meetgegevens die beschikbaar zijn voor pushberichten:

* **[!UICONTROL Time]**

   De tijd het bericht aan apparaten van de Mobiele Diensten werd geduwd.

* **[!UICONTROL Status]**

   De status van het bericht en de beschikbare statussen zijn:

   * **[!UICONTROL Cancelled]**
   * **[!UICONTROL Scheduled]**
   * **[!UICONTROL Executing]**
   * **[!UICONTROL Executed]**

* **[!UICONTROL Published]**

   Het aantal apparaattokens dat is verzonden naar Apple Push Notification Service/Firebase Cloud Messaging (APNS/FCM) voor het verzenden van het bericht naar de gebruikersapparaten.

* **[!UICONTROL Failed]**

   Het aantal apparaattokens is niet verzonden naar APNS/FCM. Enkele mogelijke oorzaken van fouten:

   * Een ongeldige pushID

   * Het push-platform (APNS, FCM enzovoort) dat is gegeven om naar te gaan, bestaat niet voor de toepassing van de taak. Het platform verzamelt bijvoorbeeld iOS-pushtokens, maar de APNS-service is niet geconfigureerd.

   * Het bericht zou kunnen ontbroken hebben omdat de dupdienst niet correct werd gevormd of het Mobiele systeem van de Diensten neer is.
   >[!IMPORTANT]
   >
   >Als u een ongebruikelijk groot aantal mislukkingen hebt, controleer uw configuratie van de duwdiensten. Neem contact op met de klantenservice van Adobe als de pushservices correct zijn geconfigureerd.

* **[!UICONTROL Blocklisted]**

   Het aantal apparaattokens dat niet langer geldig is om naar APNS of FCM te worden verzonden. Dit betekent doorgaans dat de app van het apparaat is verwijderd of dat de gebruiker zijn of haar aanmeldingsinstellingen heeft gewijzigd om berichten te ontvangen. Android en iOS verschillen van mening wanneer tokens worden geteld als blocklisted. Android-tokens worden direct weergegeven in het aantal keuzelijsten. iOS-tokens worden aanvankelijk weergegeven als gepubliceerde, maar op basis van feedback van APNS, worden op volgende berichten weergegeven als blokkeerbaar.
