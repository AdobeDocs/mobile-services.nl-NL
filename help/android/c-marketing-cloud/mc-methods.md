---
description: Hier volgen de methoden van de Experience Cloud-id die worden geleverd door de Android-bibliotheek.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Methoden van Adobe Experience Platform Identity Service
topic-fix: Developer and implementation
uuid: c5107a7e-273b-4f71-8738-4c603479b24c
exl-id: 8eb98c3f-c6ef-4593-ad3a-f566f4d4b6a2
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 24%

---

# Methoden van Adobe Experience Platform Identity Service{#experience-cloud-id-service-methods}

Hier volgen de methoden van de Experience Cloud-id die worden geleverd door de Android-bibliotheek.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target, Audience Manager en Adobe Experience Platform Identity Service.

Methoden worden vooraf bepaald volgens de oplossing. Methoden van Experience Cloud ID worden bijvoorbeeld voorafgegaan door `visitor`. Zie voor meer informatie [Configuratie van Experience Cloud-id](/help/android/c-marketing-cloud/mcvid.md).

* **public static String appendToURL(final String URL)**

   Hiermee voegt u Adobe-bezoekersgegevens toe aan een URL-tekenreeks voor gebruik met de Adobe JavaScript-bibliotheek. U moet Mobile SDK 4.12+ hebben om deze methode te kunnen gebruiken. Zie voor meer informatie [appendVisitorIDsTo](https://experienceleague.adobe.com/docs/id-service/using/id-service-api/methods/appendvisitorid.html) in de documentatie van de Adobe Experience Cloud Identity Service.

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
      >Deze methode kan een blokkerende netwerkvraag veroorzaken en zou moeten **niet** worden aangeroepen vanuit een UI-thread.

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

   Geef in `authenticationState` als een van de volgende waarden:

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

   Geef in `authenticationState` als een van de volgende waarden:
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

   Hiermee wordt een lijst met alleen-lezen opgehaald `ADBVisitorID` objecten.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static List<VisitorID> getIdentifiers(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      List<VisitorID> myVisitorIDs = Visitor.getIdentifiers(); 
      ```

* **getUrlVariablesAsync**

   Deze methode is geïntroduceerd in versie 4.16.0 en retourneert een correct gevormde tekenreeks die de URL-variabelen van de Bezoeker-id-service bevat. Voor meer informatie over hoe deze methode wordt gebruikt, zie [Methoden van Adobe Experience Platform Identity Service](/help/android/reference/hybrid-app.md).

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
