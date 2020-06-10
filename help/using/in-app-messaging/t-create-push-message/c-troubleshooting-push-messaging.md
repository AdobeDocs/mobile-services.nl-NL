---
description: Met deze informatie kunt u problemen met pushberichten oplossen.
keywords: mobile
seo-description: Met deze informatie kunt u problemen met pushberichten oplossen.
seo-title: Problemen met pushberichten oplossen
solution: Marketing Cloud,Analytics
title: Problemen met pushberichten oplossen
topic: Metrics
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
translation-type: tm+mt
source-git-commit: e6af295ddc5fea2a3e649b659894e6c6123a3457
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 0%

---


# Probleemoplossing voor pushberichten{#troubleshooting-push-messaging}

Met deze informatie kunt u problemen met pushberichten oplossen.

## Waarom zijn er soms vertragingen bij het verzenden van pushberichten?

De volgende soorten vertragingen kunnen aan dupberichten voor de Mobiele Diensten worden geassocieerd:

* **Wachten op analyseresultaten**

   Elke rapportsuite bevat een instelling om te bepalen wanneer binnenkomende analyseresultaten moeten worden verwerkt. De standaardwaarde is om de 1 uur.

   De daadwerkelijke verwerking van Analytics-hits kan tot 30 minuten duren, maar duurt doorgaans 15 tot 20 minuten. Een rapportsuite werkt bijvoorbeeld elk uur. Wanneer u de vereiste verwerkingstijd van maximaal 30 minuten meet, kan het tot 90 minuten duren voordat een binnenkomende hit beschikbaar is voor een pushbericht. Als een gebruiker de app om 9:01 uur heeft gestart, wordt de hit weergegeven in de gebruikersinterface voor mobiele services als een nieuwe unieke gebruiker tussen 10:15 en 10:30 uur.

* **Wachten op de pushservice**

   De pushservice (APNS of GCM) verzendt het bericht mogelijk niet meteen. Hoewel dit soms voorkomt, zijn er gevallen van wachttijden tot 5-10 minuten. U kunt verifiëren dat het pushbericht naar de pushservice is verzonden door de **[!UICONTROL Report]** weergave van het pushbericht te bekijken, het bericht in de **[!UICONTROL Message History]** tabel te zoeken en de **[!UICONTROL Published]** telling te bekijken.

   >[!TIP]
   >
   >Dit aantal is het aantal geslaagde verzendingen naar de pushservice(s). De pushservices garanderen niet dat er een bericht wordt verzonden.

   Voor meer informatie over de betrouwbaarheid van de dienst, zie:

   * [Kwaliteit van de dienst](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5l)
   * [De levensduur van een bericht](https://developers.google.com/cloud-messaging/concept-options#lifetime).

## Waarom is mijn Android GCM API-sleutel ongeldig?

* **Ongeldige API-sleutel**

   De API-sleutel kan om de volgende redenen ongeldig zijn:

   * De API-sleutel die u hebt opgegeven, is geen serversleutel met de juiste GCM API-sleutelwaarde.
   * Met de serversleutel zijn de IP&#39;s toegestaan en wordt voorkomen dat de servers van Adobe een pushbericht verzenden.

* **De geldigheid van de API-sleutel bepalen**

   Voer de volgende opdracht uit om de geldigheid van de API-sleutel te bepalen:

   **Android**

   ```java
   # api_key=YOUR_API_KEY
   #curl--header"Authorization:key=$api_key"\
       --headerContent-Type:"application/json"\ 
       https://gcm-http.googleapis.com/gcm/send\
       -d"{\"registration_ids\":[\"ABC\"]}"
   ```

   Een geretourneerde 401 HTTP-statuscode betekent dat de API-sleutel ongeldig is. Anders ziet u iets gelijkaardigs:

   ```java
   {"multicast_id":6782339717028231855,"success":0,"failure":1,
   canonical_ids":0,"results":[{"error":"InvalidRegistration"}]}
   ```

   U kunt de geldigheid van een registratietoken ook controleren door `"ABC"` het token te vervangen.

## Waarom werkt mijn APNS cert niet?

Uw APNS-certificaat is mogelijk ongeldig vanwege de volgende redenen:

* In plaats van het productiecertificaat gebruikt u mogelijk een sandboxcertificaat.
* U gebruikt een nieuw productie-/sandboxcertificaat dat niet wordt ondersteund.
* U gebruikt `.p8` een bestand in plaats van een `.p12` bestand.

## Fouten met pushberichten oplossen

**Een voorbeeld**

In het volgende voorbeeld ziet u hoe u een pushfout kunt verhelpen bij het gebruik van een VRS.

De volgende klant heeft twee iOS-apps:

* Toepassingsnaam: PhotoShop_app_iOS
   * Bovenliggende RSID: AllAdobe PhotoShop_apps
   * VRSID: PhotoShop_iOS_app_SF
   * VRSID-definitiesegment: `a.appid contains “PhotoShop_iOS_app_SF”`
* Toepassingsnaam: PhotoShop_app_iOS
   * Bovenliggende RSID: AllAdobe PhotoShop_apps
   * RSID: PhotoShop_iOS_app_LA
   * VRSID-definitiesegment: `a.os contains “iOS”`

In dit voorbeeld ontvangen alle gebruikers van de *PhotoShop_iOS_app_SF* -app *het pushbericht als een Photoshop-medewerker een push verzendt naar de app* PhotoShop_iOS_app_SF. Maar als de werknemer een bericht naar de app *PhotoShop_iOS_app_LA* verzendt, omdat het VRSID-definitiesegment onjuist is (`iOS` in plaats van `a.os contains "PhotoShop_iOS_app_LA"`), wordt het bericht naar **alle** iOS-gebruikers verzonden in *AllAdobe PhotoShop_apps*. Hoewel het bericht nog steeds naar gebruikers van *PhotoShop_iOS_app_LA* gaat, worden in het bericht ook de push-id&#39;s voor gebruikers van *PhotoShop_iOS_app_SF* afgewezen, omdat de *PhotoShop_iOS_app_SF* -app een ander certificaat heeft. Als het segment als `a.os contains “PhotoShop_iOS_app_LA”`gedefinieerd was, zou het pushbericht alleen naar *PhotoShop_iOS_app_LA* -gebruikers zijn verzonden.

Als de id&#39;s met het *PhotoShop_IOS_app_LA* -pushcertificaat worden doorgegeven, worden de push-id&#39;s voor de *PhotoShop_iOS_app_SF* geretourneerd als `invalid`.

>[!CAUTION]
>
>Nadat u een pushbericht hebt gemaakt voor een toepassing die een VRS gebruikt en op **[!UICONTROL Save & Send]** deze knop klikt, verschijnt er een waarschuwing die u eraan herinnert dat elke vermelde app een geldig certificaat **moet** hebben. Als elke app **geen** geldig certificaat heeft, worden de vermelde publiekssegmenten voor onbepaalde tijd geweigerd en kunt u in de toekomst mogelijk geen pushberichten naar de betrokken gebruikers verzenden. Voor meer informatie over publiekssegmenten, zie [Publiek: publieksopties voor pushberichten](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md)definiëren en configureren.
