---
description: U kunt deze informatie gebruiken om diepe en uitgestelde diepe koppelingen in uw mobiele apps te volgen met de Adobe Mobile Android SDK.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud,Analytics
title: Diepe koppelingen bijhouden
topic-fix: Developer and implementation
uuid: ebb1c08c-a246-40b3-9ac6-4606a14b4c5a
exl-id: 4f59b77d-3cac-4853-bb6b-50a403036771
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Diepkoppelingen bijhouden

U kunt deze informatie gebruiken om diepe en uitgestelde diepe koppelingen in uw mobiele apps te volgen met de Adobe Mobile Android SDK.

## Diepkoppelingen bijhouden

1. Voeg de SDK toe aan uw project en implementeer levenscyclusmetriek.

   Voor meer informatie, zie *Voeg het dossier SDK en Config aan uw project IntelliJ IDEA of Eclipse* in [de Implementatie van de Kern en Levenscyclus](/help/android/getting-started/dev-qs.md) toe.

1. Registreer de toepassing om URL&#39;s af te handelen.

   Zie [URL&#39;s](https://developer.android.com/training/basics/intents/filters.html) voor meer informatie.
1. Geef Activiteit met diepe verbindingsintentie aan Adobe SDK door `collectLifecycleData` te gebruiken.

   Hier volgt een voorbeeld van de diepe koppeling naar de track:

   ```java
   public class ParseDeepLinkActivity extends Activity { 
       @Override 
       protected void onCreate(Bundle savedInstanceState) { 
           super.onCreate(savedInstanceState); 
   
           Config.collectLifecycleData(this); 
           ... 
       } 
   }
   ```

De mobiele SDK van Adobe kan sleutel en waardeparen gegevens ontleden die aan om het even welke Diep of Universele Verbinding worden toegevoegd zolang de verbinding een sleutel met het `a.deeplink.id` etiket en een overeenkomstige niet-krachteloze en user-generated waarde bevat. Alle sleutel- en waardeparen gegevens die aan de koppeling worden toegevoegd, worden geparseerd, gekoppeld aan een levenscyclushit en verzonden naar Adobe Analytics zolang de koppeling de `a.deeplink.id`-sleutel en -waarde bevat.

Daarnaast kunt u een of meer van de volgende gereserveerde toetsen (met door de gebruiker gegenereerde waarden) toevoegen aan de diepe of Universal Link:

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Deze toetsen zijn vooraf toegewezen variabelen voor rapportage in Adobe Analytics. Voor meer informatie over afbeelding en verwerkingsregels, zie [Regels en Context Data](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) verwerken.

## Uitgestelde diepe koppelingen bijhouden (voor gebruik met marketingkoppelingen)

Met een uitgestelde diepe koppeling opent de Adobe SDK een nieuwe intentie met de diepe koppeling als de intentgegevens. Dit proces wordt behandeld als externe diepe verbinding gebruikend de bovenstaande code.

## Openbare informatie dieper koppelen {#section_1815396353614DA8A63D8D92112217E7}

### Constanten

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```
