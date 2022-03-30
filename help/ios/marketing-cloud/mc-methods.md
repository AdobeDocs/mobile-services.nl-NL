---
description: Hier volgen de methoden van Adobe Experience Platform Identity Service die worden geleverd door de iOS-bibliotheek.
solution: Experience Cloud Services,Analytics
title: Methoden van Adobe Experience Platform Identity Service
topic-fix: Developer and implementation
uuid: cdd307bc-8b7d-47a8-b77e-00902b9e2968
exl-id: 82a246fc-f679-4fa5-b9c0-dc909a7e7d93
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 22%

---

# Methoden van Adobe Experience Platform Identity Service {#experience-cloud-id-service-methods}

Hier volgen de methoden van Adobe Experience Platform Identity Service die worden geleverd door de iOS-bibliotheek.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target, Audience Manager en de Experience Cloud Visitor ID-service.

Methoden worden vooraf bepaald op basis van de oplossing en de Experience Cloud ID-methoden worden vooraf bepaald `visitor`. Zie voor meer informatie [De Experience Cloud-id inschakelen](/help/ios/marketing-cloud/mcvid.md).

* **`+`(nullable NSURL `*`.bezoekorAppendToURL:(nullable NSURL `*`url;**

   Hiermee voegt u Adobe-bezoekersgegevens toe aan een URL-tekenreeks voor gebruik met de Adobe JavaScript-bibliotheek. Als u deze methode wilt gebruiken, moet u Mobile SDK versie 4.12 of hoger hebben. Zie voor meer informatie [appendVisitorIDsTo](https://experienceleague.adobe.com/docs/id-service/using/id-service-api/methods/appendvisitorid.html) in de documentatie van de Adobe Experience Cloud Identity Service.

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

   Haalt de Experience Cloud-id op van de id-service.

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
      >Deze methode kan een blokkerende netwerkvraag veroorzaken en zou moeten **niet** worden aangeroepen vanuit een UI-thread.

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

   Synchroniseert de verstrekte herkenningstekens aan de dienst van identiteitskaart Geef in `authState` als een van de volgende waarden:

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

   Hiermee synchroniseert u het opgegeven id-type en de opgegeven waarde met de id-service. Geef in `authState` een van de volgende waarden:

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

   Hiermee wordt een array met alleen-lezen opgehaald `ADBVisitorID` objecten.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +  (nullable NSArray *) visitorGetIDs;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSArray *myVisitorIDs = [ADBMobile visitorGetIDs];
      ```

* **bezoekorgetUrlVariablesAsync**

   Deze methode is geïntroduceerd in versie 4.16.0 en retourneert een correct gevormde tekenreeks die de URL-variabelen van de Bezoeker-id-service bevat. Voor meer informatie over hoe deze methode wordt gebruikt, zie [Methoden van Adobe Experience Platform Identity Service](/help/ios/reference/hybrid-app.md).

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
