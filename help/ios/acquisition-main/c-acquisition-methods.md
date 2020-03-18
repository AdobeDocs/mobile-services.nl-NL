---
description: 'De volgende verwervingsmethoden worden geleverd door de iOS-bibliotheek '
seo-description: 'De volgende verwervingsmethoden worden geleverd door de iOS-bibliotheek '
seo-title: Verwervingsmethoden
solution: Marketing Cloud,Analytics
title: Verwervingsmethoden
uuid: 6f88de57-793d-4d33-9a54-f6714289fd2c
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Verwervingsmethoden {#acquisition-methods}

De volgende overnamemethoden worden geleverd door de iOS-bibliotheek:

De volgende methode wordt ondersteund:

* **acquisitionCampaignStartForApp:data:**

   Hiermee kunnen ontwikkelaars een campagne voor het aanschaffen van apps starten alsof de gebruiker op een koppeling had geklikt. Dit is handig voor het maken van handmatige aanschafkoppelingen en het omleiden van de app store zelf, bijvoorbeeld met een `SKStoreView`app.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
      + (void)acquisitionCampaignStartForApp:(NSString *) appId data:(NSDictionary *)data; 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile acquisitionCampaignStartForApp:@"0652024f-adcd-49f9-9bd7-2552a4564d2f" data:@{@"custom.key":@"value"}]; 
      ```


