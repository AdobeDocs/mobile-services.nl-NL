---
description: De Adobe Target-prefetch-functie gebruikt de SDK's van Android Mobile om inhoud van de aanbieding zo weinig mogelijk op te halen door de serverreacties in cache te plaatsen.
title: Inhoud van Prefetch-aanbieding in Android
uuid: 063451b8-e191-4d58-8ed8-1723e310ad1a
exl-id: 60fd9703-972b-4c2c-bf9c-86e1f59bfba5
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 5%

---

# Inhoud van Prefetch-aanbieding in Android {#prefetch-offer-content-in-android}

De Adobe Target-prefetch-functie gebruikt de SDK&#39;s van Android Mobile om inhoud van de aanbieding zo weinig mogelijk op te halen door de serverreacties in cache te plaatsen.

>[!IMPORTANT]
>
>De functie Prefetch in de mobiele SDK&#39;s voor Android wordt niet ondersteund voor de activatietypen Auto Target, Auto Allocate en Automated Personalization in Adobe Target.

Dit proces verkort de laadtijd, voorkomt meerdere netwerkaanroepen en stelt Adobe Target in staat op de hoogte te worden gebracht van welke box de gebruiker van de mobiele app heeft bezocht. Alle inhoud zal tijdens de prefetch vraag worden teruggewonnen en in het voorgeheugen ondergebracht, en deze inhoud zal van het geheime voorgeheugen voor alle toekomstige vraag worden teruggewonnen die caching inhoud voor de gespecificeerde mbox naam bevat.

Prefetch-inhoud blijft niet behouden bij alle opstarters. De prefetch-inhoud wordt in de cache geplaatst zolang de toepassing leeft of totdat de methode `clearPrefetchCache()` wordt aangeroepen.

>[!IMPORTANT]
>
>API&#39;s voor doelprefetch zijn beschikbaar sinds SDK versie 4.14.0. Zie [Batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters) voor meer informatie over parameterbeperkingen.

In SDK versie 4.14 of hoger, indien opgegeven, wordt `environmentId` gekozen uit het `ADBMobileConfig.json`-bestand wanneer een TnT-aanroep van batchmap v2 wordt gestart. Als er in dit bestand geen `environmentId` is opgegeven, wordt er geen omgevingsparameter verzonden in de aanroep van de TNT-batch mbox en wordt de aanbieding geleverd voor de standaardomgeving.

Bijvoorbeeld:

```java
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## Methoden vóór ophalen {#section_05967F1F3A554B0FBC2C08A954554BDE}

Hier volgen de methoden die u kunt gebruiken voor prefetch in Android:

* **prefetchContent**

   Verzendt een prefetch verzoek met een serie van plaatsen naar de gevormde server van het Doel en keert de verzoekstatus in verstrekte callback terug.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void prefetchContent(
      final List<TargetPrefetchObject> targetPrefetchArray,
      final Map<String, Object> profileParameters,
      final TargetCallback<Boolean> callback)
      ```

   * Hier volgen de parameters voor deze methode:

      * **targetPrefetchArray**

         Array van `TargetPrefetchObjects` die de naam en mboxParameters bevat voor elke doellocatie die moet worden voorafgegaan.

      * **profileParameters**

         Bevat de sleutels en de waarden van profielparameters die met elke plaatsprefetch in dit verzoek moeten worden gebruikt.

      * **callback**

         Wordt aangeroepen wanneer de prefetch is voltooid. Retourneert `true` als de prefetch is gelukt en `false` als de prefetch is mislukt.

* **loadRequests**

   Voert een partijverzoek voor veelvoudige mbox plaatsen uit die in de verzoekserie worden gespecificeerd.  Elk object in de array bevat een callback-functie die wordt aangeroepen wanneer er inhoud beschikbaar is voor de opgegeven locatie van de box.

   >[!IMPORTANT]
   >
   >Als de inhoud voor de gevraagde plaatsen reeds caching is, zal het onmiddellijk in de verstrekte callback zijn teruggekeerd. Anders zal SDK een netwerkverzoek naar de servers van het Doel verzenden om de inhoud terug te winnen.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void loadRequests( final List<TargetRequestObject> requestArray,  final Map<String, Object> profileParameters)
      ```

   * Hier volgen de parameters voor deze methode:

      * **requestArray**

         Array van `TargetRequestObjects` die de naam, standaardinhoud, parameters en callback-functie per locatie bevat die moet worden opgehaald.

      * **profileParameters**

         Bevat sleutels en waarden van profielparameters die met elke plaatsprefetch in dit verzoek moeten worden gebruikt.

* **clearPrefetchCache**

   Wist de gegevens die door Doel Prefetch in de cache zijn geplaatst.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void clearPrefetchCache();
      ```

   * Er zijn geen parameters voor deze methode.

* **createTargetRequestObject**

   Maakt en retourneert een instantie van `TargetRequestObject` met de verschafte gegevens.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static TargetPrefetchObject createTargetRequestObject( 
      final String mboxName,
      final String defaultContent, 
      final Map<String, Object> mboxParams, 
      final Map<String, Object> orderParams, 
      final Map<String, Object> productParams, 
      final Target.TargetCallback<String> callback)
      ```

* **createTargetPrefetchObject**

   Creeert en keert een geval van TargetPrefetchObject met de verstrekte gegevens terug.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static TargetPrefetchObject createTargetPrefetchObject( 
      final String mboxName, 
      final Map<String, Object> mboxParams) 
      final Map<String, Object> orderParams, 
      final Map<String, Object> productParams)
      ```

## Openbare klassen {#section_A273E53F069E4327BBC8CE4910B37888}

Hier volgen de openbare klassen die pre-fetch in Android ondersteunen:

### Referentie klasse: TargetPrefetchObject

Hiermee worden de naam van de box en de parameters ingekapseld die worden gebruikt voor de voorinstelling mbox.

* **`name`**

   Naam van de locatie die vooraf wordt ingesteld.
   * **Type**: String

* `mboxParameters`

   Verzameling van sleutel-waardeparen die als `mboxParameters` voor dit `TargetPrefetchObject` verzoek in bijlage zullen zijn.
   * **Type**: Kaart`<String, Object>`

* **`orderParameters`**

   Verzameling van sleutel-waardeparen die aan huidige mbox onder de ordeknooppunt in bijlage zullen zijn.
   * **Type**: Kaart  `<String, Object>`

* **`productParameters`**

   Verzameling sleutelwaardeparen die aan huidige mbox onder de productknoop zullen worden vastgemaakt.

   * **Type**: Kaart  `<String, Object>`


### Referentie klasse: TargetRequestObject

Deze klasse kapselt de mbox naam, standaardinhoud, mbox parameters en de terugkeercallback in die voor de plaatsverzoeken van het Doel wordt gebruikt.

* **`mboxName`**

   Naam van de gevraagde locatie.

   * **Type**: String

* **`mboxParameters`**

   Verzameling van sleutel-waardeparen die als `mboxParameters` voor dit `TargetRequestObject` in bijlage zullen zijn.

   * **Type: Kaart`<String, Object>`**

* **`orderParameters`**

   Verzameling van sleutel-waardeparen die aan huidige mbox onder de ordeknooppunt in bijlage zullen zijn.

   * **Type**: Kaart  `<String, Object>`

* **`productParameters`**

   Verzameling sleutelwaardeparen die aan huidige mbox onder de productknoop zullen worden vastgemaakt.

   * **Type**: Kaart  `<String, Object>`

* **`defaultContent`**

   De waarde van het koord die in callback is teruggekeerd als SDK inhoud van de servers van het Doel niet kan terugwinnen.

   * **Type**: String

* **`callback`**

   Functieaanwijzer die wordt aangeroepen wanneer inhoud voor de opgegeven `TargetRequestObject` beschikbaar is.

   * **Type**: Target.TargetCallback`<String>`


## Codevoorbeeld {#section_BF7F49763D254371B4656E17953D520C}

Hier ziet u een voorbeeld van het vooraf instellen van inhoud met de SDK&#39;s van Android:

```java
// When your app launches, prefetch the content for a list of locations. 
// Define the list of mboxes that you want to prefetch. 
List<TargetPrefetchObject> prefetchMboxesList = new ArrayList<>(); 
  
Map<String, Object> mboxParameters1 = new HashMap<>(); 
mboxParameters1.put("status", "platinum"); 
prefetchMboxesList.add(Target.createTargetPrefetchObject("mboxName1", mboxParameters1));

Map<String, Object> mboxParameters2 = new HashMap<>(); 
mboxParameters2.put("userType", "paid"); 
 
List<String> purchasedIds = new ArrayList<String>(); 
purchasedIds.add("34"); 
purchasedIds.add("125");  
Map<String, Object> orderParameters2 = new HashMap<>(); 
orderParameters2.put("id", "ADCKKIM"); 
orderParameters2.put("total", "344.30"); 
orderParameters2.put("purchasedProductIds",  purchasedIds); 
  
Map<String, Object> productParameters2 = new HashMap<>(); 
productParameters2.put("id", "24D3412"); 
productParameters2.put("categoryId","Books"); 
  
prefetchMboxesList.add(Target.createTargetPrefetchObject("mboxName2", mboxParameters2, orderParameters2, productParameters2));

// Define the profile parameters map. 
Map<String, Object> profileParameters = new HashMap<>(); 
profileParameters.put("ageGroup", "20-32");

// Define the target callback for the prefetch call status. 
Target.TargetCallback<Boolean> prefetchStatusCallback = new Target.TargetCallback<Boolean>() { 
    @Override 
    public void call(final Boolean status) { 
        // check the returned status for the prefetch call 
    }};

// Call the prefetchContent API. 
Target.prefetchContent(prefetchMboxesList, profileParameters, prefetchStatusCallback);

// When the content is required, you can initiate the locations request. 
// Define the list of target request objects. 
List<TargetRequestObject> locationRequests = new ArrayList<>(); 
  
Target.TargetCallback<String> callback1 = new Target.TargetCallback<String>() { 
    @Override 
    public void call(final String content) { 
        // check the returned content for mboxName1. 
    }}; 
  
locationRequests.add(Target.createTargetRequestObject("mboxName1", "defaultContent1", mboxParameters1, callback1));

Target.TargetCallback<String> callback2 = new Target.TargetCallback<String>() { 
    @Override 
    public void call(final String content) { 
        // check the returned content for mboxName2. 
    }}; 
  
locationRequests.add(Target.createTargetRequestObject("mboxName2", "defaultContent2", mboxParameters2, orderParameters2, productParameters2, callback2)); 
  
// Call the loadRequests API. 
Target.loadRequests(locationRequests, profileParameters); 
```

## Aanvullende informatie {#section_A454BAD1CD49423E86C71BAEE06125FD}

Hieronder vindt u aanvullende informatie over deze voorbeelden:

* `ProductParameters` staat alleen de volgende toetsen toe:

   * `id`
   * `categoryId`

* `OrderParameters` staat alleen de volgende toetsen toe:

   * `id`
   * `total`
   * `purchasedProductIds`

* `purchasedProducts` Accepteert een ArrayList met tekenreeksen.
