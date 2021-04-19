---
description: 'De volgende overnamemethoden worden geleverd door de Android-bibliotheek '
keywords: android;bibliotheek;mobile;sdk
seo-description: 'De volgende overnamemethoden worden geleverd door de Android-bibliotheek '
seo-title: Verwervingsmethoden
solution: Experience Cloud,Analytics
title: Verwervingsmethoden
topic-fix: Developer and implementation
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
exl-id: 0ce1b8fb-fd45-45de-8f97-e297e4c6529f
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 17%

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
