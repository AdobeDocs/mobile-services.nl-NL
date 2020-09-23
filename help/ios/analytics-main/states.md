---
description: Frames zijn de verschillende schermen of weergaven in uw toepassing. Telkens wanneer een nieuwe staat in uw toepassing wordt getoond, bijvoorbeeld, wanneer een gebruiker van de homepage aan het nieuwsvoer navigeert, zou een vraag van de spoorstaat moeten worden verzonden. In iOS wordt een status doorgaans bijgehouden in de methode viewDoLoad van elke weergave.
seo-description: Frames zijn de verschillende schermen of weergaven in uw toepassing. Telkens wanneer een nieuwe staat in uw toepassing wordt getoond, bijvoorbeeld, wanneer een gebruiker van de homepage aan het nieuwsvoer navigeert, zou een vraag van de spoorstaat moeten worden verzonden. In iOS wordt een status doorgaans bijgehouden in de methode viewDoLoad van elke weergave.
seo-title: App-statussen bijhouden
solution: Experience Cloud,Analytics
title: App-statussen bijhouden
topic: Developer and implementation
uuid: 12cca4eb-1f15-4cec-a58f-76b69eaff99d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 2%

---


# Track app states {#track-app-states}

Frames zijn de verschillende schermen of weergaven in uw toepassing. Telkens wanneer een nieuwe staat in uw toepassing wordt getoond, bijvoorbeeld, wanneer een gebruiker van de homepage aan het nieuwsvoer navigeert, zou een vraag van de spoorstaat moeten worden verzonden. In iOS wordt een status doorgaans bijgehouden in de methode viewDoLoad van elke weergave.

>[!TIP]
>
>Om staten te volgen, doe een vraag aan `trackState`. Frames worden niet automatisch bijgehouden.

## Frames bijhouden {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie SDK en configuratiebestand *toevoegen aan uw project* in [Core-implementatie en levenscyclus](/help/ios/getting-started/dev-qs.md)voor meer informatie.
1. Importeer de bibliotheek.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Vraag `trackState` om een klap voor deze staatsmening te verzenden.

   ```objective-c
   [ADBMobile trackState:@"Login Screen"  
                    data:nil];
   ```

In de Mobiele diensten van Adobe, **[!UICONTROL State Name]** wordt het gemeld in de *`View State`* variabele, en een mening wordt geregistreerd voor elke `trackState` vraag. In andere analytische interfaces wordt **[!UICONTROL View State]** dit gerapporteerd als **[!UICONTROL Page Name]** en worden de statusweergaven gerapporteerd als paginaweergaven.

## Extra gegevens verzenden {#section_CFDB4F944496401786A145C209AB387C}

Naast het **[!UICONTROL State Name]**, kunt u extra contextgegevens met elke vraag van de spooractie verzenden:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"logged in" forKey:@"myapp.login.LoginStatus"]; 
[ADBMobile trackState:@"Home Screen" data:contextData];
```

Contextgegevenswaarden moeten worden toegewezen aan aangepaste variabelen:

![](assets/map-variable-context-state.png)

## Rapportage toepassingsstatus {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

Frames worden meestal weergegeven met behulp van een tekenrapport, zodat u kunt zien hoe gebruikers door uw app navigeren en welke statussen het meest worden weergegeven.

|  |  |
|--- |--- |
| Adobe Mobile Services | Het **[!UICONTROL View States]** verslag. Dit rapport is gebaseerd op de wegen die de gebruikers door uw toepassing hebben genomen. Een voorbeeldpad is **[!UICONTROL Home]** > **[!UICONTROL Settings]** > **[!UICONTROL Feed]**. |
| Adobe Analytics | Frames kunnen overal worden weergegeven waar pagina&#39;s kunnen worden weergegeven, zoals het **[!UICONTROL Pages]** rapport, het **[!UICONTROL Page Views]** rapport en het **[!UICONTROL Path]** rapport. |
| Ad-hocanalyse | Frames kunnen overal worden weergegeven. Pagina&#39;s kunnen worden bekeken met behulp van de **[!UICONTROL Page]** dimensie, **[!UICONTROL Page Views]** metrisch en **[!UICONTROL Path]** rapporten. |
