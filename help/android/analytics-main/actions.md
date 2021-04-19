---
description: Acties zijn de gebeurtenissen die in uw Android-app optreden en die u wilt meten.
seo-description: Acties zijn de gebeurtenissen die in uw Android-app optreden en die u wilt meten.
seo-title: Toepassingsacties bijhouden
solution: Experience Cloud,Analytics
title: Toepassingsacties bijhouden
topic-fix: Developer and implementation
uuid: fe01c1df-f6bb-4b32-b3ef-959d2c724af6
exl-id: 495a6aa8-781d-4499-ad46-e19d57cccf40
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 1%

---

# Toepassingshandelingen bijhouden {#track-app-actions}

Acties zijn de gebeurtenissen die in uw Android-app optreden en die u wilt meten.

Elke actie heeft één of meerdere overeenkomstige metriek die elke keer worden verhoogd de gebeurtenis voorkomt. Bijvoorbeeld, zou u een `trackAction` vraag voor elk nieuw abonnement kunnen verzenden, telkens als een artikel wordt bekeken, of telkens als een niveau wordt voltooid. Handelingen worden niet automatisch bijgehouden, dus u moet `trackAction` aanroepen wanneer een gebeurtenis plaatsvindt die u wilt bijhouden en de handeling toewijzen aan een aangepaste gebeurtenis.

## Handelingen {#section_380DF56C4EE4432A823940E4AE4C9E91} bijhouden

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Voor meer informatie, zie *Voeg het dossier SDK en Config aan uw Project IntelliJ IDEA of Eclipse* in [de implementatie van de Kern en levenscyclus](/help/android/getting-started/dev-qs.md) toe.

1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. Wanneer de handeling die u wilt bijhouden plaatsvindt in uw app, roept u `trackAction` aan om een hit voor deze actie te verzenden:

   ```java
   Analytics.trackAction("myapp.ActionName", null);
   ```

1. Selecteer uw toepassing in de gebruikersinterface van Mobiele services Adobe en klik op **[!UICONTROL Manage App Settings]**.
1. Klik **[!UICONTROL Manage Variables and Metrics]** en klik **[!UICONTROL Custom Metrics]** tabel.

1. Wijs de naam van de contextgegevens die in uw code, bijvoorbeeld, `myapp.ActionName`, aan een douanegebeurtenis wordt bepaald.

   ![](assets/map-event-context-data.png)

U kunt ook een eigenschap instellen om alle actiewaarden in te houden door een aangepaste eigenschap met een naam als **[!UICONTROL Custom Actions]** toe te wijzen en de waarde in te stellen op `a.action`.

![](assets/map-custom-prop.png)

## Extra gegevens {#section_3EBE813E54A24F6FB669B2478B5661F9} verzenden

Naast de naam van de handeling kunt u aanvullende contextgegevens verzenden bij elke aanroep van een trackactie:

```java
HashMap<String, Object> exampleContextData = new HashMap<String, Object>(); 
exampleContextData.put("myapp.social.SocialSource", "Twitter"); 
Analytics.trackAction("myapp.SocialShare", exampleContextData);
```

De waarden van contextgegevens moeten aan douanevariabelen in de Mobiele diensten van Adobe worden in kaart gebracht:

![](assets/map-variable-context-action.png)

## Melding van handelingen {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

| Interface | Rapport |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL Action Paths]** verslag.  Geef de volgorde weer waarin acties in uw app plaatsvinden. U kunt **[!UICONTROL Customize]** op om het even welk rapport ook klikken om gerangschikte, georiënteerde acties, of in een verdelingsrapport te bekijken of een filter op meningsacties voor een specifiek segment toe te passen. |
| Marketingrapporten en -analyses | **[!UICONTROL Custom Event]** verslag.  Nadat een handeling is toegewezen aan een aangepaste gebeurtenis, kunt u mobiele gebeurtenissen weergeven die vergelijkbaar zijn met alle andere analytische gebeurtenissen. |
| Ad-hocanalyse | **[!UICONTROL Custom Event]** verslag.  Nadat een handeling is toegewezen aan een aangepaste gebeurtenis, kunt u mobiele gebeurtenissen weergeven die vergelijkbaar zijn met alle andere analytische gebeurtenissen. |
