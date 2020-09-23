---
description: Met deze informatie kunt u problemen met pushberichten oplossen.
keywords: mobile
seo-description: Met deze informatie kunt u problemen met pushberichten oplossen.
seo-title: Problemen met pushberichten oplossen
solution: Experience Cloud,Analytics
title: Problemen met pushberichten oplossen
topic: Metrics
uuid: 9c4a9371-6691-4a2c-a6c1-b9f901a41599
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---


# Pushberichten oplossen {#troubleshooting-push-messaging}

Met deze informatie kunt u problemen met pushberichten oplossen.

## Waarom zijn er soms vertragingen bij het verzenden van pushberichten?

De volgende soorten vertragingen kunnen aan dupberichten voor de Mobiele Diensten worden geassocieerd:

* Wachten op analysepits

   Elke rapportsuite bevat een instelling om te bepalen wanneer binnenkomende analyseresultaten moeten worden verwerkt. De standaardwaarde is 1 uur op het uur. De daadwerkelijke verwerking van Analytics-hits kan tot 30 minuten duren, maar duurt doorgaans 15 tot 20 minuten. Een rapportsuite werkt bijvoorbeeld elk uur. Als u de verwerkingstijd maximaal 30 minuten meet, kan het 90 minuten duren voordat een binnenkomende hit beschikbaar is voor een pushbericht. Als een gebruiker de app om 9:01 uur heeft gestart, wordt de hit weergegeven in de gebruikersinterface voor mobiele services als een nieuwe unieke gebruiker tussen 10:15 en 10:30 uur.

* Wachten op pushservice

   De pushservice (APNS of FCM) verzendt het bericht mogelijk niet meteen. Hoewel dit soms voorkomt, hebben we een vertraging van 5 tot 10 minuten gezien. Op de pagina van Berichten, kunt u verifiëren dat het duwbericht naar de drukkerij is verzonden door de verbinding voor het bericht te klikken. **[!UICONTROL View]** In het rapport wordt het aantal geslaagde verzendingen naar de pushservice vermeld in de **[!UICONTROL Published]** kolom.

   >[!TIP]
   >
   >De pushservices garanderen niet dat er een bericht wordt verzonden.

   Raadpleeg de desbetreffende documentatie voor meer informatie over de betrouwbaarheid van services:

   * **APNS**: [Kwaliteit van de dienst](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   * **FCM**: [Levensduur van een bericht](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)

## Waarom worden mijn pushberichten afgesneden of worden ze niet uitgebreid?

Bij sommige Android-apparaten moet u mogelijk berichten weergeven `NotificationCompat.BigTextStyle` .
