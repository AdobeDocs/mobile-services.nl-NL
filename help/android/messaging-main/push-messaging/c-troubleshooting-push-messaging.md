---
description: Met deze informatie kunt u problemen met pushberichten oplossen.
keywords: mobiel
solution: Experience Cloud Services,Analytics
title: Problemen met pushberichten oplossen
topic-fix: Metrics
uuid: 9c4a9371-6691-4a2c-a6c1-b9f901a41599
exl-id: 82b89f56-f43e-4b0d-80c5-5bff4013e5f7
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Pushberichten oplossen {#troubleshooting-push-messaging}

Met deze informatie kunt u problemen met pushberichten oplossen.

## Waarom zijn er soms vertragingen bij het verzenden van pushberichten?

De volgende typen vertragingen kunnen worden geassocieerd met pushberichten voor Mobile Services:

* Wachten op analysepits

   Elke rapportsuite bevat een instelling om te bepalen wanneer binnenkomende analyseresultaten moeten worden verwerkt. De standaardwaarde is 1 uur op het uur. De daadwerkelijke verwerking van Analytics-hits kan tot 30 minuten duren, maar duurt doorgaans 15 tot 20 minuten. Een rapportsuite werkt bijvoorbeeld elk uur. Als u de verwerkingstijd maximaal 30 minuten meet, kan het 90 minuten duren voordat een binnenkomende hit beschikbaar is voor een pushbericht. Als een gebruiker de app om 9:01 uur heeft gestart, wordt de hit weergegeven in de gebruikersinterface van Mobile Services als een nieuwe unieke gebruiker tussen 10:15 en 10:30.

* Wachten op pushservice

   De pushservice (APNS of FCM) verzendt het bericht mogelijk niet meteen. Hoewel dit soms voorkomt, hebben we een vertraging van 5 tot 10 minuten gezien. Op de pagina Berichten kunt u controleren of het pushbericht naar de pushservice is verzonden door op de knop **[!UICONTROL View]** koppeling voor het bericht. In het rapport wordt het aantal geslaagde verzendingen naar de pushservice vermeld in het dialoogvenster **[!UICONTROL Published]** kolom.

   >[!TIP]
   >
   >De pushservices garanderen niet dat er een bericht wordt verzonden. Raadpleeg de desbetreffende documentatie voor meer informatie over de betrouwbaarheid van services:
   >
   >* **APNS**: [Kwaliteit van de dienst](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   >* **FCM**: [Levensduur van een bericht](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)


## Waarom worden mijn pushberichten afgesneden of worden ze niet uitgebreid?

Bij sommige Android-apparaten moet u `NotificationCompat.BigTextStyle` bij het weergeven van berichten.
