---
description: Hier volgt een lijst met Adobe Target-methoden die worden geleverd door de Android-bibliotheek.
keywords: android;library;mobile;sdk
seo-description: Hier volgt een lijst met Adobe Target-methoden die worden geleverd door de Android-bibliotheek.
seo-title: Doelmethoden voor Android
solution: Marketing Cloud,Analytics
title: Doelmethoden voor Android
topic: Developer and implementation
uuid: 8e9808b2-ba80-4646-ba05-8e62d4fde065
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 23%

---


# Doelmethoden voor Android{#target-methods}

Hier volgt een lijst met Adobe Target-methoden die worden geleverd door de Android-bibliotheek.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target, Audience Manager en Adobe Experience Platform Identity Service. Methoden worden vooraf bepaald volgens de oplossing. Experience Cloud ID-methoden hebben bijvoorbeeld de voorvoegsel `target`.

>[!TIP]
>
>[Levenscyclusmetriek](/help/android/metrics.md) worden als parameters naar elke mbox-lading verzonden.

## Klassenverwijzing: TargetLocationRequest {#section_A8CC898922164E819EC730DC92A6742B}

**Properties:**

```java
public String name; 
public String defaultContent; 
public HashMap<String, Object> parameters;
```

**Tekenreeksconstanten**

>[!TIP]
>
>De volgende constanten zijn voor gebruiksgemak wanneer u toetsen instelt voor aangepaste parameters.

```java
public static final String TARGET_PARAMETER_ORDER_ID   = "orderId"; 
public static final String TARGET_PARAMETER_ORDER_TOTAL         = "orderTotal"; 
public static final String TARGET_PARAMETER_PRODUCT_PURCHASE_ID = "productPurchasedId"; 
public static final String TARGET_PARAMETER_CATEGORY_ID         = "categoryId"; 
public static final String TARGET_PARAMETER_MBOX_3RDPARTY_ID    = "mbox3rdPartyId"; 
public static final String TARGET_PARAMETER_MBOX_PAGE_VALUE     = "mboxPageValue"; 
public static final String TARGET_PARAMETER_MBOX_PC             = "mboxPC"; // pcId in cookie 
public static final String TARGET_PARAMETER_MBOX_SESSION_ID     = "mboxSession"; // sessionId in cookie 
public static final String TARGET_PARAMETER_MBOX_HOST           = "mboxHost";
```

>[!IMPORTANT]
>
>* Als u SDKs **vóór** versie 4.14.0 gebruikt, zie [https://developers.adobetarget.com/api/#input-parameters](https://developers.adobetarget.com/api/#input-parameters) voor parameterbeperkingen.
   >
   >
* Als u SDKs versie 4.14.0 **of later** gebruikt, zie [https://developers.adobetarget.com/api/#batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters) voor parameterbeperkingen.


* **loadRequest**

   Verzendt verzoek naar uw gevormde server van het Doel en keert de koordwaarde van de aanbieding terug die in een blokcallback wordt geproduceerd.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void loadRequest(TargetLocationRequest request, TargetCallback<String> callback);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Target.loadRequest(heroBannerRequest, new Target.TargetCallback<String>() {  @Override  public void call(String item) {   // do something with item  } });
      ```

* **loadRequest**

   Verzendt verzoek naar uw gevormde server van het Doel en keert de koordwaarde van de aanbieding terug die in een blokcallback wordt geproduceerd.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void loadRequest(final String name final String defaultContent, final Map `<String, Object>` profileParameters, 
                                     final Map `<String, Object>` orderParameters,final Map `<String Object>` mboxParameters, final TargetCallback<String> callback)
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”);
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); 
      mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters
      new TargetCallback<String>() {
          @Override
          public void call (String item) {
             Log.d(“Target Content”, item); 
          }
      });
      ```

* **loadRequest**

   Verzendt een verzoek naar uw gevormde server van het Doel en keert de koordwaarde van de aanbieding terug die in een TargetCallback wordt geproduceerd.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void loadRequest(final String name, final String defaultContent, final Map<String, Object> profileParameters, final Map<String, Object> orderParameters, final Map<String, Object> mboxParameters, final Map<String, Object> requestLocationParameters, final TargetCallback<String> callback);
      ```

   * **Retourneert:** N.v.t.

   * **Parameters:**

      Hier volgen de parameters voor deze methode:

      * **name**

         Naam van de doos/de plaats van het Doel die u wilt terugwinnen.

         * **Type:** String
      * **defaultContent**

         Waarde die in callback is teruggekeerd als de server van het Doel onbereikbaar is, of de gebruiker kwalificeert niet voor de campagne.

         * **Type:** String
      * **profileParameters**

         Waarden in dit woordenboek worden opgenomen in het object &quot;profileParameters&quot; in de aanvraag aan Doel.

         * **Type:** Kaart `<String, Object>`
      * **orderParameters**

         Waarden in dit woordenboek worden opgenomen in het object &quot;order&quot; in de aanvraag aan Target.

         * **Type:** Kaart `<String, Object>`
      * **mboxParameters**

         Waarden in dit woordenboek worden opgenomen in de aanvraag aan Target.

         * **Type:** Kaart `<String, Object>`
      * **requestLocationParameters**

         Waarden in dit woordenboek worden opgenomen in het object &quot;requestLocation&quot; in de aanvraag aan Target.

         * **Type:** Kaart `<String, Object>`
      * **callback**

         Deze methode wordt aangeroepen met de inhoud van de aanbieding van de doelserver. Als de server van het Doel onbereikbaar is of de gebruiker niet voor de campagne kwalificeert, defaultContent zal zijn teruggekeerd.

         * **Type:** TargetCallback `<String>`
   * Hier volgt een voorbeeldcode voor deze methode:

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”); 
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Map `<String, Object>` requestLocationParameters = new HashMap `<String, Object>`(); requestLocationParameters.put(“request-location-parameter-key”, “request-location-parameter-value”); 
      
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters, requestLocationParameters,new TargetCallback<String>() {
         @Override
         public void call (String item) { 
            Log.d(“Target Content”, item);
         } 
      });
      ```

      Voor meer informatie over het onderliggende Doel API, zie [Levering](https://docs.adobe.com/dev/products/target/reference/delivery.html) in de hulp van de Ontwikkelaar van het Doel.








* **createOrder &#x200B; ConfirmRequest**

   Maakt een TargetLocationRequest-object met de opgegeven parameters.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static TargetLocationRequest createOrderConfirmRequest(String name, String orderId, String orderTotal, String productPurchasedId, Map<String, Object> parameters);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      TargetLocationRequest orderConfirm = Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null);
      ```

* **createRequest**

   Maakt een TargetLocationRequest-object met de opgegeven parameters.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static TargetLocationRequest createRequest(String name, String defaultContent, Map<String, Object> parameters);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      TargetLocationRequest heroBannerRequest = Target.createRequest("heroBanner", "default.png", null);
      ```

* **clearCookies**

   Wist doelcookies uit uw app.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void clearCookies();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Target.clearCookies();
      ```

* **getPcID**

   Retourneert de pcID.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static String getPcID();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Target.getPcID();
      ```

* **getSessionID**

   Retourneert de sessie-id.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static String getSessionID();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Target.getSessionID();
      ```

* **setThirdPartyID**

   Hiermee stelt u de id van een derde in.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static String setThirdPartyID(final String thirdPartyId);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Target.setThirdPartyID(“third-party-id”);
      ```

* **getThirdPartyID**

   Retourneert de id van de derde.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static String getThirdPartyID();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      String thirdPartyId = Target.getThirdPartyID();
      ```
