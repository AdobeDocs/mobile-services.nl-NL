---
description: Met deze informatie kunt u diepe en uitgestelde diepe koppelingen in uw mobiele apps bijhouden met de Adobe Mobile Android SDK.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Diepe koppelingen bijhouden
topic-fix: Developer and implementation
uuid: ebb1c08c-a246-40b3-9ac6-4606a14b4c5a
exl-id: 4f59b77d-3cac-4853-bb6b-50a403036771
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Diepkoppelingen bijhouden

Met deze informatie kunt u diepe en uitgestelde diepe koppelingen in uw mobiele apps bijhouden met de Adobe Mobile Android SDK.

## Diepkoppelingen bijhouden

1. Voeg de SDK toe aan uw project en implementeer levenscyclusmetriek.

   Zie voor meer informatie *Voeg de SDK en het Dossier Config aan uw IDEA van IntelliJ of Project toe Eclipse* in [Core-implementatie en levenscyclus](/help/android/getting-started/dev-qs.md).

1. Registreer de toepassing om URL&#39;s af te handelen.

   Zie voor meer informatie [URL&#39;s](https://developer.android.com/training/basics/intents/filters.html).
1. Activiteit doorgeven met intentie om diep te koppelen aan Adobe SDK door `collectLifecycleData`.

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

De Adobe Mobile SDK kan sleutel- en waardeparen gegevens parseren die aan elke Diep of Universele Verbinding worden toegevoegd zolang de koppeling een sleutel met de `a.deeplink.id` label en een corresponderende waarde die niet null is en door de gebruiker wordt gegenereerd. Alle sleutel- en waardeparen gegevens die aan de koppeling worden toegevoegd, worden geparseerd, gekoppeld aan een levenscyclushit en verzonden naar Adobe Analytics zolang de koppeling de koppeling bevat `a.deeplink.id` sleutel en waarde.

Daarnaast kunt u een of meer van de volgende gereserveerde toetsen (met door de gebruiker gegenereerde waarden) toevoegen aan de diepe of Universal Link:

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Deze toetsen zijn vooraf toegewezen variabelen voor rapportage in Adobe Analytics. Voor meer informatie over het in kaart brengen en verwerkingsregels, zie [Verwerkingsregels en contextgegevens](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html).

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
