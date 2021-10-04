---
description: In de gebruikersinterface van Adobe Mobile Services kunt u een pushbericht plannen dat direct moet worden bezorgd, dat later moet worden geleverd, en als een terugkerende gebeurtenis. Deze gebeurtenissen kunnen dagelijks, wekelijks, of maandelijks worden gepland.
keywords: mobiel
solution: Experience Cloud,Analytics
title: Push-bericht plannen
topic-fix: Metrics
uuid: 6810e27a-016f-4286-8fe2-9972d85fa326
exl-id: 36f263a0-4aad-423e-bb78-9c532c98df19
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 0%

---

# Planning: pushberichten{#schedule-push-message}

In de gebruikersinterface van Adobe Mobile Services kunt u een pushbericht plannen dat direct moet worden bezorgd, dat later moet worden geleverd, en als een terugkerende gebeurtenis. Deze gebeurtenissen kunnen dagelijks, wekelijks, of maandelijks worden gepland.

>[!TIP]
>
>Gebruikers kunnen de planningsinstellingen voor een pushbericht op elk gewenst moment wijzigen. Als er geen van toepassing zijnde datum is om een terugkerend gepland bericht, bijvoorbeeld, een maandelijkse terugkomende baan om de 31ste dag, op 31e februari, of de 5e Dinsdag van de maand te verzenden, wordt geen bericht verzonden.

De volgende informatie onthouden:

* De juiste datum- en tijdnotatie is `hh:mm` en `mm/dd/yyyy`.

* U kunt een gepland bericht op de volgende manieren bewerken:

   * Wijzig de datum in een latere datum.
   * Wijzig het herhalingsinterval in een ander interval.

      Bijvoorbeeld, als u oorspronkelijk een bericht had dat elke dag werd verzonden, kunt u de herhaling aan wekelijkse schakelen.

## Voordat terugkerende pushberichten worden gepland

U **must** begrijpt de volgende informatie alvorens terugkomende dupberichten te plannen:

* Welke opties in de vervolgkeuzelijst **[!UICONTROL Repeat]** worden weergegeven, is afhankelijk van de datum die u hebt getypt of geselecteerd.

   Als u bijvoorbeeld `Saturday, October 7` hebt getypt, worden de volgende opties weergegeven:

   * **[!UICONTROL Never]**
   * **[!UICONTROL Every day]**
   * **[!UICONTROL Every Saturday]**
   * **[!UICONTROL Day 7 of Every Month]**
   * **[!UICONTROL 1st Saturday of Every Month]**

* Pushberichten worden gepland en verzonden op basis van Greenwich Mean Time (GMT).

   Als u bijvoorbeeld een terugkerend bericht hebt gepland dat elke zaterdag om 12:00 uur (middag) **PST** wordt verzonden, te beginnen op 7 oktober, wordt het bericht feitelijk verzonden op zaterdag om 7 uur **GMT**.
* De berichten worden verzonden verschillend afhankelijk van of u in de V.S., Europa, of Azië wordt gevestigd.

   Bijvoorbeeld, als u in San Jose, Californië wordt gevestigd, en u een bericht plant dat op ***Oktober 31*** om 17:30 **PST** moet worden verzonden, wordt het bericht eigenlijk verzonden op ***November 1*** om 12:30 am **GMT**. Als u in Tokio wordt gevestigd, en u een bericht plant dat op ***Januari 1*** om 5:30 uur moet worden verzonden, zal het op ***December 31*** om 8:30 **GMT** worden verzonden.
* Pushberichten worden een uur eerder of later verzonden, afhankelijk van het tijdstip waarop de dag licht wordt bespaard.
* Wanneer u uw rapport van de duwberichten bekijkt, wordt het bericht getoond in de lokale tijdzone van uw systeem.

   Bijvoorbeeld, als uw begintijd 12:00 pm **PST** is, hoewel het bericht om 7pm **GMT** zal worden verzonden, zal het berichtrapport de tijd tonen verzonden als 12:00 pm **PST**.

## Een terugkerend pushbericht plannen {#section_675BD754E5A04423A1751193698A978F}

1. Selecteer **[!UICONTROL Scheduled]** of **[!UICONTROL Now]** op de pagina Schema voor een nieuw pushbericht.

   Zie [Een pushbericht maken](/help/using/in-app-messaging/t-create-push-message/t-create-push-message.md) voor meer informatie.

   Als u **[!UICONTROL Now]** selecteerde, wordt het bericht geduwd onmiddellijk. Klik op **[!UICONTROL Save as Draft]** om te voorkomen dat het bericht direct wordt gepland.

   ![](assets/schedule-push-message.png)

1. Als u **[!UICONTROL Scheduled]** hebt geselecteerd, klikt u op het kalenderpictogram en selecteert of typt u een begindatum.
1. Typ een tijd. 
1. Selecteer onder **[!UICONTROL Repeat]** een van de volgende opties:

   * **[!UICONTROL Never]**
   * **[!UICONTROL Every day]**
   * **[!UICONTROL Every Tuesday]**
   * **`<Day x>`van de maand**

      De weergegeven opties veranderen afhankelijk van de dag die u hebt geselecteerd of als startdag hebt getypt.
   * **`<nth day>`van elke maand**

      De weergegeven waarde verandert afhankelijk van de datum die u hebt geselecteerd of als begindatum hebt getypt.

1. Typ in **[!UICONTROL End Repeat]** een einddatum en -tijd.
1. Klik op een van de volgende opties:

   * **[!UICONTROL Save as Draft]**

      Met deze optie slaat u het bericht op in een concept-indeling. U kunt deze optie kiezen om een onvoltooid bericht op te slaan of het bericht op te slaan zodat iemand anders het bericht kan bewerken en goedkeuren voordat het wordt geactiveerd.

      Als u **[!UICONTROL Now]** in de vorige stap selecteerde, wordt het ontwerpbericht verzonden onmiddellijk na activering. Als u een datum en tijd selecteerde om het bericht te duwen, wordt het bericht gedrukt volgens dit programma.

   * **[!UICONTROL Save & Schedule]**

      Met deze optie verstuurt u het bericht op de geplande dag en tijd.

Voer een van de volgende taken uit als u het conceptbericht later wilt uitvoeren:

* Klik **[!UICONTROL Manage Messages]**, selecteer de controledoos naast het bericht, en klik **[!UICONTROL Activate Selected]**.
* Klik **[!UICONTROL Save & Send]** om het bericht te bewaren en het te verzenden.
