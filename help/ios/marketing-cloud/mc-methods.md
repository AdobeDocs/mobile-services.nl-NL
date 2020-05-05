---
description: Hier volgen de methoden van de Adobe Experience Platform Identity Service die worden geleverd door de iOS-bibliotheek.
seo-description: Hier volgen de methoden van de Adobe Experience Platform Identity Service die worden geleverd door de iOS-bibliotheek.
seo-title: Methoden van Adobe Experience Platform Identity Service
solution: Marketing Cloud,Analytics
title: Methoden van Adobe Experience Platform Identity Service
topic: Developer and implementation
uuid: cdd307bc-8b7d-47a8-b77e-00902b9e2968
translation-type: tm+mt
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa

---


# Methoden van Adobe Experience Platform Identity Service {#experience-cloud-id-service-methods}

Hier volgen de methoden van de Adobe Experience Platform Identity Service die worden geleverd door de iOS-bibliotheek.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target, Audience Manager en Experience Cloud Visitor ID-service.

Methoden worden vooraf ingesteld op basis van de oplossing en methoden van Experience Cloud ID worden vooraf ingesteld op `visitor`. Zie [De Cloud-id](/help/ios/marketing-cloud/mcvid.md)voor ervaring inschakelen voor meer informatie.

* **`+`(nullable NSURL`*`)bezoekerAppendToURL:(nullable NSURL`*`)url;**

   Hiermee voegt u gegevens van Adobe-bezoekers toe aan een URL-tekenreeks voor gebruik met de Adobe JavaScript-bibliotheek. Als u deze methode wilt gebruiken, moet u Mobile SDK versie 4.12 of hoger hebben. Zie Helperfunctie voor [bezoekersidentiteitskaart toevoegen voor meer informatie](https://docs.adobe.com/content/help/en/id-service/using/id-service-api/methods/appendvisitorid.html).

   >[!IMPORTANT]
   >
   >Deze methode kan een blokkerende netwerkvraag veroorzaken. Roep dit niet op tijd-gevoelige draden.

   * Invoer: `URL<NSURL>`
Een vereiste URL-tekenreeks waaraan de bezoekersinformatie wordt toegevoegd.
   * `URL<NSURL>`
Tekenreeks met bezoekersinfo toegevoegd.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
       NSURL *url = [NSURL URLWithString:@"https://www.example.com"];  
       NSURL *decoratedURL = [ADBMobile visitorAppendToURL: url];  
       [[UIApplication sharedApplication] openURL: decoratedURL];  
      ```

* **bezoekerMarketingCloudID**

   Haalt de Experience Cloud ID op van de ID-service.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (NSString  *)  visitorMarketingCloudID;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSString *mcid = [ADBMobile visitorMarketingCloudID]; 
      ```

      >[!IMPORTANT]
      >
      >Deze methode kan een het blokkeren netwerkvraag veroorzaken en zou **niet** van een draad UI moeten worden geroepen.

* **bezoekerSyncIdentifiers:**

   Met de Experience Cloud-id kunt u aanvullende klant-id&#39;s instellen die aan elke bezoeker kunnen worden gekoppeld. De bezoeker-API accepteert meerdere Customer ID&#39;s voor dezelfde bezoeker, met een id voor het klanttype om het bereik van de verschillende klant-id&#39;s te scheiden. Deze methode komt overeen met `setCustomerIDs` in de JavaScript-bibliotheek.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +  (void)  visitorSyncIdentifiers:(NSDictionary  *)identifiers;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"idType":@"idValue"}];
      ```

* **bezoekerSyncIdentifiers:authenticationState:**

   Synchroniseert de verstrekte herkenningstekens aan de dienst van identiteitskaart Geef de waarde door `authState` als een van de volgende waarden:

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +  (void) visitorSyncIdentifiers:(nullable NSDictionary  *)identifiers  authenticationState:(ADBMobileVisitorAuthenticationState)authState; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"myIdType":@"valueForUser"}  authenticationState:ADBMobileVisitorAuthenticationStateAuthenticated]; 
      ```

* **bezoekerSyncIdentifierWithType:identifier:authenticationState:**

   Hiermee synchroniseert u het opgegeven id-type en de opgegeven waarde met de id-service. Geef een van de `authState` volgende waarden door:

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void) visitorSyncIdentifierWithType:(nullable NSString *)identifierType  
      identifier:(nullable NSString *)identifier authenticationState:
      (ADBMobileVisitorAuthenticationState)authState; 
      ```

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      [ADBMobile visitorSyncIdentifierWithType:@"myIdType" identifier:@"valueForUser"  
      authenticationState:ADBMobileVisitorAuthenticationStateLoggedOut]; 
      ```

* **bezoekerGetIDs**

   Hiermee wordt een array van alleen-lezen `ADBVisitorID` objecten opgehaald.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +  (nullable NSArray *) visitorGetIDs;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSArray *myVisitorIDs = [ADBMobile visitorGetIDs];
      ```

* **bezoekorgetUrlVariablesAsync**

   Deze methode, die is geïntroduceerd in versie 4.16.0, retourneert een correct gevormde tekenreeks die URL-variabelen van de Bezoeker-id-service bevat. Zie de methoden [van](/help/ios/reference/hybrid-app.md)Adobe Experience Platform Identity Service voor meer informatie over hoe deze methode wordt gebruikt.

   * Hier volgt de syntaxis voor deze methode:

      ```objectivec
      + (void) visitorGetUrlVariablesAsync:(nullable void (^)(NSString* __nullable urlVariables))callback;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objectivec
      NSString *urlString = @"https://www.mydomain.com/index.php"; 
      [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
        NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
        // use urlStringWithVisitorData 
      }];
      ```

## ADBVisitorID-interface {#section_2FF74454D25C4ADABAC5E43CBFAAEC26}

**Openbare methoden:**

```objective-c
- (nullable NSString *) idType; 
- (nullable NSString *) identifier; 
- (ADBMobileVisitorAuthenticationState) authenticationState; 
```

## ADBMobileVisitorAuthenticationState enum {#section_A55A3F336DDF4F838900632087F51430}

```objective-c
ADBMobileVisitorAuthenticationStateUnknown, 
ADBMobileVisitorAuthenticationStateAuthenticated, 
ADBMobileVisitorAuthenticationStateLoggedOut
```

