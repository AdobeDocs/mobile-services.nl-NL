---
description: U kunt SDK van Adobe gebruiken om persoonlijk identificeerbare informatie (PII) te verzamelen en het naar een derdeeindpunt te verzenden.
seo-description: U kunt SDK van Adobe gebruiken om persoonlijk identificeerbare informatie (PII) te verzamelen en het naar een derdeeindpunt te verzenden.
seo-title: PII-postbacks
title: PII-postbacks
uuid: 8d1f1fb8-6842-478b-a164-e7f727755bd9
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---


# PII-postbacks {#pii-postbacks}

U kunt SDK van Adobe gebruiken om persoonlijk identificeerbare informatie (PII) te verzamelen en het naar een derdeeindpunt te verzenden.

Wanneer u Adobe SDK wilt gebruiken om PII te verzamelen, zou u een spoorPII vraag moeten verzenden. Hoewel het gebruiken van deze vraag inzameling van PII- gegevens toelaat, verzendt SDK niet automatisch de gegevens naar een eindpunt van Adobe. Een PII type postback moet met het aangewezen eindpunt worden gevormd.

>[!TIP]
>
>Een eindpunt dat HTTPS steunt wordt vereist om het PII postback type te gebruiken.

## PII-postbacks bijhouden {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Voor meer informatie, zie *Voeg het Dossier SDK en Config aan uw IDEA IntelliJ of Project* Eclipse in de implementatie en de levenscyclus [van de](/help/android/getting-started/dev-qs.md)Kern toe.

1. De bibliotheek importeren:

   ```java
   #import "ADBMobile.h"
   ```

1. Wanneer u klaar bent om PII vast te leggen, roep dan `trackPII` om een hit voor deze actie, gebeurtenis of weergave te verzenden:

   ```java
   Config.collectPII(new HashMap<String, Object>(){{
     put("key","value");
   }});
   ```

