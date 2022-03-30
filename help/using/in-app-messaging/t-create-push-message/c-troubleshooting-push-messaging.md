---
description: Met deze informatie kunt u problemen met pushberichten oplossen.
keywords: mobiel
solution: Experience Cloud Services,Analytics
title: Problemen met pushberichten oplossen
topic-fix: Metrics
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
exl-id: 56feb8e1-e196-4b70-8240-6e41581ca602
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# Probleemoplossing voor pushberichten{#troubleshooting-push-messaging}

Met deze informatie kunt u problemen met pushberichten oplossen.

## Waarom zijn er soms vertragingen bij het verzenden van pushberichten?

De volgende typen vertragingen kunnen worden geassocieerd met pushberichten voor Mobile Services:

* **Wachten op analyseresultaten**

   Elke rapportsuite bevat een instelling om te bepalen wanneer binnenkomende analyseresultaten moeten worden verwerkt. De standaardwaarde is om de 1 uur.

   De daadwerkelijke verwerking van Analytics-hits kan tot 30 minuten duren, maar duurt doorgaans 15 tot 20 minuten. Een rapportsuite werkt bijvoorbeeld elk uur. Wanneer u de vereiste verwerkingstijd van maximaal 30 minuten meet, kan het tot 90 minuten duren voordat een binnenkomende hit beschikbaar is voor een pushbericht. Als een gebruiker de app om 9:01 uur heeft gestart, wordt de hit weergegeven in de gebruikersinterface van Mobile Services als een nieuwe unieke gebruiker tussen 10:15 en 10:30 uur.

* **Wachten op de pushservice**

   De pushservice (APNS of GCM) verzendt het bericht mogelijk niet meteen. Hoewel dit soms voorkomt, zijn er gevallen van wachttijden tot 5-10 minuten. U kunt controleren of het pushbericht naar de pushservice is verzonden door te kijken naar de **[!UICONTROL Report]** weergave van het pushbericht, het bericht zoeken in het dialoogvenster **[!UICONTROL Message History]** en kijken naar de **[!UICONTROL Published]** aantal.

   >[!TIP]
   >
   >De pushservices garanderen niet dat er een bericht wordt verzonden. Raadpleeg de desbetreffende documentatie voor meer informatie over de betrouwbaarheid van services:
   >
   >* **APNS**: [Kwaliteit van de dienst](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   >* **FCM**: [Levensduur van een bericht](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)


## Waarom is mijn Android GCM API-sleutel ongeldig?

* **Ongeldige API-sleutel**

   De API-sleutel kan om de volgende redenen ongeldig zijn:

   * De API-sleutel die u hebt opgegeven, is geen serversleutel met de juiste GCM API-sleutelwaarde.
   * De serversleutel heeft IPs toegestaan en blokkeert servers om een pushbericht te verzenden.

* **De geldigheid van de API-sleutel bepalen**

   Voer de volgende opdracht uit om de geldigheid van de API-sleutel te bepalen:

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

   U kunt ook de geldigheid van een registratietoken controleren door `"ABC"` met het token.

## Waarom werkt mijn APNS cert niet?

Uw APNS-certificaat is mogelijk ongeldig vanwege de volgende redenen:

* In plaats van het productiecertificaat gebruikt u mogelijk een sandboxcertificaat.
* U gebruikt een nieuw productie-/sandboxcertificaat dat niet wordt ondersteund.
* U gebruikt `.p8` bestand in plaats van `.p12` bestand.

## Fouten met pushberichten oplossen

In het volgende voorbeeld ziet u hoe u een pushfout kunt verhelpen bij het gebruik van een VRS.

De volgende klant heeft twee iOS-apps:

* Toepassingsnaam: Photoshop_app_iOS
   * Bovenliggende RSID: AllAdobe Photoshop_apps
   * VRSID: Photoshop_iOS_app_SF
   * VRSID-definitiesegment: `a.appid contains "PhotoShop_iOS_app_SF"`
* Toepassingsnaam: Photoshop_app_iOS
   * Bovenliggende RSID: AllAdobe Photoshop_apps
   * RSID: Photoshop_iOS_app_LA
   * VRSID-definitiesegment: `a.os contains "iOS"`

In dit voorbeeld geldt dat als een Photoshop-medewerker een pushbericht naar de *Photoshop_iOS_app_SF* app, alle *Photoshop_iOS_app_SF-app* gebruikers ontvangen het pushbericht zoals verwacht. Maar als de werknemer een bericht naar de *Photoshop_iOS_app_LA* app, omdat het VRSID-definitiesegment onjuist is (`iOS` in plaats van `a.os contains "PhotoShop_iOS_app_LA"`), wordt het bericht verzonden naar **alles** iOS-gebruikers in *AllAdobe Photoshop_apps*. Hoewel het bericht nog steeds gaat naar *Photoshop_iOS_app_LA* gebruikers, voegt op lijst van gewenste personen het bericht ook duw IDs voor *Photoshop_iOS_app_SF* gebruikers omdat de *Photoshop_iOS_app_SF* app heeft een ander certificaat. Als het segment gedefinieerd was als `a.os contains "PhotoShop_iOS_app_LA"`, zou het pushbericht alleen naar zijn verzonden *Photoshop_iOS_app_LA* gebruikers.

Indien doorgegeven met de *Photoshop_IOS_app_LA* push-certificaat, de push-id&#39;s voor de *Photoshop_iOS_app_SF* terugkomen als `invalid`.

>[!CAUTION]
>
>Nadat u een pushbericht hebt gemaakt voor een toepassing die een VRS gebruikt, klikt u op **[!UICONTROL Save & Send]** verschijnt er een waarschuwing die u eraan herinnert dat elke app die wordt vermeld **moet** beschikken over een geldig certificaat. Als elke app dat doet **niet** Als u over een geldig certificaat beschikt, zijn de publiekssegmenten wellicht oneindig gevoegd op lijst van gewenste personen en kunt u in de toekomst mogelijk geen pushberichten naar de desbetreffende gebruikers verzenden. Voor meer informatie over publiekssegmenten, zie [Publiek: publieksopties voor pushberichten definiëren en configureren](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).
