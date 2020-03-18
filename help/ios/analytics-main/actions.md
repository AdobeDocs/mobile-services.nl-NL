---
description: Acties zijn de gebeurtenissen die in uw app voorkomen en die u wilt meten. Elke actie heeft één of meerdere overeenkomstige metriek die elke keer worden verhoogd de gebeurtenis voorkomt. U kunt bijvoorbeeld een nieuw abonnement bijhouden wanneer een artikel wordt weergegeven of telkens wanneer een niveau wordt voltooid. De overeenkomstige metriek voor deze gebeurtenissen worden gevormd als abonnementen, gelezen artikelen, en voltooide niveaus.
seo-description: Acties zijn de gebeurtenissen die in uw app voorkomen en die u wilt meten. Elke actie heeft één of meerdere overeenkomstige metriek die elke keer worden verhoogd de gebeurtenis voorkomt. U kunt bijvoorbeeld een nieuw abonnement bijhouden wanneer een artikel wordt weergegeven of telkens wanneer een niveau wordt voltooid. De overeenkomstige metriek voor deze gebeurtenissen worden gevormd als abonnementen, gelezen artikelen, en voltooide niveaus.
seo-title: Toepassingshandelingen bijhouden
solution: Marketing Cloud,Analytics
title: Toepassingshandelingen bijhouden
topic: Developer and implementation
uuid: 62017be1-5395-4d16-bde3-4c40a2c012d4
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Toepassingsacties bijhouden {#track-app-actions}

Acties zijn de gebeurtenissen die in uw app voorkomen en die u wilt meten. Elke actie heeft één of meerdere overeenkomstige metriek die elke keer worden verhoogd de gebeurtenis voorkomt. U kunt bijvoorbeeld een nieuw abonnement bijhouden wanneer een artikel wordt weergegeven of telkens wanneer een niveau wordt voltooid. De overeenkomstige metriek voor deze gebeurtenissen worden gevormd als abonnementen, gelezen artikelen, en voltooide niveaus.

Handelingen worden niet automatisch bijgehouden, dus als u een gebeurtenis wilt volgen, moet u een gebeurtenis aanroepen `trackAction`.

## Handelingen bijhouden {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie SDK en configuratiebestand *toevoegen aan uw project* in [Core-implementatie en levenscyclus](/help/ios/getting-started/dev-qs.md)voor meer informatie.
1. Importeer de bibliotheek.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Wanneer de handeling die u wilt bijhouden plaatsvindt in uw app, roept u `trackAction` aan om een hit voor deze actie te verzenden.

   ```objective-c
   [ADBMobile trackAction:@"myapp.ActionName"  
                     data:nil];
   ```

   >[!TIP]
   >
   >Als de code waar u deze aanroep toevoegt mogelijk wordt uitgevoerd terwijl de toepassing zich op de achtergrond bevindt, roept u deze aan `trackActionFromBackground` in plaats van `trackAction`.

1. Selecteer uw toepassing in de gebruikersinterface van Adobe Mobile-services en klik op **[!UICONTROL Manage App Settings]**.

1. Klik **[!UICONTROL Manage Variables and Metrics]** en klik op het **[!UICONTROL Custom Metrics]** tabblad.

1. Wijs bijvoorbeeld de naam van de contextgegevens die in de code is gedefinieerd, toe `a.action=myapp.ActionName`aan een aangepaste gebeurtenis.

   ![](assets/map-event-context-data.png)

U kunt ook een eigenschap instellen om alle actiewaarden in te houden door een aangepaste eigenschap met een naam als **[!UICONTROL Custom Actions]** en de waarde in te stellen op `a.action`.

![](assets/map-custom-prop.png)

## Extra gegevens verzenden {#section_3EBE813E54A24F6FB669B2478B5661F9}

Naast de naam van de handeling kunt u aanvullende contextgegevens verzenden bij elke aanroep van een trackactie:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"Twitter" forKey:@"myapp.social.SocialSource"]; 
[ADBMobile trackAction:@"myapp.SocialShare" data:contextData];
```

Contextgegevenswaarden moeten worden toegewezen aan aangepaste variabelen:

![](assets/map-variable-context-action.png)

## Achtergrondhandelingen bijhouden {#section_AC13013F207D4FBAAF27E4412034251E}

Als u een handeling bijhoudt in code die kan worden uitgevoerd wanneer de toepassing op de achtergrond wordt uitgevoerd, roept u deze aan `trackActionFromBackground` in plaats van `trackAction`. Hoewel `trackActionFromBackground` enkele aanvullende logica bevat om te voorkomen dat levenscyclusaanroepen worden afgevuurd wanneer dat niet het geval is, zijn de parameters hetzelfde.

## Actierapport {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

| Interface | Rapport |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL Action Paths]** verslag. Geef de volgorde weer waarin acties in uw app plaatsvinden. U kunt ook op elk rapport klikken **[!UICONTROL Customize]** om gerangschikte, beheerde acties of een defecatierapport weer te geven of een filter toepassen om acties voor een bepaald segment weer te geven. |
| Marketingrapporten en analyses | **[!UICONTROL Custom Event]** verslag.  Nadat een handeling is toegewezen aan een aangepaste gebeurtenis, kunt u mobiele gebeurtenissen weergeven die vergelijkbaar zijn met alle andere analytische gebeurtenissen. |
| Ad-hocanalyse | **[!UICONTROL Custom Event]** verslag. Nadat een handeling is toegewezen aan een aangepaste gebeurtenis, kunt u mobiele gebeurtenissen weergeven die vergelijkbaar zijn met alle andere analytische gebeurtenissen. |