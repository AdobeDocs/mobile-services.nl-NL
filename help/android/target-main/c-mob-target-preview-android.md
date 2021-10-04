---
description: Met Voorvertoning van doel kunt u gemakkelijk end-to-end QA voor doelactiviteiten uitvoeren en deze activiteiten op uw apparaat voorvertonen.
title: Doelvoorvertoning op Android
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
exl-id: 69103f3a-9521-4808-8ecd-7b960efca04d
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 12%

---

# Doelvoorvertoning op Android {#target-preview-on-android}

Met Voorvertoning van doel kunt u gemakkelijk end-to-end QA voor doelactiviteiten uitvoeren en deze activiteiten op uw apparaat voorvertonen.

Ga voor meer informatie over het instellen en gebruiken van Voorvertoning doel naar [Mobiele voorvertoning doel](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html) in de gebruikershandleiding van Adobe Target.

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
      Target.setPreviewRestartDeeplink("myapp://myhost"); 
      ```
