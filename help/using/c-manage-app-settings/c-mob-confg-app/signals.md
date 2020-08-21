---
description: Met Postbacks kunt u gegevens die door Adobe Mobile zijn verzameld, naar een aparte externe server verzenden. Door de zelfde trekkers en de eigenschappen te gebruiken die u gebruikt om een in-app bericht te tonen, kunt u de Mobiele Diensten vormen om aangepaste gegevens naar een derdebestemming te verzenden.
seo-description: Met Postbacks kunt u gegevens die door Adobe Mobile zijn verzameld, naar een aparte externe server verzenden. Door de zelfde trekkers en de eigenschappen te gebruiken die u gebruikt om een in-app bericht te tonen, kunt u de Mobiele Diensten vormen om aangepaste gegevens naar een derdebestemming te verzenden.
seo-title: Postbacks configureren
title: Postbacks configureren
uuid: a026575c-057b-4868-b6c8-9514cbc32b4d
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 1%

---


# Postbacks configureren {#configure-postbacks}

Met Postbacks kunt u gegevens die door Adobe Mobile zijn verzameld, naar een aparte externe server verzenden. Door de zelfde trekkers en de eigenschappen te gebruiken die u gebruikt om een in-app bericht te tonen, kunt u de Mobiele Diensten vormen om aangepaste gegevens naar een derdebestemming te verzenden.

>[!IMPORTANT]
>
>Om postbacks te gebruiken, moet u 4.6 SDK of later installeren. Zie [Android - Postbacks](/help/android/analytics-main/postbacks/postbacks.md) of [iOS - Postbacks](/help/ios/analytics-main/postback/postback.md)voor meer informatie.

1. Klik op de naam van de gewenste app om naar de pagina Toepassingsinstellingen beheren te gaan en klik op de **[!UICONTROL Manage Postbacks]** koppeling rechtsboven.
1. Klik op **[!UICONTROL Create Postback]**.
1. Typ de volgende informatie in de velden:

   * **[!UICONTROL Postback Type]**

      Kies **[!UICONTROL Custom]**. Sjablonen zijn in de toekomst beschikbaar.

   * **[!UICONTROL Name]**

      Geef een beschrijvende naam op voor de postback.

   * **[!UICONTROL URL]**

      Specificeer een geldig eindpunt URL (met aangewezen vraagparameters zoals nodig voor GET- verzoeken). U verkrijgt deze URL van de partij u de gegevens naar (ad server of uw eigen eindpunt) verzendt. Bijvoorbeeld `https://my.server.com/?user=bob&amp;zip=90210&amp;c16=4.6.0-iOS&amp;c27=cln,132`.

   * **[!UICONTROL Context Variable]**

      Markeer gedeelten van de URL en selecteer de gewenste contextvariabele in de vervolgkeuzelijst. U kunt ook contextvariabelen in de URL invoegen en de URL vervangt alle sjabloonvariabelen door waarden uit de hit.

   * **[!UICONTROL Add Post Body]**

      Geef aanvullende inhoud van de berichttekst op, bijvoorbeeld in geval van een aanvraag. Als u tekst voor de berichttekst opgeeft, geeft u het inhoudstype voor de berichttekst op. Bijvoorbeeld, `application/json`.

   * **[!UICONTROL Timeout (in seconds)]**

      Geef de tijd (in seconden) op die moet worden gewacht tot de reservekopie is gemaakt.

   * **[!UICONTROL Trigger(s)]**

      Geef een of meer gegevenstags en -voorwaarden op die de postback activeren. U kunt bijvoorbeeld kiezen **[!UICONTROL Crashed]** als trigger en **[!UICONTROL Exists]** als voorwaarde om de terugmelding te activeren wanneer de toepassing vastloopt. U kunt ook opgeven welke metriek de postback activeert. U kunt bijvoorbeeld **[!UICONTROL Device Name]** als trigger **[!UICONTROL Equals]** en **[!UICONTROL iPhone 6 Plus]** als voorwaarde selecteren om de postback te activeren wanneer de toepassing vastloopt op iPhone 6 Plus-apparaten.

   * **[!UICONTROL Trait(s)]**
   Geef op wie het bericht kan zien wanneer het wordt geactiveerd. De opties omvatten **[!UICONTROL Session Length]**, **[!UICONTROL First Launch Date]**, en **[!UICONTROL App ID]**.

1. Klik **[!UICONTROL Save]** om de postback te maken en deze aan de **[!UICONTROL Manage Postbacks]** lijst toe te voegen.

   Voer een van de volgende handelingen uit om het terugsturen in de toekomst te activeren:

   * Schakel het selectievakje naast de postback in de **[!UICONTROL Manage Postbacks]** lijst in en klik op **[!UICONTROL Activate Selected]**.
   * Klik **[!UICONTROL Save & Activate]** om uw wijzigingen op te slaan en de terugzending onmiddellijk te activeren.
