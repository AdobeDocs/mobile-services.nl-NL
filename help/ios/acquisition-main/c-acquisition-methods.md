---
description: 'De volgende verwervingsmethoden worden geleverd door de iOS-bibliotheek '
solution: Experience Cloud,Analytics
title: Verwervingsmethoden
uuid: 6f88de57-793d-4d33-9a54-f6714289fd2c
exl-id: dd2721ae-b9a6-48b9-bc92-8e12ee551929
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 18%

---

# Verwervingsmethoden {#acquisition-methods}

De volgende overnamemethoden worden geleverd door de iOS-bibliotheek:

De volgende methode wordt ondersteund:

* **acquisitionCampaignStartForApp:data:**

   Hiermee kunnen ontwikkelaars een campagne voor het aanschaffen van apps starten alsof de gebruiker op een koppeling had geklikt. Dit is handig voor het maken van handmatige aanschafkoppelingen en het omleiden van de app store zelf, bijvoorbeeld met een `SKStoreView`.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void)acquisitionCampaignStartForApp:(NSString *) appId data:(NSDictionary *)data; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile acquisitionCampaignStartForApp:@"0652024f-adcd-49f9-9bd7-2552a4564d2f" data:@{@"custom.key":@"value"}]; 
      ```
