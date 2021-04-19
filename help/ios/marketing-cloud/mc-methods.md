---
description: Hier volgen de methoden van de Adobe Experience Platform Identity Service die worden geleverd door de iOS-bibliotheek.
seo-description: Hier volgen de methoden van de Adobe Experience Platform Identity Service die worden geleverd door de iOS-bibliotheek.
seo-title: Methoden van Adobe Experience Platform Identity Service
solution: Experience Cloud,Analytics
title: Methoden van Adobe Experience Platform Identity Service
topic-fix: Developer and implementation
uuid: cdd307bc-8b7d-47a8-b77e-00902b9e2968
exl-id: 82a246fc-f679-4fa5-b9c0-dc909a7e7d93
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 21%

---

# Methoden van Adobe Experience Platform Identity Service {#experience-cloud-id-service-methods}

Hier volgen de methoden van de Adobe Experience Platform Identity Service die worden geleverd door de iOS-bibliotheek.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target, Audience Manager en de Experience Cloud Visitor ID-service.

Methoden worden vooraf bepaald volgens de oplossing en de methoden Experience Cloud ID worden voorafgegaan door `visitor`. Zie [De Experience Cloud-id inschakelen](/help/ios/marketing-cloud/mcvid.md) voor meer informatie.

* **`+`(nullable NSURL  `*`)bezoekerAppendToURL:(nullable NSURL  `*`)url;**

   Hiermee voegt u Adobe-bezoekersgegevens toe aan een URL-tekenreeks voor gebruik met de Adobe JavaScript-bibliotheek. Als u deze methode wilt gebruiken, moet u Mobile SDK versie 4.12 of hoger hebben. Zie [Helperfunctie voor bezoeker-id toevoegen](https://docs.adobe.com/content/help/en/id-service/using/id-service-api/methods/appendvisitorid.html) voor meer informatie.

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
      >Deze methode kan een blokkerende netwerkvraag veroorzaken en zou **not** van een draad moeten worden geroepen UI.

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

   Synchroniseert de verstrekte herkenningstekens aan de dienst van identiteitskaart Geef `authState` door als een van de volgende waarden:

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

   Hiermee synchroniseert u het opgegeven id-type en de opgegeven waarde met de id-service. Geef een van de volgende waarden door in de `authState`:

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

   Hiermee wordt een array van alleen-lezen `ADBVisitorID`-objecten opgehaald.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      +  (nullable NSArray *) visitorGetIDs;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      NSArray *myVisitorIDs = [ADBMobile visitorGetIDs];
      ```

* **bezoekorgetUrlVariablesAsync**

   Deze methode, die is geïntroduceerd in versie 4.16.0, retourneert een correct gevormde tekenreeks die URL-variabelen van de Bezoeker-id-service bevat. Voor meer informatie over hoe deze methode wordt gebruikt, zie [Methoden van de Dienst van de Identiteit van Adobe Experience Platform](/help/ios/reference/hybrid-app.md).

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
