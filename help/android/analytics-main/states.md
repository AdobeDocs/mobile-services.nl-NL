---
description: Frames zijn de verschillende schermen of weergaven in uw toepassing.
seo-description: Frames zijn de verschillende schermen of weergaven in uw toepassing.
seo-title: App-statussen bijhouden
solution: Marketing Cloud,Analytics
title: App-statussen bijhouden
topic: Developer and implementation
uuid: 69c99d05-5816-4c86-97c5-d218dc26c129
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Toepassingsstaten bijhouden {#track-app-states}

Frames zijn de verschillende schermen of weergaven in uw toepassing.

Telkens wanneer een nieuwe staat in uw toepassing wordt getoond, bijvoorbeeld, wanneer een gebruiker van de homepage aan de nieuwsvoer navigeert, wordt een `trackState` vraag verzonden. In Android wordt `trackState` doorgaans aangeroepen wanneer een nieuwe activiteit wordt geladen.

## Frames bijhouden {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Voor meer informatie, zie *Voeg het Dossier SDK en Config aan uw IDEA IntelliJ of Project* Eclipse in de implementatie en de levenscyclus [van de](/help/android/getting-started/dev-qs.md)Kern toe.

1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. In de `onCreate` functie, roep `trackState` om een klap voor deze staatsmening te verzenden:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Adobe - track when this state loads 
       Analytics.trackState("State Name", null); 
   }
   ```

Het `"State Name"` wordt gemeld in de `View State` variabele in de diensten van Adobe Mobile, en een mening wordt geregistreerd voor elke `trackState` vraag. In andere analytische interfaces, `View State` wordt gemeld zoals `Page Name`, en `state views` wordt gemeld zoals `page views`.

## Extra gegevens verzenden {#section_CFDB4F944496401786A145C209AB387C}

Naast het `"State Name"`, kunt u extra contextgegevens met elke vraag van de spooractie verzenden:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
    super.onCreate(savedInstanceState); 
    setContentView(R.layout.main); 
  
    // Adobe - track when this state loads 
    HashMap<String, Object> exampleContextData = new HashMap<String, Object>(); 
    exampleContextData.put("myapp.login.LoginStatus", "logged in"); 
    Analytics.trackState("Home Screen", exampleContextData); 
}
```

Contextgegevenswaarden moeten worden toegewezen aan aangepaste variabelen in Adobe Mobile-services:

![](assets/map-variable-context-state.png)

## Rapportage toepassingsstatus {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

Frames worden meestal weergegeven met behulp van een tekenrapport, waarmee u kunt zien hoe gebruikers door uw app navigeren en welke statussen het vaakst worden weergegeven.

|  |  |
|--- |--- |
| Adobe Mobile Services | Het **[!UICONTROL View States]** verslag. Dit rapport is gebaseerd op de wegen die de gebruikers door uw toepassing hebben genomen. Een voorbeeldpad is **[!UICONTROL Home]** > **[!UICONTROL Settings]** > **[!UICONTROL Feed]**. |
| Adobe Analytics | Frames kunnen overal worden weergegeven waar pagina&#39;s kunnen worden weergegeven, zoals het **[!UICONTROL Pages]** rapport, het **[!UICONTROL Page Views]** rapport en het **[!UICONTROL Path]** rapport. |
| Ad-hocanalyse | Frames kunnen overal worden weergegeven. Pagina&#39;s kunnen worden bekeken met behulp van de **[!UICONTROL Page]** dimensie, **[!UICONTROL Page Views]** metrisch en **[!UICONTROL Path]** rapporten. |


