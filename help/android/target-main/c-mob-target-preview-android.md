---
description: Met Voorvertoning van doel kunt u gemakkelijk end-to-end QA voor doelactiviteiten uitvoeren en deze activiteiten op uw apparaat voorvertonen.
seo-description: Met Voorvertoning van doel kunt u gemakkelijk end-to-end QA voor doelactiviteiten uitvoeren en deze activiteiten op uw apparaat voorvertonen.
seo-title: Doelvoorvertoning op Android
title: Doelvoorvertoning op Android
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 10%

---


# Doelvoorvertoning op Android {#target-preview-on-android}

Met Voorvertoning van doel kunt u gemakkelijk end-to-end QA voor doelactiviteiten uitvoeren en deze activiteiten op uw apparaat voorvertonen.

Ga voor meer informatie over het instellen en gebruiken van Voorvertoning doel naar [Voorvertoning](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/target-mobile-preview.html)mobiele telefoon van doel.

>[!IMPORTANT]
>
>Als u Voorvertoning doel wilt gebruiken, hebt u SDK versie 4.14.0 of hoger nodig.

* **setPreviewRestartDeplink**

   Hiermee stelt u een toepassingsdeplink in die wordt geactiveerd wanneer voorvertoningsselecties worden toegepast in de modus Voorbeeld.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void setPreviewRestartDeeplink(String deeplink);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Target.setPreviewRestartDeeplink(“myapp://myhost”); 
      ```

