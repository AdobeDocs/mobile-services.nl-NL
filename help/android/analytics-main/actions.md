---
description: Acties zijn de gebeurtenissen die in uw Android-app optreden en die u wilt meten.
solution: Experience Cloud Services,Analytics
title: Toepassingsacties bijhouden
topic-fix: Developer and implementation
uuid: fe01c1df-f6bb-4b32-b3ef-959d2c724af6
exl-id: 495a6aa8-781d-4499-ad46-e19d57cccf40
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 1%

---

# Toepassingsacties bijhouden {#track-app-actions}

Acties zijn de gebeurtenissen die in uw Android-app optreden en die u wilt meten.

Elke actie heeft één of meerdere overeenkomstige metriek die elke keer worden verhoogd de gebeurtenis voorkomt. U kunt bijvoorbeeld een `trackAction` vraag voor elk nieuw abonnement, telkens als een artikel wordt bekeken, of telkens als een niveau wordt voltooid. Handelingen worden niet automatisch bijgehouden, dus u moet `trackAction` wanneer een gebeurtenis plaatsvindt die u wilt volgen, en de actie aan een douanegebeurtenis in kaart brengen.

## Handelingen bijhouden {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie voor meer informatie *Voeg de SDK en het Dossier Config aan uw IDEA van IntelliJ of Project toe Eclipse* in [Kernimplementatie en levenscyclus](/help/android/getting-started/dev-qs.md).

1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. Wanneer de handeling die u wilt bijhouden plaatsvindt in uw app, roept u `trackAction` om een hit voor deze handeling te verzenden:

   ```java
   Analytics.trackAction("myapp.ActionName", null);
   ```

1. Selecteer uw app in de gebruikersinterface van Adobe Mobile Services en klik op **[!UICONTROL Manage App Settings]**.
1. Klikken **[!UICONTROL Manage Variables and Metrics]** en klik op de knop **[!UICONTROL Custom Metrics]** tab.

1. Wijs bijvoorbeeld de naam van de contextgegevens toe die in uw code is gedefinieerd, `myapp.ActionName`, naar een aangepaste gebeurtenis.

   ![](assets/map-event-context-data.png)

U kunt ook een eigenschap instellen om alle actiewaarden in te houden door een aangepaste eigenschap met een naam als **[!UICONTROL Custom Actions]** en de waarde instellen op `a.action`.

![](assets/map-custom-prop.png)

## Extra gegevens verzenden {#section_3EBE813E54A24F6FB669B2478B5661F9}

Naast de naam van de handeling kunt u aanvullende contextgegevens verzenden bij elke aanroep van een trackactie:

```java
HashMap<String, Object> exampleContextData = new HashMap<String, Object>(); 
exampleContextData.put("myapp.social.SocialSource", "Twitter"); 
Analytics.trackAction("myapp.SocialShare", exampleContextData);
```

De waarden van contextgegevens moeten aan douanevariabelen in de diensten van Adobe Mobile worden in kaart gebracht:

![](assets/map-variable-context-action.png)

## Actierapport {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

| Interface | Rapport |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL Action Paths]** verslag.  Geef de volgorde weer waarin acties in uw app plaatsvinden. U kunt ook op **[!UICONTROL Customize]**  op om het even welk rapport om acties te bekijken gerangschikt, trended, of in een verdelingsrapport of een filter toe te passen om acties voor een specifiek segment te bekijken. |
| Marketingrapporten en -analyses | **[!UICONTROL Custom Event]** verslag.  Nadat een handeling is toegewezen aan een aangepaste gebeurtenis, kunt u mobiele gebeurtenissen weergeven die vergelijkbaar zijn met alle andere analytische gebeurtenissen. |
| Ad-hocanalyse | **[!UICONTROL Custom Event]** verslag.  Nadat een handeling is toegewezen aan een aangepaste gebeurtenis, kunt u mobiele gebeurtenissen weergeven die vergelijkbaar zijn met alle andere analytische gebeurtenissen. |
