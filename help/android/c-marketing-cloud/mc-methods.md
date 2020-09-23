---
description: Hier volgen de methoden van de Experience Cloud-id die worden geleverd door de Android-bibliotheek.
keywords: android;library;mobile;sdk
seo-description: Hier volgen de methoden van de Experience Cloud-id die worden geleverd door de Android-bibliotheek.
seo-title: Methoden van Adobe Experience Platform Identity Service
solution: Experience Cloud,Analytics
title: Methoden van Adobe Experience Platform Identity Service
topic: Developer and implementation
uuid: c5107a7e-273b-4f71-8738-4c603479b24c
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 23%

---


# Adobe Experience Platform Identity Service methods{#experience-cloud-id-service-methods}

Hier volgen de methoden van de Experience Cloud-id die worden geleverd door de Android-bibliotheek.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target, Audience Manager en Adobe Experience Platform Identity Service.

Methoden worden vooraf bepaald volgens de oplossing. Experience Cloud ID-methoden hebben bijvoorbeeld de voorvoegsel `visitor`. Voor meer informatie, zie de Configuratie [van identiteitskaart van de](/help/android/c-marketing-cloud/mcvid.md)Experience Cloud.

* **public static String appendToURL(final String URL)**

   Hiermee voegt u Adobe-bezoekersgegevens toe aan een URL-tekenreeks voor gebruik met de Adobe JavaScript-bibliotheek. U moet Mobile SDK 4.12+ hebben om deze methode te gebruiken. Zie Helperfunctie voor [bezoekersidentiteitskaart toevoegen voor meer informatie](https://docs.adobe.com/content/help/en/id-service/using/id-service-api/methods/appendvisitorid.html).

   >[!IMPORTANT]
   >
   >Deze methode kan een blokkerende netwerkvraag veroorzaken. Roep dit niet op tijd-gevoelige draden.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static String appendToURL(final String URL) 
      ```

      Een vereiste URL-tekenreeks waaraan de bezoekersinformatie wordt toegevoegd.

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      String urlSample = "https://example.com";`
              String urlWithAdobeVisitorInfo = Visitor.appendToURL(urlSample);
      
              Intent(Intent.ACTION_VIEW);
              i.setData(Uri.parse(urlWithAdobeVisitorInfo));
              startActivity(i);
      ```

* **getMarketingCloudId**

   Hiermee wordt de Experience Cloud-id opgehaald van de service bezoekersidentiteitskaart.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static String getMarketingCloudId(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      String = Visitor.getMarketingCloudId();
      ```

      >[!IMPORTANT]
      >
      >Deze methode kan een het blokkeren netwerkvraag veroorzaken en zou **niet** van een draad UI moeten worden geroepen.

* **syncIdentifiers**

   Met de Experience Cloud-id kunt u aanvullende klant-id&#39;s instellen die aan elke bezoeker kunnen worden gekoppeld. De bezoeker-API accepteert meerdere klant-id&#39;s voor dezelfde bezoeker, met een id voor het klanttype om het bereik van de verschillende klant-id&#39;s te scheiden. Deze methode komt overeen met `setCustomerIDs` in de JavaScript-bibliotheek.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void syncIdentifiers(Map<String, String> identifiers); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Map<String,String> identifiers = new HashMap<String, String>();
      identifiers.put("idType", "idValue");
      Visitor.syncIdentifiers(identifiers);
      ```

* **syncIdentifier**

   Hiermee synchroniseert u het opgegeven id-type en de opgegeven waarde met de service Bezoeker-id.

   Geef de waarde door `authenticationState` als een van de volgende waarden:

   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void syncIdentifier(final String identifierType, final String identifier, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Visitor.syncIdentifier("myIdType", "valueForUser", VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT);
      ```

* **syncIdentifiers**

   Synchroniseert de verstrekte herkenningstekens aan de dienst van identiteitskaart

   Geef de waarde door `authenticationState` als een van de volgende waarden:
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void syncIdentifiers(final Map<String String> identifiers, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Map<String, String> identifiers = new HashMap<String, String>();
          identifiers.put("myIdType", "valueForUser"); Visitor.syncIdentifiers(identifiers,
      VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED); 
      ```

* **getIdentifiers**

   Hiermee wordt een lijst met alleen-lezen `ADBVisitorID` objecten opgehaald.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static List<VisitorID> getIdentifiers(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      List<VisitorID> myVisitorIDs = Visitor.getIdentifiers(); 
      ```

* **getUrlVariablesAsync**

   Deze methode, die is geïntroduceerd in versie 4.16.0, retourneert een correct gevormde tekenreeks die URL-variabelen van de Bezoeker-id-service bevat. Zie de methoden [van](/help/android/reference/hybrid-app.md)Adobe Experience Platform Identity Service voor meer informatie over hoe deze methode wordt gebruikt.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void getUrlVariablesAsync(final VisitorCallback callback);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      final String urlString = https://www.mydomain.com/index.php; 
      Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
        @Override 
        public void call(String urlVariables) { 
            final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
            ...
        } 
      });
      ```

## Openbare methoden {#section_8AC744B431A3438C9B45629CA3EA0F51}

```java
public class VisitorID { 
    public final String idOrigin; 
    public final String idType; 
    public final String id; 
    public VisitorIDAuthenticationState authenticationState; 
 
    public enum VisitorIDAuthenticationState { 
         VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN(0), 
         VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED(1), 
         VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT(2); 
    } 
}
```
