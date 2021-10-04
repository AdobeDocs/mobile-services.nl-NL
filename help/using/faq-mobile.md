---
description: Veelgestelde vragen en antwoorden voor Adobe Mobile Services en een algemene beschrijving van functies.
keywords: mobiel
solution: Experience Cloud,Analytics
title: Veelgestelde vragen
topic-fix: Metrics
uuid: 62a9241c-2ada-483a-a594-b023916cb0b6
exl-id: d7dfc36e-56f0-498a-ad50-93fee90cb6ff
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 1%

---

# Veelgestelde vragen {#frequently-asked-questions}

De volgende lijst bevat een lijst van vaak gestelde vragen voor de Mobiele Diensten van Adobe:

## Adobe Mobile SDK {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### Welke SDK-versie moet ik hebben?

Onze huidige SDK&#39;s zijn versie 4.11. Voor meer informatie, zie [Nota&#39;s van de Versie](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html).

### Waar kan ik SDKs downloaden?

SDK&#39;s voor afzonderlijke mobiele platforms kunnen worden gedownload door de sectie [Toepassingsinstellingen beheren](/help/using/c-manage-app-settings/c-manage-app-settings.md) te bezoeken.

### Hoe vorm ik SDKs?

Nadat u een nieuwe app-rapportsuite hebt gemaakt, navigeert u naar Toepassingsinstellingen beheren en configureert u alle vereiste opties op de pagina met toepassingsgegevens. Nadat u uw configuratie hebt opgeslagen, downloadt u de vereiste SDK&#39;s onder aan de pagina Toepassingsinstellingen beheren. De SDK wordt vooraf geconfigureerd met de opties die u hebt opgeslagen. U vindt deze in het bestand `ADBMobileConfig.json` in het SDK-pakket. Als u SDK-instellingen wijzigt op de pagina App Settings (Toepassingsinstellingen beheren), moet u de SDK-bestanden opnieuw downloaden of het `ADBMobileConfig.json`-bestand bijwerken met de benodigde wijzigingen.

### Steunt de Adobe Mobile SDKs IPv6 voor iOS?

De Adobe Mobile-SDK&#39;s maken gebruik van de standaard iOS- en Android-netwerkstapels. Voor iOS gebruikt de SDK NSURLSessie (iOS versies 7+) en NSURLConnection (iOS versies 7 en hoger) die volledig compatibel zijn met IPv6. De ontwikkelaars die hun eigen voorzien van een netwerkstapel hebben gebouwd of gebruikt zouden kunnen willen herzien als er andere het verlichten overwegingen zijn. Hier volgt een aantal aanvullende informatie van Apple:

*Als u een cliënt-kant app gebruikend high-level voorzien van een netwerkAPIs zoals NSURLSessie en het kader van het Netwerk CFNetwork schrijft en u verbindt door naam, zou u niets voor uw app moeten veranderen om met IPv6 adressen te werken.* Voor meer informatie zie,  [ondersteunend IPv6 DNS64/NAT64 Netwerken](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1).

## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### Wat zijn levenscyclusstatistieken?

Levenscyclusstatistieken zijn &#39;out-of-the-box&#39;-meetgegevens die automatisch worden verzameld wanneer de SDK voor het eerst wordt geïmplementeerd in uw app. Zie [Levenscyclusmetriek (Android)](/help/android/metrics.md) en [Levenscyclusmetriek (iOS)](/help/ios/metrics.md) voor meer informatie.

### Hoe kan ik verwerkingsregels problemen oplossen?

Zie [Verwerkingsregels - Tips en trucs](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html) in de documentatie van Adobe Analytics.

### Kan ik mijn analysegegevens naar meerdere rapportensuites sturen?

Ja. De SDK&#39;s bieden de mogelijkheid om gegevens naar meerdere Adobe Analytics-rapportreeksen te verzenden. Om gegevens in veelvoudige rapportreeksen te vangen door een beeldverzoek te gebruiken, plaats de veelvoudige rapportreeks IDs in het **[!UICONTROL rsids]** gebied onder **[!UICONTROL analytics]** sectie in het `ADBMobileConfig.json` dossier, die door komma&#39;s en geen ruimten wordt afgebakend. Zie [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md) voor meer informatie.

### Hoe verschillen mobiele bezoeken van lanceringen?

Een introductie wordt gemeten door de SDK wanneer een gebruiker de app voor de eerste keer opent of naar de app terugkeert nadat hij de app langer heeft verlaten dan de opgegeven time-outwaarde. De typische onderbreking is 5 minuten (300 seconden) in **[!UICONTROL lifecycleTimeout]** gebied, dat in het `ADBMobileConfig.json` dossier wordt gevestigd. Een bezoek is een serverberekening door Adobe Analytics en is gebaseerd op de eerste en laatste gegevenstreffers die door de SDK worden verzonden zonder een bezoekonderbreking te overschrijden. Doorgaans worden sessietime-outs ingesteld op 30 minuten voor een rapportsuite. Hoewel bezoeken afkomstig zijn van traditionele webanalyses, bieden deze resultaten nog steeds waardevolle inzichten in de manier waarop gebruikers uw app kunnen betreden en verlaten.

## Berichten {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### Zijn er groottebeperkingen of andere beperkingen voor pushberichten?

Pushberichten mogen maximaal 140 tekens bevatten. Er gelden geen limieten voor het aantal meldingen dat kan worden verzonden of gepland of voor het aantal meldingen dat moet worden verzonden.

### Biedt u ondersteuning voor aangepaste payloads voor pushberichten?

Ja, we zorgen voor een aangepaste pushlading die in JSON kan worden gecodeerd. Android- en iOS-payloads zijn beperkt tot respectievelijk 4 kB en 2 kB. Deze payloads worden naar de app verzonden via een pushmelding of een lokale melding. Zie [Ervaring voor meer informatie: Push Message](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### Zijn er groottebeperkingen voor in-app berichten?

Gepubliceerde en actieve in-app berichten die zijn gemaakt in Adobe Mobile Services worden gehost op een server met een 15 MB-groottebeperking per rapportsuite voor de app. Hoewel deze beperking van toepassing is op berichtinhoud en bronnen die worden gehost met Adobe, gelden er geen beperkingen voor de bronnen waarnaar het bericht in de app kan verwijzen op andere hosts of op de bronnen in de app.

### Kan ik mijn eigen HTML voor in-app berichten gebruiken?

Ja, we ondersteunen aangepaste HTML voor uw in-app-berichten. Zie [Ervaring voor meer informatie: Bericht](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md) in de app.

### Welke triggers kan ik gebruiken om pushmeldingen of in-app berichten te verzenden?

Marketers kunnen alle analysegegevens of gebeurtenissen die worden verzonden als trigger kiezen voor het weergeven van berichten in de app. In-app berichten gebruiken triggers die lokaal op het apparaat plaatsvinden. Als er meerdere triggers worden gekozen, moeten alle triggers in dezelfde hit worden uitgevoerd voordat het bericht wordt weergegeven. Zie [Ervaring voor meer informatie: Bericht](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md) in de app.

Push-berichten worden verzonden met behulp van bestaande Adobe Analytics-segmenten of aangepaste segmenten die kunnen worden gemaakt op basis van historische analysegegevens die al zijn verzameld. Zie [Ervaring voor meer informatie: Push Message](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### Waarom krijg ik een fout met de naam van de in-app, push of Marketing Link die ik heb getypt?

U kunt niet dezelfde naam voor berichten, pushberichten of markeerkoppelingen gebruiken in meerdere apps die dezelfde bovenliggende rapportsuite of VRS gebruiken. Voer een andere naam in voor uw bericht in de app, pushbericht of marketingkoppeling om dit probleem op te lossen.

## Locatie {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### Is er een grens aan hoeveel punten van belang (POI&#39;s) kan ik hebben?

Er is geen specifieke beperking, maar voor ideale prestaties en vanwege geheugenbeperkingen op het apparaat van de gebruiker raden we u aan maximaal 5000 POI&#39;s te maken of te uploaden.

## Acquisitie {#section_B37F1129CD5843E890D0E54179455357}

### Kan ik campagnes toewijzen aan activiteiten in de app?

Ja. Adobe Mobile Services kan u helpen marketingtrucs te maken die u helpen uw apps te promoten en het verkeer naar uw apps te sturen en acquisitiecampagnes aan analyses en conversies in de app te koppelen. Zie [Acquisitie](/help/using/acquisition-main/acquisition-main.md) voor meer informatie.

### Hoe kan ik koppelingen instellen om nieuwe gebruikers van apps aan te schaffen en te volgen?

U kunt marketingkoppelingen maken waarmee gebruikers toepassingen kunnen downloaden van de Apple App Store en Google Play. Met deze koppelingen kunt u succesgebeurtenissen aan de downloads toewijzen. Voor meer informatie, zie [de Bouwer van Verbindingen van de Marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).
