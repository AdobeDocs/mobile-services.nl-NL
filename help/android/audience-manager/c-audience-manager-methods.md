---
description: Hier volgt een lijst met de methoden voor Audience Managers die worden geleverd door de Android-bibliotheek.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Methoden van Audience Manager
topic-fix: Developer and implementation
uuid: 2f6e4664-1306-41d4-9fa7-e3a99f1df4ab
exl-id: 707b40b8-e56e-4c26-8b59-87c5d71cad0c
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 27%

---

# Methoden van Audience Manager{#audience-manager-methods}

Hier volgt een lijst met de methoden voor Audience Managers die worden geleverd door de Android-bibliotheek.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen, waaronder Analytics, Target, Audience Manager en Adobe Experience Platform Identity Service. Methoden worden vooraf bepaald volgens de oplossing. Methoden van Experience Cloud ID worden bijvoorbeeld voorafgegaan door `audience manager`.

Als Audience Manager is geconfigureerd in uw JSON-bestand, wordt een signaal met levenscyclusmetriek verzonden bij een hit tijdens de levenscyclus.

* **getVisitorProfile**

   Retourneert het bezoekersprofiel dat het laatst is verkregen en retourneert, als er geen signaal is verzonden `null`. Het bezoekersprofiel is opgeslagen in `SharedPreferences` voor eenvoudige toegang bij meerdere startpagina&#39;s van uw app.

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
