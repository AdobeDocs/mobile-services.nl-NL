---
description: Met deze informatie kunt u problemen met pushberichten oplossen.
keywords: mobiel
solution: Experience Cloud,Analytics
title: Problemen met pushberichten oplossen
topic-fix: Metrics
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
exl-id: 56feb8e1-e196-4b70-8240-6e41581ca602
source-git-commit: 1fa6111d6bf1c2d36f15d2f037718646a035435a
workflow-type: tm+mt
source-wordcount: '708'
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

   De pushservice (APNS of GCM) verzendt het bericht mogelijk niet meteen. Hoewel dit soms voorkomt, zijn er gevallen van wachttijden tot 5-10 minuten. U kunt controleren dat het pushbericht naar de pushservice is verzonden door de **[!UICONTROL Report]**-weergave van het pushbericht te bekijken, het bericht in de tabel **[!UICONTROL Message History]** te zoeken en naar het aantal **[!UICONTROL Published]** te kijken.

   >[!TIP]
   >
   >De pushservices garanderen niet dat er een bericht wordt verzonden. Raadpleeg de desbetreffende documentatie voor meer informatie over de betrouwbaarheid van services:
   >
   >* **APNS**:  [Kwaliteit van de dienst](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   >* **FCM**:  [Levensduur van een bericht](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)


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

   U kunt de geldigheid van een registratietoken ook controleren door `"ABC"` met het teken te vervangen.

## Waarom werkt mijn APNS cert niet?

Uw APNS-certificaat is mogelijk ongeldig vanwege de volgende redenen:

* In plaats van het productiecertificaat gebruikt u mogelijk een sandboxcertificaat.
* U gebruikt een nieuw productie-/sandboxcertificaat dat niet wordt ondersteund.
* U gebruikt `.p8` dossier in plaats van een `.p12` dossier.

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

Als een Photoshop-medewerker in dit voorbeeld een push verzendt naar de *Photoshop_iOS_app_SF*-app, ontvangen alle *Photoshop_iOS_app_SF-app*-gebruikers het pushbericht zoals verwacht. Maar als de werknemer een bericht naar de *Photoshop_iOS_app_LA*-app verzendt, omdat het VRSID Definition-segment onjuist is (`iOS` in plaats van `a.os contains "PhotoShop_iOS_app_LA"`), wordt het bericht verzonden naar **alle** iOS-gebruikers in *AllAdobe Photoshop_apps*. Hoewel het bericht nog steeds naar gebruikers van *Photoshop_iOS_app_LA* gaat, worden in het bericht ook de push-id&#39;s voor gebruikers van *Photoshop_iOS_app_SF* gevoegd op lijst van gewenste personen omdat de *Photoshop_iOS_app_SF*-app een ander certificaat heeft. Als het segment was gedefinieerd als `a.os contains "PhotoShop_iOS_app_LA"`, zou het pushbericht alleen zijn verzonden naar *Photoshop_iOS_app_LA* gebruikers.

Als deze waarde wordt doorgegeven met het *Photoshop_IOS_app_LA*-pushcertificaat, worden de push-id&#39;s voor het *Photoshop_iOS_app_SF* geretourneerd als `invalid`.

>[!CAUTION]
>
>Nadat u een pushbericht hebt gemaakt voor een toepassing die een VRS gebruikt en op **[!UICONTROL Save & Send]** klikt, verschijnt er een waarschuwing die u eraan herinnert dat elke vermelde app **must** een geldig certificaat heeft. Als elke app **not** een geldig certificaat heeft, kunnen uw publiekssegmenten voor onbepaalde tijd worden gevoegd op lijst van gewenste personen, en u zou toekomstige dupberichten aan de beïnvloede gebruikers kunnen niet kunnen verzenden. Voor meer informatie over publiekssegmenten, zie [Publiek: definieer en configureer publieksopties voor pushberichten](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).
