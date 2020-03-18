---
description: Met de Adobe Mobile Android-SDK kunt u op basis van deze informatie diepe en uitgestelde diepe koppelingen in uw mobiele apps bijhouden.
keywords: android;library;mobile;sdk
seo-description: Met de Adobe Mobile Android-SDK kunt u op basis van deze informatie diepe en uitgestelde diepe koppelingen in uw mobiele apps bijhouden.
seo-title: Diepe koppelingen bijhouden in Adobe Mobile Services
solution: Marketing Cloud,Analytics
title: Diepe koppelingen bijhouden
topic: Developer and implementation
uuid: ebb1c08c-a246-40b3-9ac6-4606a14b4c5a
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Diepkoppelingen bijhouden {#tracking-deep-links}

Met de Adobe Mobile Android-SDK kunt u op basis van deze informatie diepe en uitgestelde diepe koppelingen in uw mobiele apps bijhouden.

## Diepkoppelingen bijhouden

1. Voeg de SDK toe aan uw project en implementeer levenscyclusmetriek.

   Voor meer informatie, zie *voeg het SDK en het Dossier Config aan uw IntelliJ IDEA of het Project* van de Verduistering in de Implementatie van de [Kern en Levenscyclus](/help/android/getting-started/dev-qs.md)toe.

1. Registreer de toepassing om URL&#39;s af te handelen.

   Zie [URL&#39;s voor meer informatie](https://developer.android.com/training/basics/intents/filters.html).
1. Geef Activiteit met diepe koppelingsintentie door aan Adobe SDK door te gebruiken `collectLifecycleData`.

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

De SDK van Adobe Mobile] kan sleutel- en waardeparen gegevens parseren die aan een Diep of Universele Verbinding worden toegevoegd zolang de koppeling een sleutel met het `a.deeplink.id` label en een overeenkomstige niet-null en user-generated waarde bevat. Alle sleutel- en waardeparen met gegevens die aan de koppeling worden toegevoegd, worden geparseerd, gekoppeld aan een hit tijdens de levenscyclus en verzonden naar Adobe Analytics] zolang de koppeling de `a.deeplink.id` sleutel en waarde bevat.

Daarnaast kunt u een of meer van de volgende gereserveerde toetsen (met door de gebruiker gegenereerde waarden) toevoegen aan de diepe of Universal Link:

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Deze toetsen zijn vooraf toegewezen variabelen voor rapportage in Adobe Analytics. Voor meer informatie over afbeelding en verwerkingsregels, zie de Regels van de [Verwerking en de Gegevens](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)van de Context.

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
