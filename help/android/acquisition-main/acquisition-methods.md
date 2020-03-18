---
description: 'De volgende overnamemethoden worden geleverd door de Android-bibliotheek '
keywords: android;library;mobile;sdk
seo-description: 'De volgende overnamemethoden worden geleverd door de Android-bibliotheek '
seo-title: Verwervingsmethoden
solution: Marketing Cloud,Analytics
title: Verwervingsmethoden
topic: Developer and implementation
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Verwervingsmethoden{#acquisition-methods}

De volgende overnamemethode wordt geleverd door de Android-bibliotheek:

* **campagneStartForApp**

   Hiermee kunnen ontwikkelaars een campagne voor het aanschaffen van apps starten alsof de gebruiker op een koppeling klikt. Dit is handig voor het maken van handmatige aanschafkoppelingen en het omleiden van de app store zelf.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void campaignStartForApp(final String appId final Map<String Object> data); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Acquisition.campaignStartForApp("0652024f-adcd-49f9-9bd7-2552a4564d2f" new 
      HashMap<String Object (){{
           put("custom.key" "value");
      }}); 
      ```
