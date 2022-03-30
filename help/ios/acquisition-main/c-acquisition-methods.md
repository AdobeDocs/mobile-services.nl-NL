---
description: 'De volgende overnamemethoden worden geleverd door de iOS-bibliotheek '
solution: Experience Cloud Services,Analytics
title: Verwervingsmethoden
uuid: 6f88de57-793d-4d33-9a54-f6714289fd2c
exl-id: dd2721ae-b9a6-48b9-bc92-8e12ee551929
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 18%

---

# Verwervingsmethoden {#acquisition-methods}

De volgende overnamemethoden zijn beschikbaar in de iOS-bibliotheek:

De volgende methode wordt ondersteund:

* **acquisitionCampaignStartForApp:data:**

   Hiermee kunnen ontwikkelaars een campagne voor het aanschaffen van apps starten alsof de gebruiker op een koppeling had geklikt. Dit is handig voor het maken van handmatige aanschafkoppelingen en het omleiden van de app store naar uzelf, bijvoorbeeld met een `SKStoreView`.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void)acquisitionCampaignStartForApp:(NSString *) appId data:(NSDictionary *)data; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile acquisitionCampaignStartForApp:@"0652024f-adcd-49f9-9bd7-2552a4564d2f" data:@{@"custom.key":@"value"}]; 
      ```
