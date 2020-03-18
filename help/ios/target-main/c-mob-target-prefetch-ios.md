---
description: De Adobe Target-prefetch-functie gebruikt de iOS Mobile SDK's om inhoud van de aanbieding zo weinig mogelijk op te halen door de serverreacties in cache te plaatsen.
seo-description: De Adobe Target-prefetch-functie gebruikt de iOS Mobile SDK's om inhoud van de aanbieding zo weinig mogelijk op te halen door de serverreacties in cache te plaatsen.
seo-title: Prefetch-aanbiedingsinhoud in iOS
title: Prefetch-aanbiedingsinhoud in iOS
uuid: fef58042-65e2-4579-b8f1-d21554d2af57
translation-type: tm+mt
source-git-commit: fa7375ac8a1345d81748bcf635791c46d3943fed

---


# Prefetch-aanbiedingsinhoud in iOS {#prefetch-offer-content-in-ios}

De Adobe Target-prefetch-functie gebruikt de iOS Mobile SDK&#39;s om inhoud van de aanbieding zo weinig mogelijk op te halen door de serverreacties in cache te plaatsen.

>[!IMPORTANT]
>
>De functie Prefetch in de mobiele SDK&#39;s voor iOS wordt niet ondersteund voor de activiteitentypen Automatisch doelbewust, Automatisch toewijzen en Automatisch aanpassen aan persoonlijke instellingen in Adobe Target.

Dit proces verkort de laadtijd, voorkomt meerdere netwerkaanroepen en stelt Adobe Target in staat op de hoogte te worden gebracht van de doos die door de gebruiker van de mobiele app is bezocht. Alle inhoud zal tijdens de prefetch vraag worden teruggewonnen en in het voorgeheugen ondergebracht, en deze inhoud zal van het geheime voorgeheugen voor alle toekomstige vraag worden teruggewonnen die caching inhoud voor de gespecificeerde mbox naam bevat.

Prefetch-inhoud blijft niet behouden bij alle opstarters. De inhoud van de prefetch wordt in de cache geplaatst zolang de toepassing leeft of totdat de `clearPrefetchCache()` methode wordt aangeroepen.

>[!IMPORTANT]
>
>API&#39;s voor doelprefetch zijn beschikbaar sinds SDK versie 4.14.0. Zie [Batch-invoerparameters](https://developers.adobetarget.com/api/#batch-input-parameters)voor meer informatie over parameterbeperkingen.

In SDK versie 4.14 of hoger, indien opgegeven, `environmentId` wordt de tag uit het `ADBMobileConfig.json` bestand opgehaald wanneer een TnT-aanroep van een batchmap v2 wordt gestart. Als er geen `environmentId` is opgegeven in dit bestand, wordt er geen omgevingsparameter verzonden in de aanroep van de TNT-batch-box en wordt de aanbieding geleverd voor de standaardomgeving.

Bijvoorbeeld:

```
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## Methoden van Prefetch {#section_05967F1F3A554B0FBC2C08A954554BDE}

Hier volgen de methoden die u kunt gebruiken voor prefetch in iOS:

* **targetPrefetchContent**

   Verzendt een prefetch verzoek met een serie van plaatsen naar de gevormde server van het Doel en keert de verzoekstatus in verstrekte callback terug.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      (void) targetPrefetchContent:(nonnull NSArray*)targetPrefetchObjectArray 
                     withProfileParameters:(nullable NSDictionary*)profileParameters 
                            callback:(nullable void(^)(BOOL success))callback;
      ```

   * Hier volgen de parameters voor deze methode:

      * **`targetPrefetchArray`**

         Array van `TargetPrefetchObjects` die de naam en mboxParameters bevat voor elke doellocatie die moet worden voorafgegaan.

      * **`profileParameters`**

         Bevat de sleutels en de waarden van profielparameters die met elke plaatsprefetch in dit verzoek moeten worden gebruikt.

      * **`callback`**

         Wordt aangeroepen wanneer de prefetch is voltooid. Retourneert `true` of de prefetch is gelukt en `false` of de prefetch is mislukt.

* **targetLoadRequests**

   Voert een partijverzoek voor veelvoudige mbox plaatsen uit die in de verzoekserie worden gespecificeerd. Elk object in de array bevat een callback-functie die wordt aangeroepen wanneer er inhoud beschikbaar is voor de opgegeven locatie van de box.

   >[!IMPORTANT]
   >
   >Als de inhoud voor de gevraagde plaatsen reeds caching is, zal het onmiddellijk in de verstrekte callback zijn teruggekeerd. Anders zal SDK een netwerkverzoek naar de servers van het Doel verzenden om de inhoud terug te winnen.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      (void)targetLoadRequests:(nonnullNSArray*)requests 
               withProfileParameters:(nullableNSDictionary*)profileParameters;
      ```

   * Hier volgen de parameters voor deze methode:

      * **`requests`**

         Array van `TargetRequestObjects` die de naam, standaardinhoud, parameters en callback-functie per locatie bevat die moet worden opgehaald.

      * **`profileParameters`**

         Bevat sleutels en waarden van profielparameters die met elke plaatsprefetch in dit verzoek moeten worden gebruikt.

* **targetPrefetchClearCache**

   Wist de gegevens die door Doel Prefetch in de cache zijn geplaatst.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      (void) targetPrefetchClearCache; 
      ```

   * Er zijn geen parameters voor deze methode.

* **targetRequestObjectWithName**

   Maakt en retourneert een instantie van `TargetRequestObject` de opgegeven gegevens.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +(nullableADBTargetRequestObject*)targetRequestObjectWithName:(nonnullNSString*)name
      defaultContent:(nonnullNSString*)defaultContent
      mboxParameters:(nullableNSDictionary*)mboxParameters
      callback:(nullablevoid(^)(NSString*__nullablecontent))callback;
      ```

   * Er zijn geen parameters voor deze methode.

* **createTargetPrefetchObject**

   Maakt en retourneert een instantie van `TargetPrefetchObject` de opgegeven gegevens.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +(nullable ADBTargetPrefetchObject *) targetPrefetchObjectWithName:(nonnullNSString *)name
      mboxParameters:(nullableNSDictionary *)mboxParameters;
      ```

## Openbare klassen {#section_A273E53F069E4327BBC8CE4910B37888}

Hier volgen de openbare klassen die pre-fetch in iOS ondersteunen:

### Referentie klasse: TargetPreFetchObject

Hiermee worden de naam van de box en de parameters ingekapseld die worden gebruikt voor de voorinstelling mbox.

* **`name`**

   Naam voor de plaats/de doos u wilt terugwinnen.

   * **Type**: NSString*

* **`mboxParameters`**

   Een optioneel woordenboek dat de sleutelwaardeparen van mbox-parameters bevat.

   * **Type**: NSDictionary*

* **`orderParameters`**

   Woordenboek dat de sleutel-waardeparen van ordeparameters bevat.

   * **Type**: NSDictionary*

* **`productParameters`**

   Woordenboek dat de sleutelwaardeparen van productparameters bevat.

   * **Type**: NSDictionary*

### Referentie klasse: TargetRequestObject

Deze klasse kapselt de mbox naam, standaardinhoud, mbox parameters en de terugkeercallback in die voor de plaatsverzoeken van het Doel wordt gebruikt.

* **`name`**

   Naam van de gevraagde locatie.

   * **Type**: NSString*

* **`mboxParameters`**

   De waarde NSString die de naam voor de plaats/mbox vertegenwoordigt u wilt terugwinnen.

   * **Type**: NSString*

* **`defaultContent`**

   De standaardinhoud die zal worden teruggekeerd als de servers van het Doel onbereikbaar zijn.

   * **Type**: NSString*

* **`callback`**

   Wanneer de partij de plaatsen van het Doel verzoekt, callback zal worden aangehaald wanneer de inhoud voor deze plaats beschikbaar is.

   * **Type**: Functie

## Codevoorbeeld {#section_BF7F49763D254371B4656E17953D520C}

Hier volgt een voorbeeld van hoe u inhoud vooraf kunt instellen met behulp van de iOS SDK&#39;s:

```objective-c
/** 
 * Prefetch Content 
 */ 
  
    NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
    NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
    NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
  
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    // Creating Prefetch Objects 
    ADBTargetPrefetchObject *prefetch1 = [ADBMobile targetPrefetchObjectWithName:@"logo" mboxParameters:mboxParameters1]; 
    prefetch1.productParameters = productParameters1; 
    prefetch1.orderParameters = orderParameters1; 
  
    ADBTargetPrefetchObject *prefetch2 = [ADBMobile targetPrefetchObjectWithName:@"buttonColor" mboxParameters:mboxParameters2]; 
    prefetch2.productParameters = productParameters2; 
    prefetch2.orderParameters = orderParameters2; 

    // Creating prefetch Array 
    NSArray *prefetchArray = @[prefetch1,prefetch2]; 
  
    // Creating Profile parameters 
    NSDictionary *profileParmeters = @{@"age":@"20-32"};

    // Target API Call 
    [ADBMobile targetPrefetchContent:prefetchArray withProfileParameters:profileParmeters callback:^(BOOL isSuccess){ 
       // do something with the Boolean result 
    }];
```

Hier volgt een voorbeeld van de batch `loadRequest` met behulp van de iOS SDK&#39;s:

```objective-c
/** 
 * Batch loadRequest  
 */ 
  
   NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
   NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
   NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    ADBTargetRequestObject *request1 = [ADBMobile targetRequestObjectWithName:@"logo" defaultContent:@"BlueWhale" mboxParameters:mboxParameters1 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
  
    request1.productParameters = productParameters1; 
    request1.orderParameters = orderParameters1;

    ADBTargetRequestObject *request2 = [ADBMobile targetRequestObjectWithName:@"buttonColor" defaultContent:@"red" mboxParameters:mboxParameters2 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
    request2.productParameters = productParameters1; 
    request2.orderParameters = orderParameters1;

    // create request object array 
    NSArray *requestArray = @[request1,request2]; 
  
    // Call the API 
    [ADBMobile targetLoadRequests:requestArray withProfileParameters:profileParmeters];
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

* `purchasedProducts` accepteert een array van tekenreeksen.