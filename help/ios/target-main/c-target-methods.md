---
description: Hier volgt een lijst met Adobe Target-methoden die worden geleverd door de iOS-bibliotheek.
solution: Experience Cloud,Analytics
title: Doelmethoden voor iOS
topic-fix: Developer and implementation
uuid: 692bcda1-02ba-4902-bd65-15888adf1952
exl-id: ba03f865-970c-4b48-af35-749f05b273d8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 23%

---

# Doelmethoden voor iOS {#target-methods}

Hier volgt een lijst met Adobe Target-methoden die worden geleverd door de iOS-bibliotheek.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target, Audience Manager en Adobe Experience Platform Identity Service. Methoden worden vooraf bepaald volgens de oplossing. Doelmethoden hebben bijvoorbeeld de voorvoegsel `target`.

>[!TIP]
>
>Levenscyclusstatistieken worden als parameters naar elke lading van de box verzonden. Zie [Levenscyclusmetriek](/help/ios/metrics.md) voor meer informatie. Als u de verzoeken van het Doel binnen de `didFinishLaunching` afgevaardigde methode verzendt, voeg een `[ADBMobile trackAction:data:]` of `[ADBMobile trackState:data:]` vraag vóór de de implementatiecode van het Doel toe. Op deze manier bevatten de doelaanvragen de volledige levenscyclusgegevens.

## Klassenverwijzing: ADBTargetLocationRequest

### Properties

```objective-c
NSString *name; 
NSString *defaultContent; 
NSMutableDictionary *parameters;
```

### Tekenreeksconstanten

>[!TIP]
>
>De volgende constanten zijn voor gebruiksgemak wanneer u toetsen instelt voor aangepaste parameters.

```iOS
NSString *const ADBTargetParameterOrderId; 
NSString *const ADBTargetParameterOrderTotal; 
NSString *const ADBTargetParameterProductPurchasedId; 
NSString *const ADBTargetParameterCategoryId; 
NSString *const ADBTargetParameterMbox3rdPartyId; 
NSString *const ADBTargetParameterMboxPageValue; 
NSString *const ADBTargetParameterMboxPc; 
NSString *const ADBTargetParameterMboxSessionId; 
NSString *const ADBTargetParameterMboxHost;
```

>[!IMPORTANT]
>
>* Als u SDK&#39;s **voor** versie 4.14.0 gebruikt, zie [Invoerparameters](https://developers.adobetarget.com/api/#input-parameters) voor parameterbeperkingen.
>
>* Als u SDKs versie 4.14.0 **of na** gebruikt, zie [Parameters van de Invoerpartij](https://developers.adobetarget.com/api/#batch-input-parameters) voor parameterbeperkingen.


### Methoden

* **targetLoadRequest: &#x200B; callback**

   Verzendt verzoek naar uw gevormde server van het Doel en keert de koordwaarde van de aanbieding terug die in een blok `callback` wordt geproduceerd.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) targetLoadRequest:(ADBTargetLocationRequest *)request
                        callback:(void (^)(NSString *content))callback;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile targetLoadRequest:myRequest
                          callback:^(NSString *content) {
                            // do something with content
                          }];
      ```

* **:defaultContent::orderParameters::requestLocationParameters:targetLoadRequestWithNameProfileParametersmboxParameterscallback:**

   Verzendt een verzoek naar uw gevormde server van het Doel en keert de koordwaarde van de aanbieding terug die in een blokcallback wordt geproduceerd.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                requestLocationParameters:(nullable NSDictionary *)requestLocationParameters
                                 callback:(nullable void (^)(NSString
                                 * __nullable content))callback;
      ```

   * Retourneert: N.v.t.

   * Hier volgen de parameters voor deze methode:

      * **`name`**

         Naam van de doos/de plaats van het Doel die u wilt terugwinnen.

         * **Type**: NSString*
      * **`defaultContent`**

         Waarde die in callback is teruggekeerd als de server van het Doel onbereikbaar is, of de gebruiker kwalificeert niet voor de campagne.

         * **Type**: NSString*
      * **`profileParameters`**

         Waarden in dit woordenboek worden opgenomen in het object &quot;profileParameters&quot; in de aanvraag aan Doel.

         * **Type**: NSDictionary*
      * **`orderParameters`**

         Waarden in dit woordenboek worden opgenomen in het object &quot;order&quot; in de aanvraag aan Target.

         * **Type**: NSDictionary
      * **`mboxParameters`**

         Waarden in dit woordenboek worden opgenomen in het object &quot;mboxParameters&quot; in de aanvraag aan Doel.

         * **Type**: NSDictionary*
      * **`requestLocationParameters`**

         Waarden in dit woordenboek worden opgenomen in het object &quot;requestLocation&quot; in de aanvraag aan Target.

         **Type**: NSDictionary*

      * **`callback`**

         Deze methode wordt aangeroepen met de inhoud van de aanbieding van de doelserver. Als de server van het Doel onbereikbaar is, of de gebruiker niet voor de campagne kwalificeert, zal defaultContent zijn teruggekeerd.
      **Type**: Functie

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile targetLoadRequestWithName:@"myHeroBanner"
                            defaultContent:@"defaultHeroBanner.png"
                        profileParameters:@{@"age":@"20-29"}
                          orderParameters:nil
                           mboxParameters:@{@"customParam":@"customValue"}
                requestLocationParameters:@{@"host":@"my.hostname.com"}
                                 callback:^(NSString *content){
                                   // do something with content
                                   myImageView.image = [UIImage imageNamed:content];
                                 }];
      ```

      Voor meer informatie over het onderliggende Doel API, zie [doel API verwijzing](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-target/target-api-reference-deprecated).







* **:defaultContent::orderParameters:targetLoadRequestWithNameProfileParametersmboxParameters:callback**

   Verzendt verzoek naar uw gevormde server van het Doel en keert de koordwaarde van de aanbieding terug die in een blokcallback wordt geproduceerd.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                               callback:(nullable void (^)(NSString * __nullable content))callback;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile targetLoadRequestWithName:@"mboxName"
                            defaultContent:@"defaultContent"
                         profileParameters:{@"profile-parameter-key": @"profile-parameter-value"}
                           orderParameters:@{@"order-parameter-key": @"order-parameter-value"}
                            mboxParameters:@{@"mbox-parameter-key": @"mbox-parameter-value"}
                                   callback:^(NSString * content) {
                                           //do something with content 
                                 }
                               }];
      ```

* **targetCreateOrder &#x200B; ConfirmRequestWithName: &#x200B; orderId: &#x200B; orderTotal: &#x200B; productPurchasedId: &#x200B; parameters**

   Hiermee maakt u een `ADBTargetLocationRequest`.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateOrderConfirmRequestWithName:(NSString *)name
                                      orderId:(NSString *)orderId
                                  orderTotal:(NSString *)orderTotal
                          productPurchasedId:(NSString *)productPurchasedId
                              parameters:(NSDictionary *)parameters;
      ```

* **targetCreateRequestWithName: &#x200B; &#x200B; defaultContent: &#x200B; parameters**

   De aannemer van de gemak om een voorwerp ADBTargetLocationRequest met de bepaalde parameters tot stand te brengen.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateRequestWithName:(NSString *)name
                           defaultContent:(NSString *)defaultContent
                               parameters:(NSDictionary *)parameters;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      ADBTargetLocationRequest *myRequest =  
      [ADBMobile targetCreateRequestWithName:@"heroBanner"
                              defaultContent:@"default.png"
                                  parameters:nil];
      ```

* **targetThirdPartyID**

   Retourneert de id van de derde.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (nullable NSString *) targetThirdPartyID;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSString *thirdPartyId = [ADBMobile targetThirdPartyID];
      ```

* **targetSetThirdPartyID**

   Hiermee stelt u de id van een derde in.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) targetSetThirdPartyID:(nullable NSString *)thirdPartyID;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile targetSetThirdPartyID:@"thirdPartyID"];
      ```

* **targetClearCookies**

   Wist doelcookies uit uw app.

   >[!TIP]
   >
   >Sinds versie 4.10.0 van de SDK gebruikt Target geen cookies meer. Deze methode stelt thirdPartyID en sessionID terug.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) targetClearCookies;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile targetClearCookies];
      ```

* **targetPcID**

   Retourneert de PcID.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSString *myTargetPcID = [ADBMobile targetPcID];
      ```

* **targetSessionID**

   Retourneert de SessionID.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSString *myTargetSessionID = [ADBMobile targetSessionID];
      ```

### Voorbeeld

```objective-c
// make your request 
ADBTargetLocationRequest *myRequest =  
 [ADBMobile targetCreateRequestWithName:@"heroBanner"  
                         defaultContent:@"default.png"  
                          parameters:nil]; 
// load your request 
[ADBMobile targetLoadRequest:myRequest  
                    callback:^(NSString *content) { 
                        // do something with content 
                        heroImage.image = [UIImage imageNamed:content];
                    }];
```
