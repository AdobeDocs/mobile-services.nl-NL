---
description: U kunt ervaringsopties configureren voor pushberichten en uitgebreide pushberichten, zoals naam, berichttekst en bestemmingsopties. U kunt ook geavanceerde opties configureren, zoals opties voor het laden van de lading en aangepaste opties voor iOS-apparaten.
keywords: mobiel
seo-description: U kunt ervaringsopties configureren voor pushberichten en uitgebreide pushberichten, zoals naam, berichttekst en bestemmingsopties. U kunt ook geavanceerde opties configureren, zoals opties voor het laden van de lading en aangepaste opties voor iOS-apparaten.
seo-title: Experience Push Message
solution: Experience Cloud,Analytics
title: Experience Push Message
topic-fix: Metrics
uuid: 1a8baf3e-9fea-452c-b0fc-4ba8ac270861
exl-id: 9158487e-6ac5-4f17-a8ff-15de0360ab60
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 0%

---

# Ervaring: pushbericht {#experience-push-message}

U kunt ervaringsopties configureren voor pushberichten en uitgebreide pushberichten, zoals naam, berichttekst en bestemmingsopties. U kunt ook geavanceerde opties configureren, zoals opties voor het laden van de lading en aangepaste opties voor iOS-apparaten.

1. Klik op **[!UICONTROL Experience]** op de pagina Publiek voor een nieuw pushbericht.

   ![Experience push-berichtscherm](assets/experience-push-message.png)

1. Typ een naam voor dit bericht.
1. Typ informatie in de volgende velden in de sectie **[!UICONTROL Message]**:

   * **[!UICONTROL Content]**

      Geef de tekst van het bericht op. U kunt maximaal 140 tekens opgeven.

   * **[!UICONTROL Media URL]**

      Typ de URL van het mediabestand dat u wilt gebruiken in het pushbericht. Voor vereisten om rijke dupberichten te gebruiken, zie *Vereisten voor Rich Push Notifications* hieronder.

      >[!IMPORTANT]
      >
      >Houd rekening met het volgende als u een afbeelding of video wilt weergeven in een pushmelding:
      > * De `attachment-url` gegevens worden behandeld in de duwlading.
      > * De media-URL moet aanvragen van spikes kunnen verwerken.


   * **[!UICONTROL Destination]**

      Selecteer een specifieke bestemming, zoals een web-, diepe of hybride koppeling, om gebruikers te verzenden wanneer zij op het bericht klikken. Zie [Doelen](/help/using/acquisition-main/c-create-destinations.md) voor meer informatie.

      >[!TIP]
      >
      >Wanneer u * **[!UICONTROL Web Link]** of **[!UICONTROL Custom Link]** bestemmingstypes gebruikt, wordt het bestemmingstype niet gevolgd. Alleen **[!UICONTROL Deep Links]** worden bijgehouden.

## Vereisten voor uitgebreide pushmeldingen

Hier volgen de vereisten voor het verzenden van uitgebreide pushberichten:

* **Ondersteunde versies**

   Rijke pushmeldingen worden ondersteund in de volgende versies:
   * Android 4.1.0 of hoger
   * iOS 10 of hoger

      >[!IMPORTANT]
      >
      >De volgende informatie onthouden:
      >* Rijke pushberichten die naar eerdere versies worden verzonden, worden wel verzonden, maar alleen de tekst wordt weergegeven.
      >* Op dit moment is er geen ondersteuning voor toezicht.


* **Bestandsindelingen**

   Hier volgen de ondersteunde bestandsindelingen:
   * Afbeeldingen: JPG en PNG
   * Animaties (alleen iOS): GIF
   * Video&#39;s (alleen iOS): MP4

* **URL-indelingen**
   * Alleen HTTPS

* **Grootte**
   * Afbeeldingen moeten een 2:1-indeling hebben, anders worden ze bijgesneden.

Zie de volgende inhoud voor meer informatie over het configureren van pushberichten met de extensie Rich Push Meldingen:

* [Pushmeldingen ontvangen in Android](/help/android/messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
* [Rich Push-berichten ontvangen in iOS](/help/ios/messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)

Een pushbericht configureren op de pagina Experience:

1. (**Optioneel**) Klik op de koppeling **[!UICONTROL Show Advanced Options]** om aanvullende opties te configureren:

   * **[!UICONTROL Payload: Data]**

      Geef een aangepaste pushlading in JSON die via een pushmelding of een lokale melding naar de app wordt verzonden. De limiet voor Android en iOS is 4 kB.

   * **[!UICONTROL Apple Options: Category]**

      Geef een categorie op voor pushberichten en lokale meldingen. Zie [De meldingsondersteuning van uw app beheren](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW9) in de *iOS-ontwikkelaarsbibliotheek* voor meer informatie.

   * **[!UICONTROL Apple Options: Sound]**

      Geef de naam op van het geluidsbestand dat in uw app-bundel moet worden afgespeeld. Als er geen standaardgeluid voor waarschuwingen is ingesteld, wordt dit geluid afgespeeld. Zie [Kennisondersteuning van uw app beheren](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/SupportingNotificationsinYourApp.html#//apple_ref/doc/uid/TP40008194-CH4-SW10) in de *iOS-ontwikkelaarsbibliotheek* voor meer informatie.

   * **[!UICONTROL Apple Options: Content Available]**

      Selecteer deze optie zodat iOS uw app op de achtergrond activeert wanneer het bericht wordt ontvangen en de app code kan uitvoeren op basis van het bericht dat wordt geladen. Zie [Apple Push Notification Service](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1) in de *iOS Developer Library* voor meer informatie.

1. (Optioneel) Klik op de volgende pictogrammen om een voorvertoning van de lay-out van het bericht weer te geven:

   * **[!UICONTROL x Summary]**

      Hiermee verbergt u het voorvertoningsvenster. Klik ![voorproef](assets/icon_preview.png) om de voorproefruit opnieuw te tonen.

   * **[!UICONTROL Change the orientation]**

      Als u de richting van de voorvertoning wilt wijzigen van Staand in Liggend, klikt u op ![orientation](assets/icon_orientation.png). In het geval van stalen verandert de oriëntatie van een rond horlogevlak in een vierkant horlogevlak.

   * **[!UICONTROL Preview on a user's watch]**

      Klik op ![watch icon](assets/icon_watch.png) om een voorvertoning van uw bericht weer te geven zoals het wordt weergegeven in de stalen van een gebruiker.

   * **[!UICONTROL Preview on a user's mobile phone]**

      Klik op ![telefoonpictogram](assets/icon_phone.png) om een voorvertoning van uw bericht weer te geven zoals deze op de mobiele telefoons van een gebruiker wordt weergegeven.

   * **[!UICONTROL Preview on a user's tablet]**

      Klik op ![tabletpictogram](assets/icon_tablet.png) om een voorvertoning van uw bericht weer te geven op het tablet van de gebruiker.
   Onder aan het voorvertoningsvenster kunt u een beschrijving weergeven van het publiek dat u in de vorige stap hebt geselecteerd.

1. (**Optioneel**) Klik **[!UICONTROL Test]** om uw bericht voor testdoeleinden naar opgegeven apparaten te verzenden.
1. Selecteer de service en typ de pushtokens voor ten minste één apparaat waarop u het bericht wilt duwen.

   Geef de tokens op in een lijst met komma&#39;s als scheidingsteken om het bericht naar meerdere apparaten te sturen.

1. Vorm de het plannen opties voor het bericht.

   Zie [Schema voor meer informatie: pushbericht](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md).
