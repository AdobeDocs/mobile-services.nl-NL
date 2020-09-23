---
description: Met deze informatie kunt u problemen met pushberichten oplossen.
keywords: mobile
seo-description: Met deze informatie kunt u problemen met pushberichten oplossen.
seo-title: Problemen met pushberichten oplossen
solution: Experience Cloud,Analytics
title: Problemen met pushberichten oplossen
topic: Metrics
uuid: 87d7dcb6-82a8-46e3-a6ed-7f895a22f2af
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '356'
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
   >* **APNS**: [Kwaliteit van de dienst](https://developer.apple.com/documentation/usernotifications)
      >
      >
   * **GCM**: [Levensduur van een bericht](https://developers.google.com/cloud-messaging/concept-options)


## Hoe kan ik mijn Apple Push Service Certificate vernieuwen?

Voor het verzenden van pushberichten is een geldig Push Service Certificate vereist. Mobiele services stellen u op de hoogte wanneer uw certificaat bijna verlopen is of verlopen is. Als u deze melding ontvangt, voert u de volgende stappen uit om uw certificaat te vernieuwen:

1. Klik op **[!UICONTROL Manage App Settings]**.
2. Als u het huidige certificaat wilt verwijderen, schuift u naar **[!UICONTROL Push Services]** en klikt u **[!UICONTROL Delete]**.
3. Configureer en test een nieuw certificaat.

   Voor meer informatie, zie [Vereisten om het Overseinen van de Duw toe te laten](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)

4. Klik op **[!UICONTROL Save]**.

## Waarom kan ik mijn pushberichten niet zien in een iOS-simulator?

iOS-simulators bieden geen ondersteuning voor pushberichten.
