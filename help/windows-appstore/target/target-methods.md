---
description: Lijst met doelmethoden die worden geleverd door de Windows 8.1 Universal App Store-bibliotheek.
solution: Experience Cloud Services,Analytics
title: Doelmethoden
topic-fix: Developer and implementation
uuid: 8c35b31c-c70b-4dba-8759-173342a301e9
exl-id: 2db9f594-01e7-4ca8-a90e-9d12278350d0
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 34%

---

# Doelmethoden {#target-methods}

Lijst met doelmethoden die worden geleverd door de Windows 8.1 Universal App Store-bibliotheek.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target en Audience Manager. Methoden worden vooraf bepaald volgens de oplossing. Analysemethoden hebben de voorvoegsel &quot;Doel&quot;.

[Levenscycluscijfers](/help/windows-appstore/metrics.md) worden verzonden als parameters naar elke mbox lading.

>[!TIP]
>
>Wanneer u `winmd` methoden van winJS (JavaScript), wordt de eerste letter van alle methoden automatisch verlaagd.

## Referentie klasse: TargetLocationRequest

### Properties

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## Tekenreeksconstanten

Met deze informatie kunt u toetsen instellen voor aangepaste parameters.

```
static property Platform::String ^TARGET_PARAMETER_ORDER_ID { 
  Platform::String ^get() { return L"orderId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_ORDER_TOTAL { 
  Platform::String ^get() { return L"orderTotal"; } 
} 
static property Platform::String ^TARGET_PARAMETER_PRODUCT_PURCHASE_ID { 
  Platform::String ^get() { return L"productPurchasedId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_CATEGORY_ID { 
  Platform::String ^get() { return L"categoryId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_3RDPARTY_ID { 
  Platform::String ^get() { return L"mbox3rdPartyId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PAGE_VALUE { 
  Platform::String ^get() { return L"mboxPageValue"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PC { 
  Platform::String ^get() { return L"mboxPC"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_SESSION_ID { 
  Platform::String ^get() { return L"mboxSession"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_HOST { 
  Platform::String ^get() { return L"mboxHost"; } 
}
```

* **LoadRequest (winJS: loadRequest)**

   Verzenden `request` aan uw gevormde server van het Doel en keert de koordwaarde van de aanbieding terug die in een blok wordt geproduceerd `callback`.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile; 
      ADB.Target.loadRequest(heroBannerRequest).then(function(content) { 
      // do something with content returned from target server 
      });
      ```

* **CreateRequest (winJS: createRequest()**

   Hiermee maakt u een `TargetLocationRequest` met de opgegeven parameters.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile; 
      var heroBannerRequest = ADB.Target.createRequest("heroBanner", "default.png", null); 
      ```

* **CreateOrder &#x200B; ConfirmRequest (winJS: createOrder &#x200B; ConfirmRequest)**

   Hiermee maakt u een `TargetLocationRequest` met de opgegeven parameters.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId, Platform::String ^orderTotal, Platform::String ^productPurchasedId, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^parameters); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      var ADB = ADBMobile; 
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null); 
      ```

* **ClearCookies (winJS: clearCookies)**

   Wist doelcookies voor de toepassing op het huidige apparaat.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static void ClearCookies(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **GetPcId (winJS: getPcId)**

   Keert het koekje van identiteitskaart van PC voor het huidige apparaat terug.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static Platform::String ^GetPcId();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      auto pcId = ADBMobile.Target.getPcId(); 
      ```

* **GetSessionId (winJS: getSessionId)**

   Retourneert het cookie van de sessie-id voor het huidige apparaat.

   * Hier volgt de syntaxis voor deze methode:

      ```csharp
      static Platform::String ^GetSessionId(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```js
      auto sessionId = ADBMobile.Target.getSessionId(); 
      ```
