---
description: Acties zijn de gebeurtenissen die in uw app voorkomen en die u wilt meten. Elke actie heeft één of meerdere overeenkomstige metriek die elke keer worden verhoogd de gebeurtenis voorkomt. U kunt bijvoorbeeld een nieuw abonnement bijhouden wanneer een artikel wordt weergegeven of telkens wanneer een niveau wordt voltooid. De overeenkomstige metriek voor deze gebeurtenissen worden gevormd als abonnementen, gelezen artikelen, en voltooide niveaus.
seo-description: Acties zijn de gebeurtenissen die in uw app voorkomen en die u wilt meten. Elke actie heeft één of meerdere overeenkomstige metriek die elke keer worden verhoogd de gebeurtenis voorkomt. U kunt bijvoorbeeld een nieuw abonnement bijhouden wanneer een artikel wordt weergegeven of telkens wanneer een niveau wordt voltooid. De overeenkomstige metriek voor deze gebeurtenissen worden gevormd als abonnementen, gelezen artikelen, en voltooide niveaus.
seo-title: App-acties bijhouden
solution: Experience Cloud,Analytics
title: App-acties bijhouden
topic-fix: Developer and implementation
uuid: 62017be1-5395-4d16-bde3-4c40a2c012d4
exl-id: ff317eff-1b8e-46e1-a305-a404979447cb
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 1%

---

# Toepassingshandelingen bijhouden {#track-app-actions}

Acties zijn de gebeurtenissen die in uw app voorkomen en die u wilt meten. Elke actie heeft één of meerdere overeenkomstige metriek die elke keer worden verhoogd de gebeurtenis voorkomt. U kunt bijvoorbeeld een nieuw abonnement bijhouden wanneer een artikel wordt weergegeven of telkens wanneer een niveau wordt voltooid. De overeenkomstige metriek voor deze gebeurtenissen worden gevormd als abonnementen, gelezen artikelen, en voltooide niveaus.

Handelingen worden niet automatisch bijgehouden, dus als u een gebeurtenis wilt bijhouden, moet u `trackAction` aanroepen.

## Handelingen {#section_380DF56C4EE4432A823940E4AE4C9E91} bijhouden

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie *SDK en configuratiebestand toevoegen aan uw project* in [Core-implementatie en LiveCycle](/help/ios/getting-started/dev-qs.md) voor meer informatie.
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
   >Als de code waar u deze vraag toevoegt zou kunnen lopen terwijl app op de achtergrond is, vraag `trackActionFromBackground` in plaats van `trackAction`.

1. Selecteer uw app in de gebruikersinterface van Mobiele Adobe-services en klik op **[!UICONTROL Manage App Settings]**.

1. Klik **[!UICONTROL Manage Variables and Metrics]** en klik **[!UICONTROL Custom Metrics]** tabel.

1. Wijs de naam van de contextgegevens die in uw code, bijvoorbeeld, `a.action=myapp.ActionName`, aan een douanegebeurtenis wordt bepaald.

   ![](assets/map-event-context-data.png)

U kunt ook een eigenschap instellen om alle actiewaarden in te houden door een aangepaste eigenschap met een naam als **[!UICONTROL Custom Actions]** toe te wijzen en de waarde in te stellen op `a.action`.

![](assets/map-custom-prop.png)

## Extra gegevens {#section_3EBE813E54A24F6FB669B2478B5661F9} verzenden

Naast de naam van de handeling kunt u aanvullende contextgegevens verzenden bij elke aanroep van een trackactie:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"Twitter" forKey:@"myapp.social.SocialSource"]; 
[ADBMobile trackAction:@"myapp.SocialShare" data:contextData];
```

Contextgegevenswaarden moeten worden toegewezen aan aangepaste variabelen:

![](assets/map-variable-context-action.png)

## Achtergrondhandelingen bijhouden {#section_AC13013F207D4FBAAF27E4412034251E}

Als u een actie in code volgt die zou kunnen lopen wanneer app op de achtergrond is, roep `trackActionFromBackground` in plaats van `trackAction`. Hoewel `trackActionFromBackground` wat extra logica bevat om levenscyclusvraag te verhinderen te vuren wanneer zij zouden moeten niet, zijn de parameters het zelfde.

## Melding van handelingen {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

| Interface | Rapport |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL Action Paths]** verslag. Geef de volgorde weer waarin acties in uw app plaatsvinden. U kunt **[!UICONTROL Customize]** op om het even welk rapport ook klikken om gerangschikte, georiënteerde acties, of in een verdelingsrapport te bekijken of een filter op meningsacties voor een specifiek segment toe te passen. |
| Marketing reports and analytics | **[!UICONTROL Custom Event]** verslag.  Nadat een handeling is toegewezen aan een aangepaste gebeurtenis, kunt u mobiele gebeurtenissen weergeven die vergelijkbaar zijn met alle andere analytische gebeurtenissen. |
| Ad-hocanalyse | **[!UICONTROL Custom Event]** verslag. Nadat een handeling is toegewezen aan een aangepaste gebeurtenis, kunt u mobiele gebeurtenissen weergeven die vergelijkbaar zijn met alle andere analytische gebeurtenissen. |
