---
description: Frames zijn de verschillende schermen of weergaven in uw toepassing.
solution: Experience Cloud Services,Analytics
title: App-statussen bijhouden
topic-fix: Developer and implementation
uuid: 69c99d05-5816-4c86-97c5-d218dc26c129
exl-id: ee1ea716-ee72-4c28-92cb-26df1327f5c6
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 3%

---

# Toepassingsstaten bijhouden {#track-app-states}

Frames zijn de verschillende schermen of weergaven in uw toepassing.

Elke keer dat een nieuwe status in uw toepassing wordt weergegeven, bijvoorbeeld wanneer een gebruiker van de startpagina naar de nieuwsfeed navigeert, wordt een `trackState` de vraag wordt verzonden. In Android: `trackState` wordt doorgaans aangeroepen wanneer een nieuwe activiteit wordt geladen.

## Frames bijhouden {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Zie voor meer informatie *Voeg de SDK en het Dossier Config aan uw IDEA van IntelliJ of Project toe Eclipse* in [Kernimplementatie en levenscyclus](/help/android/getting-started/dev-qs.md).

1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. In de `onCreate` functie, aanroepen `trackState` om een hit voor deze statusweergave te verzenden:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Adobe - track when this state loads 
       Analytics.trackState("State Name", null); 
   }
   ```

De `"State Name"` wordt gerapporteerd in de `View State` variabele in de diensten van Adobe Mobile, en een mening wordt geregistreerd voor elk `trackState` vraag. In andere analytische interfaces, `View State` wordt gerapporteerd zoals `Page Name`, en `state views` wordt gerapporteerd zoals `page views`.

## Extra gegevens verzenden {#section_CFDB4F944496401786A145C209AB387C}

Naast de `"State Name"`, kunt u extra contextgegevens verzenden met elke vraag van de spooractie:

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

De waarden van contextgegevens moeten aan douanevariabelen in de diensten van Adobe Mobile worden in kaart gebracht:

![](assets/map-variable-context-state.png)

## Rapportage toepassingsstatus {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

Frames worden meestal weergegeven met behulp van een tekenrapport, waarmee u kunt zien hoe gebruikers door uw app navigeren en welke statussen het vaakst worden weergegeven.

|  |  |
|--- |--- |
| Adobe Mobile Services | De **[!UICONTROL View States]** verslag. Dit rapport is gebaseerd op de wegen die de gebruikers door uw toepassing hebben genomen. Een voorbeeldpad is  **[!UICONTROL Home]**  >  **[!UICONTROL Settings]**  > **[!UICONTROL Feed]**. |
| Adobe Analytics | Frames kunnen overal worden weergegeven waar pagina&#39;s kunnen worden weergegeven, zoals de **[!UICONTROL Pages]** het **[!UICONTROL Page Views]** en de **[!UICONTROL Path]** verslag. |
| Ad-hocanalyse | Frames kunnen overal worden weergegeven Pagina&#39;s kunnen worden weergegeven met de opdracht **[!UICONTROL Page]** dimensie, **[!UICONTROL Page Views]** metrisch, **[!UICONTROL Path]** rapporten. |
