---
description: Met Voorvertoning van doel kunt u gemakkelijk end-to-end QA voor doelactiviteiten uitvoeren en deze activiteiten op uw apparaat voorvertonen.
title: Voorvertoning doel op iOS
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
exl-id: d5695156-59cd-42c5-b9a3-d8e0ebbb89d0
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 12%

---

# Voorvertoning doel op iOS{#target-preview-on-ios}

Met Voorvertoning van doel kunt u gemakkelijk end-to-end QA voor doelactiviteiten uitvoeren en deze activiteiten op uw apparaat voorvertonen.

Zie [Mobiele voorvertoning van doel](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html) in de documentatie van Adobe Target voor meer informatie over het instellen en gebruiken van Voorvertoning van doel.

>[!IMPORTANT]
>
>Als u Voorvertoning doel wilt gebruiken, hebt u SDK versie 4.14.0 of hoger nodig.

## Methode Doelvoorbeeld

* **setPreviewRestartDeplink**

   Hiermee stelt u een toepassingsdeplink in die wordt geactiveerd wanneer voorvertoningsselecties worden toegepast in de modus Voorbeeld.

   * Hier volgt de syntaxis voor deze methode:

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@"myapp://myhost"]; 
      ```
