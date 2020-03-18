---
description: Met Voorvertoning van doel kunt u gemakkelijk end-to-end QA voor doelactiviteiten uitvoeren en deze activiteiten op uw apparaat voorvertonen.
seo-description: Met Voorvertoning van doel kunt u gemakkelijk end-to-end QA voor doelactiviteiten uitvoeren en deze activiteiten op uw apparaat voorvertonen.
seo-title: Voorvertoning doel op iOS
title: Voorvertoning doel op iOS
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Voorvertoning doel op iOS{#target-preview-on-ios}

Met Voorvertoning van doel kunt u gemakkelijk end-to-end QA voor doelactiviteiten uitvoeren en deze activiteiten op uw apparaat voorvertonen.

Zie [Doel mobiele voorvertoning](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/target-mobile-preview.html)voor meer informatie over het instellen en gebruiken van Voorvertoning doel.

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
      [ADBMobile targetPreviewRestartDeepLink:@" myapp://myhost"]; 
      ```
