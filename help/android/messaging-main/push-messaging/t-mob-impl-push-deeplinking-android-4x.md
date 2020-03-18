---
description: Nadat u de deep linking-URL hebt geconfigureerd in de gebruikersinterface van Adobe Mobile Services, bevindt deze URL zich in de pushlading met de adb_deplink-toets.
seo-description: Nadat u de deep linking-URL hebt geconfigureerd in de gebruikersinterface van Adobe Mobile Services, bevindt deze URL zich in de pushlading met de adb_deplink-toets.
seo-title: Implementeer Push Messaging met Deep Linking
title: Implementeer Push Messaging met Deep Linking
uuid: e24f9248-8d48-4e57-84af-3a05b72e2a09
translation-type: tm+mt
source-git-commit: 13ff2cb549c4b82a4e0285e1c7c6b3f9c1a5bd4b

---


# Push messaging implementeren met deep linking {#implement-push-messaging-with-deep-linking}

Nadat u de deep linking-URL hebt geconfigureerd in de gebruikersinterface van Adobe Mobile Services, bevindt deze URL zich in de pushlading met de adb_deplink-toets.

U kunt URL krijgen door `remoteMessage.getData().get("adb_deeplink")` in te roepen `FirebaseMessagingService`.

>[!TIP]
>
>U kunt verschillende intenties definiëren, afhankelijk van het feit of de payload een deep linking-URL heeft.

1. Voer een van de volgende taken uit:

   * Als de deep linking-URL **zich** in de pushlading bevindt, maakt u een `ACTION_VIEW` intentie met de URL.

      Wanneer de gebruiker op het pushbericht klikt, wordt een diepe koppeling geactiveerd.

   * Als de deep linking-URL zich niet **in de pushlading** bevindt, maakt u een intentie die een van uw activiteiten opent.

## Voorbeeld

Hier volgt een voorbeeldimplementatie voor de klasse die zich uitbreidt van `FirebaseMessagingService`:

```java
public void onMessageReceived(RemoteMessage message) { 
 
       Map<String, String> data = message.getData(); 
       String messageStr = data.get("message"); 
       String deepLink = data.get("adb_deeplink"); 
 
       sendNotification(deepLink, messageStr, data); 
    } 
 
private void sendNotification(String deeplink, String message, Map<String, String> data) { 
       Intent intent; 
 
       if (deeplink!=null) { 
           intent = new Intent(Intent.ACTION_VIEW, Uri.parse(deeplink)); 
       } else { 
           intent = new Intent(this, MainActivity.class); 
       } 
 
       intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP); 
 
       //put the data map into the intent to track clickthroughs 
       Bundle pushData = new Bundle(); 
       Set<String> keySet = data.keySet(); 
       for (String key : keySet) { 
           pushData.putString(key, data.get(key)); 
       } 
 
       intent.putExtras(pushData); 
 
       PendingIntent pendingIntent = PendingIntent.getActivity(this, 0, intent, 
               PendingIntent.FLAG_ONE_SHOT); 
 
       Uri defaultSoundUri= RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION); 
 
       NotificationCompat.Builder notificationBuilder = new NotificationCompat.Builder(this) 
                .setSmallIcon(R.drawable.icon) 
                .setContentTitle("FCM Deep Link Push") 
                .setContentText(message) 
                .setAutoCancel(true) 
                .setSound(defaultSoundUri) 
                .setContentIntent(pendingIntent); 
 
       NotificationManager notificationManager =  
       (NotificationManager)getApplicationContext().getSystemService(Context.NOTIFICATION_SERVICE); 
           notificationManager.notify(0, notificationBuilder.build()); 
       } 
```
