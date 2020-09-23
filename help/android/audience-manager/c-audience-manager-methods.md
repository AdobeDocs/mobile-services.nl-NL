---
description: Hier volgt een lijst met de methoden voor Audience Managers die worden geleverd door de Android-bibliotheek.
keywords: android;library;mobile;sdk
seo-description: Hier volgt een lijst met de methoden voor Audience Managers die worden geleverd door de Android-bibliotheek.
seo-title: Methoden van Audience Manager
solution: Experience Cloud,Analytics
title: Methoden van Audience Manager
topic: Developer and implementation
uuid: 2f6e4664-1306-41d4-9fa7-e3a99f1df4ab
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 25%

---


# Methoden van Audience Manager{#audience-manager-methods}

Hier volgt een lijst met de methoden voor Audience Managers die worden geleverd door de Android-bibliotheek.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target, Audience Manager en Adobe Experience Platform Identity Service. Methoden worden vooraf bepaald volgens de oplossing. Experience Cloud ID-methoden hebben bijvoorbeeld de voorvoegsel `audience manager`.

Als Audience Manager is geconfigureerd in uw JSON-bestand, wordt een signaal met levenscyclusmetriek verzonden bij een hit tijdens de levenscyclus.

* **getVisitorProfile**

   Retourneert het bezoekersprofiel dat het laatst is verkregen en retourneert, als er geen signaal is verzonden, `null`. Het bezoekersprofiel wordt opgeslagen in `SharedPreferences` zodat u eenvoudig toegang hebt tot meerdere startpagina&#39;s van uw app.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static HashMap<String, Object> getVisitorProfile(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      HashMap<String, Object> visitorProfile = AudienceManager.getVisitorProfile(); 
      ```

* **getDpid**

   Retourneert de huidige DPID.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void getDpid(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      String dpid = AudienceManager.getDpid(); 
      ```

* **getDpuuid**

   Retourneert de huidige DPUUID.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void getDpuuid(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      String dpuuid = AudienceManager.getDpuuid(); 
      ```

* **setDpidAndDpuuid**

   Plaatst DPID en DPUUID, en deze waarden worden verzonden met elk signaal.

   Als de DPUUID-waarde die aan deze methode wordt doorgegeven, tekens bevat die niet URL-veilig zijn, moeten klanten de parameter coderen voordat ze deze aan de SDK doorgeven.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void setDpidAndDpuuid(String dpid, String dpuuid); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      AudienceManager.setDpidAndDpuuid("myDpid", "myDpuuid"); 
      ```

* **signaalWithData**

   Verzendt publieksbeheer een signaal met eigenschappen en krijgt de passende segmenten die in een blokcallback worden teruggekeerd.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void signalWithData(Map<String, Object> data, AudienceManagerCallback<Map<String, Object>> callback);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      HashMap Traits = new HashMap<String, Object>();
      aamTraits.put("trait", "b");
      AudienceManager.signalWithData(aamTraits, new AudienceManager.AudienceManagerCallback<Map<String, Object>> () {
        @Override
         public void call(Map<String, Object> item) { 
              // segments come back here normally found in the segs object of your json 
         }
      });
      ```
