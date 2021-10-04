---
description: Frames zijn de verschillende schermen of weergaven in uw toepassing. Telkens wanneer een nieuwe staat in uw toepassing wordt getoond, bijvoorbeeld, wanneer een gebruiker van de homepage aan het nieuwsvoer navigeert, zou een vraag van de spoorstaat moeten worden verzonden. In iOS wordt een status doorgaans bijgehouden in de methode viewDoLoad van elke weergave.
solution: Experience Cloud,Analytics
title: App-statussen bijhouden
topic-fix: Developer and implementation
uuid: 12cca4eb-1f15-4cec-a58f-76b69eaff99d
exl-id: 1b7d2fbb-d2df-4063-b923-e59fa3582830
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 2%

---

# Toepassingsstaten bijhouden {#track-app-states}

Frames zijn de verschillende schermen of weergaven in uw toepassing. Telkens wanneer een nieuwe staat in uw toepassing wordt getoond, bijvoorbeeld, wanneer een gebruiker van de homepage aan het nieuwsvoer navigeert, zou een vraag van de spoorstaat moeten worden verzonden. In iOS wordt een status doorgaans bijgehouden in de methode viewDoLoad van elke weergave.

>[!TIP]
>
>Om staten te volgen, doe een vraag aan `trackState`. Frames worden niet automatisch bijgehouden.

## Frames bijhouden {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie *SDK en configuratiebestand toevoegen aan uw project* in [Core-implementatie en LiveCycle](/help/ios/getting-started/dev-qs.md) voor meer informatie.
1. Importeer de bibliotheek.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Roep `trackState` aan om een hit voor deze statusweergave te verzenden.

   ```objective-c
   [ADBMobile trackState:@"Login Screen"  
                    data:nil];
   ```

In de Mobiele diensten van Adobe, wordt **[!UICONTROL State Name]** gerapporteerd in *`View State`* variabele, en een mening wordt geregistreerd voor elke `trackState` vraag. In andere analytische interfaces wordt **[!UICONTROL View State]** gerapporteerd als **[!UICONTROL Page Name]** en worden de statusweergaven gerapporteerd als paginaweergaven.

## Extra gegevens verzenden {#section_CFDB4F944496401786A145C209AB387C}

Naast **[!UICONTROL State Name]**, kunt u extra contextgegevens met elke vraag van de spooractie verzenden:

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
| Adobe Mobile Services | Het **[!UICONTROL View States]** rapport. Dit rapport is gebaseerd op de wegen die de gebruikers door uw toepassing hebben genomen. Een voorbeeldpad is **[!UICONTROL Home]** > **[!UICONTROL Settings]** > **[!UICONTROL Feed]**. |
| Adobe Analytics | Frames kunnen overal worden weergegeven waar pagina&#39;s kunnen worden weergegeven, zoals het **[!UICONTROL Pages]**-rapport, het **[!UICONTROL Page Views]**-rapport en het **[!UICONTROL Path]**-rapport. |
| Ad-hocanalyse | Staten kunnen overal worden bekeken Pagina&#39;s kunnen worden bekeken door de **[!UICONTROL Page]** dimensie, **[!UICONTROL Page Views]** metrisch, **[!UICONTROL Path]** rapporten te gebruiken. |
