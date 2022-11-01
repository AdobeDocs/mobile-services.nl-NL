---
description: U kunt publieksopties voor pushberichten definiëren en configureren, waaronder opties voor datumbereik, Analysesegmenten en aangepaste segmenten.
keywords: mobiel
solution: Experience Cloud Services,Analytics
title: Het publiek bepaalt en vormt de Segmenten van het Publiek voor de Duw Berichten
topic-fix: Metrics
uuid: efd410e7-3b6c-4cf4-a26f-b11688adc491
exl-id: d1062a76-2e72-4649-8497-58617a7a47cb
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 0%

---

# Publiek: pushberichten{#audience-define-and-configure-audience-segments-for-push-messages}

{#eol}

U kunt publieksopties voor pushberichten definiëren en configureren, waaronder opties voor datumbereik, Analysesegmenten en aangepaste segmenten.

## Doelsegmenten definiëren {#section_7C4D2393CF7441959FE2381A02867CAC}

Wanneer een publiekssegment voor pushberichten wordt gecreeerd, zou het segment gebruikers van één of meerdere apps kunnen impliceren omdat de rapportreeksen of virtuele rapportreeksen gegevens van één of meerdere apps zouden kunnen bevatten. Voor meer informatie over virtuele rapportsuites, zie [Virtuele rapportsuites](/help/using/manage-apps/c-mob-vrs.md).

In Adobe Mobile Services kunnen marketers slechts op één app per platform drukken. Als marketers vanuit meerdere apps naar segmenten proberen te gaan die gebruikers bevatten, wordt een waarschuwing weergegeven met de mededeling dat dit kan leiden tot ernstige pushfouten en dat gebruikers mogelijk gevoegd op lijst van gewenste personen kunnen worden. Als u een fout ondervindt in de drukknop, zie *Pushfouten oplossen* in [Probleemoplossing voor pushberichten](/help/using/in-app-messaging/t-create-push-message/c-schedule-push-message.md).

Om de gegevens van de Audience Manager in uw segmentdefinitie te gebruiken, zie [Audience Analytics](https://experienceleague.adobe.com/docs/analytics/integration/audience-analytics/mc-audiences-aam.html).

>[!IMPORTANT]
>
>Als gebruikers van de app zijn gevoegd op lijst van gewenste personen, kunnen marketers **nooit** Stuur de pushberichten opnieuw naar de betrokken gebruikers.

Als u een publiekssegment selecteert dat gebruikers over veelvoudige apps bevat, zou u het volgende alarm kunnen zien:

![meerdere toepassingsnamen](assets/multiple_appname.png)

De toepassingsnaam is gebaseerd op de geparafeerde versie van de appId, die automatisch naar Adobe Analytics wordt verzonden door de SDK van Mobile Services in het dialoogvenster `<app name> <version number> (<bundle id>)` gebruiken.

>[!TIP]
>
>Het versienummer is optioneel.

Maximaal 6 cijfersets voor de versie en 5 cijfersets voor de bundle-id worden verwijderd.

Bijvoorbeeld:

* `Bea[rd]cons 1.0 (123)` wordt weergegeven zoals `Bea[rd]cons`
* `Bea[rd]cons 1.2 (1.2)` wordt weergegeven zoals `Bea[rd]cons`
* `Bea[rd]cons 1.2.3.4.5.6.7 (1111)` wordt weergegeven zoals `Bea[rd]cons .7`
* `Bea[rd]cons 1.2.3. (1.2.3.4.5.6)` wordt weergegeven zoals `Bea[rd]cons (.6)`

Als u het pushbericht naar de vermelde apps wilt blijven verzenden, selecteert u de optie **[!UICONTROL Yes, I want to proceed.]** selectievakje en klik op **[!UICONTROL Send]**.

## Best practices

Hier volgen enkele aanbevolen procedures:

* Om verwarring te voorkomen, **vermijden** virtuele-rapportsuite voor mobiele apps definiëren die gegevens van meerdere apps bevatten.
* Een unieke toepassings-id gebruiken als onderdeel van een publiekssegment **elk** tijd dat u een pushbericht wilt verzenden.
Dit zorgt ervoor dat pushmeldingen worden verzonden naar een publiekssegment dat behoort tot **alleen** één app.

### Voorbeelden

Hier volgen enkele voorbeelden om u te helpen begrijpen hoe u segmenten correct kunt definiëren:

**Do**: De Marketer biedt pushcertificaten voor de iOS- en Android-versies van één app, bijvoorbeeld voor Adobe Photoshop. De Marketer kan een pushmelding verzenden naar een gebruikerssegment dat zich uitstrekt over beide platforms.

**Niet gebruiken**: Marketers bieden pushcertificaten voor iOS en Android-versies van één app, bijvoorbeeld voor Adobe Photoshop. Als de markeerteken een segment van *alle actieve gebruikers in de laatste 30 dagen* En alleen de gebruikers van de Adobe Photoshop iOS- en Android-app ontvangen de push en alle gebruikers van de Adobe Illustrator iOS- en Android-app worden gevoegd op lijst van gewenste personen. Zie voor meer informatie *Fouten met pushberichten oplossen* in [Problemen met pushberichten oplossen](/help/using/in-app-messaging/t-create-push-message/c-troubleshooting-push-messaging.md).

## publiekssegmenten configureren {#section_A92C60885A30421B8150820EC1CCBF13}

1. Ga naar de pagina Publiek voor een nieuw duwbericht.

   Zie voor meer informatie [Een pushbericht maken](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md).

   Houd rekening met het volgende terwijl u de publieksopties configureert **belangrijk** informatie:

   * De **[!UICONTROL Estimated Opt-In Audience]** is het aantal apparaten dat overeenkomt met het Adobe Analytics-segment **en** het aantal opted-in-apparaten.

      U kunt een schatting weergeven van het aantal gebruikers in het geselecteerde segment of de geselecteerde segmenten die zich hebben aangemeld voor het ontvangen van berichten en die het pushbericht zullen ontvangen. Het totale aantal gebruikers van de app wordt weergegeven onder de schatting, ongeacht de status van de opt-in.

   * De **[!UICONTROL Total]** is het aantal apparaten dat overeenkomt met het Adobe Analytics-segment.

   * Pushberichten worden verzonden naar de apparaten die deel uitmaken van een bepaald Adobe Analytics-segment **en** die hebben gekozen voor pushberichten.

      Dit betekent dat de SDK de waarde van `True` voor Push Message Opt-In evar.

   * Hoewel het apparaat een geldig apparaattoken heeft, tenzij Adobe Analytics de markering Opted-In heeft ingesteld, wordt het bericht niet naar het apparaat geduwd.

2. Typ gegevens in de volgende velden:

   * **[!UICONTROL During The]**

      Typ het tijdkader dat voor het geschatte publiek moet worden gebruikt. Van de **[!UICONTROL During The]** Selecteer een optie in de vervolgkeuzelijst:

   * **[!UICONTROL Last]** Hiermee kunt u een relatief tijdframe selecteren (bijvoorbeeld de laatste 7 dagen, de laatste 30 dagen of de laatste 60 dagen) vanaf het moment dat het bericht volgens de planning moet worden verstuurd.

      Als u bijvoorbeeld de laatste 30 dagen selecteert en het bericht op 31 oktober plant, is het geschatte publiek het aantal gebruikers dat heeft gekozen om de 30 dagen voor 31 oktober pushberichten te ontvangen.

   * **[!UICONTROL Static Range]** Hiermee kunt u een statisch bereik selecteren door de begin- en einddatum voor het geschatte bereik van het publiek te kiezen.

      Als u in het vorige voorbeeld een datumbereik selecteert dat begint op 1 oktober en eindigt op 15 oktober, maar het bericht op 31 oktober verzendt, wordt het geschatte publiek weergegeven als het aantal gebruikers dat heeft gekozen voor het ontvangen van pushberichten in het statische datumbereik dat u hebt opgegeven (1 oktober tot 15 oktober).

   * **[!UICONTROL Analytics Segments]**

      Selecteer een bestaand Adobe Analytics-segment in de vervolgkeuzelijst. Zie voor meer informatie de [Segment builder](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-build.html) in de documentatie van Adobe Analytics.

   * **[!UICONTROL Custom Segments]**

      Selecteer een metrische waarde of variabele in de vervolgkeuzelijst (bijvoorbeeld **[!UICONTROL Days Since Last Use]** of **[!UICONTROL Point of Interest]**) en configureert u het filter naar wens. Bijvoorbeeld, richt het volgende douanesegment gebruikers die een mobiele telefoon hebben die iOS in werking stellen en in de Californische (Verenigde Staten) regio zijn.
   >[!IMPORTANT]
   >
   >In de **[!UICONTROL Create Audience]** sectie, als u klikt **[!UICONTROL And]** wordt een dialoogvenster weergegeven waarin u wordt herinnerd aan de vraag of elke app die wordt weergegeven **moet** beschikken over een geldig certificaat. Als u hebt geklikt **[!UICONTROL Or]** wordt het standaarddialoogvenster weergegeven. Ga voor meer informatie over geldige certificaten en rapportsuites naar [Virtuele rapportsuites](/help/using/manage-apps/c-mob-vrs.md).
