---
description: Met deze informatie kunt u problemen met pushberichten oplossen.
keywords: mobiel
solution: Experience Cloud,Analytics
title: Problemen met pushberichten oplossen
topic-fix: Metrics
uuid: 87d7dcb6-82a8-46e3-a6ed-7f895a22f2af
exl-id: dda84d30-2a7b-496c-b8f3-3bd6b97076aa
source-git-commit: 1fa6111d6bf1c2d36f15d2f037718646a035435a
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Probleemoplossing voor pushberichten {#troubleshooting-push-messaging}

Met deze informatie kunt u problemen met pushberichten oplossen.

## Waarom zijn er soms vertragingen bij het verzenden van pushberichten?

De volgende soorten vertragingen kunnen aan dupberichten voor de Mobiele Diensten worden geassocieerd:

* **Wachten op analysepits**

   Elke rapportsuite bevat een instelling om te bepalen wanneer binnenkomende analyseresultaten moeten worden verwerkt. De standaardwaarde is 1 uur op het uur. De daadwerkelijke verwerking van Analytics-hits kan tot 30 minuten duren, maar duurt doorgaans 15 tot 20 minuten.

   Een rapportsuite werkt bijvoorbeeld elk uur. Als u de verwerkingstijd maximaal 30 minuten meet, kan het 90 minuten duren voordat een binnenkomende hit beschikbaar is voor een pushbericht. Als een gebruiker de app om 9:01 uur heeft gestart, wordt de hit weergegeven in de gebruikersinterface voor mobiele services als een nieuwe unieke gebruiker tussen 10:15 en 10:30 uur.

* **Wachten op pushservice**

   De pushservice (APNS of GCM) verzendt het bericht mogelijk niet meteen. Hoewel dit soms voorkomt, hebben we een vertraging van 5 tot 10 minuten gezien. Op de pagina van Berichten, kunt u verifiëren dat het duwbericht naar de drukkerij is verzonden door de verbinding van de Mening voor het bericht te klikken. In het rapport wordt het aantal geslaagde verzendingen naar de pushservice vermeld in de kolom Gepubliceerd.

   >[!TIP]
   >
   >De pushservices garanderen niet dat er een bericht wordt verzonden. Raadpleeg de desbetreffende documentatie voor meer informatie over de betrouwbaarheid van services:
   >
   >* **APNS**:  [Kwaliteit van de dienst](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   >* **FCM**:  [Levensduur van een bericht](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)


## Hoe kan ik mijn Apple Push Service Certificate vernieuwen?

Voor het verzenden van pushberichten is een geldig Push Service Certificate vereist. Mobiele services stellen u op de hoogte wanneer uw certificaat bijna verlopen is of verlopen is. Als u deze melding ontvangt, voert u de volgende stappen uit om uw certificaat te vernieuwen:

1. Klik op **[!UICONTROL Manage App Settings]**.
2. Als u het huidige certificaat wilt verwijderen, schuift u naar **[!UICONTROL Push Services]** en klikt u op **[!UICONTROL Delete]**.
3. Configureer en test een nieuw certificaat.

   Voor meer informatie, zie [Vereisten om het Overseinen van de Duw toe te laten](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)

4. Klik op **[!UICONTROL Save]**.

## Waarom kan ik mijn pushberichten niet zien in een iOS-simulator?

iOS-simulators bieden geen ondersteuning voor pushberichten.
