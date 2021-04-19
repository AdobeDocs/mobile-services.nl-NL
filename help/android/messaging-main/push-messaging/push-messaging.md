---
description: Met Adobe Mobile en de SDK van Adobe Mobile kunt u pushberichten verzenden naar uw gebruikers. Met de SDK kunt u ook eenvoudig gebruikers melden die uw app hebben geopend nadat u via een pushbericht hebt geklikt.
seo-description: Met Adobe Mobile en de SDK van Adobe Mobile kunt u pushberichten verzenden naar uw gebruikers. Met de SDK kunt u ook eenvoudig gebruikers melden die uw app hebben geopend nadat u via een pushbericht hebt geklikt.
seo-title: Push Messaging
solution: Experience Cloud,Analytics
title: Push Messaging
topic-fix: Developer and implementation
uuid: 729d4010-3733-4dff-b188-ad45bd3e7cc4
exl-id: 4472e0b9-1d00-4e1a-8653-f3976b74c078
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 8%

---

# Push messaging {#push-messaging}

Met Adobe Mobile en de SDK van Adobe Mobile kunt u pushberichten verzenden naar uw gebruikers. Met de SDK kunt u ook eenvoudig gebruikers melden die uw app hebben geopend nadat u via een pushbericht hebt geklikt.

Als u pushberichten wilt gebruiken, hebt u **must** SDK versie 4.6 of hoger.

>[!IMPORTANT]
>
>Stel de Experience Cloud-id niet handmatig in in uw app. Hierdoor wordt een nieuwe unieke gebruiker gemaakt die geen pushberichten zal ontvangen vanwege de status van deze gebruiker. Een gebruiker heeft er bijvoorbeeld voor gekozen pushberichten te ontvangen die zijn aangemeld bij uw app. Als u zich na het aanmelden handmatig de id in uw app instelt, wordt een nieuwe unieke gebruiker gemaakt die niet heeft gekozen voor het ontvangen van pushberichten. Deze nieuwe gebruiker zal uw pushberichten niet ontvangen.
>
>Het verplaatsen van uw app naar een nieuwe rapportsuite wordt niet ondersteund. Als u naar een nieuwe rapportreeks migreert, kan uw dupconfiguratie breken, en de berichten zouden niet kunnen worden verzonden.

## Enable push messaging {#section_CBD63C5B11FE4424BC2BF552C23F2BD9}

>[!TIP]
>
>Als uw app al is ingesteld voor het gebruik van berichten via Firebase Cloud Messaging (FCM), kunnen enkele van de volgende stappen al zijn voltooid.

1. Controleer of het `ADBMobileConfig.json`-bestand de vereiste instellingen voor pushberichten bevat.

   Voor het `"marketingCloud"`-object moet de `"org"`-eigenschap zijn geconfigureerd voor pushberichten.

   ```js
   "marketingCloud": { 
     "org": <org-id-string> 
    }
   ```

1. Verkrijg de registratie-id/-token met behulp van de FCM-API (Firebase Cloud Messaging).

   * Zie [Een Firebase Cloud Messaging Client-app instellen op Android](https://firebase.google.com/docs/cloud-messaging/android/client) voor meer informatie over het instellen van FCM.

   ```js
   String token = FirebaseInstanceId.getInstance().getToken();
   ```

1. De registratie-id/token moet worden doorgegeven aan de SDK met behulp van de methode `Config.setPushIdentifier(final String registrationId)`.

   ```js
   Config.setPushIdentifier(token); // token was obtained in step 2
   ```

1. Laat rapportering toe door uw activiteit in de `collectLifecycleData` methode over te gaan.

   Hier zijn de vereisten om duw klik-door rapportering toe te laten:

   * In uw implementatie van `FireBaseMessageService`, moet het voorwerp van de Bundel dat de berichtgegevens bevat, die in de `onMessageReceived` methode met het voorwerp RemoteMessage wordt overgegaan, aan de Intentie worden toegevoegd die wordt gebruikt om de doelactiviteit op klikthrough te openen. Dit kan worden gedaan gebruikend de `putExtras` methode. Zie [putExtras](https://developer.android.com/reference/android/content/Intent.html#putExtras(android.os.Bundle)) voor meer informatie.

   ```java
   Intent intent = new Intent(this, MainActivity.class);
      intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
   // get the bundle from the RemoteMessage object
      intent.putExtras(message.toIntent().getExtras());
   ```

   * In de doelactiviteit van klikthrough, moet de activiteit in SDK met de `collectLifecycleData` vraag worden overgegaan.

      De volgende informatie onthouden:

      * Gebruik `Config.collectLifecycleData(this)` of `Config.collectLifecycleData(this, contextData)`.

      * Gebruik **not** `Config.collectLifecycleData()`.
