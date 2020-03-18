---
description: U kunt afbeeldingsbestanden koppelen aan uw Android-meldingen. Door visuele componenten toe te voegen kan de betrokkenheid van de gebruiker bij pushberichten aanzienlijk toenemen.
seo-description: U kunt afbeeldingsbestanden koppelen aan uw Android-meldingen. Door visuele componenten toe te voegen kan de betrokkenheid van de gebruiker bij pushberichten aanzienlijk toenemen.
seo-title: Rich Push-berichten ontvangen
title: Rich Push-berichten ontvangen
uuid: 4a0340a6-666b-49b6-907a-9afc966dfdba
translation-type: tm+mt
source-git-commit: dca3663986b3ecc6e9fb736cc99513279715225c

---


# Rich push-berichten ontvangen {#receive-rich-push-notifications}

U kunt afbeeldingsbestanden koppelen aan uw Android-meldingen. Door visuele componenten toe te voegen kan de betrokkenheid van de gebruiker bij pushberichten aanzienlijk toenemen.

## Het binnenkomende uitgebreide pushbericht (FCM) verwerken {#section_AF1A3BC2312C4E1DA517CC90296C11E2}

Als de app op de voorgrond staat, wordt het pushbericht verwerkt door de app die de `FirebaseMessagingService` klasse uitbreidt en wordt deze als volgt in het manifestbestand gedeclareerd:

```java
<service
    android:name=".MyFirebaseMessagingService"
    android:exported="false">
    <intent-filter>
        <action android:name="com.google.firebase.MESSAGING_EVENT" />
    </intent-filter>
</service>
```

>[!IMPORTANT]
>
>De klasse die de `onMessageReceived()` implementatie bevat behandelt de gegevens die worden ontvangen.

Als het pushbericht een Media-URL bevat, is de URL beschikbaar in de `RemoteMessage` parameter die aan de `onMessageReceived()` functie wordt doorgegeven. De te gebruiken sleutel is `attachment-url` zoals aangetoond in het volgende codevoorbeeld:

```java
public class MyFirebaseMessagingService extends FirebaseMessagingService {
        @Override
        public void onMessageReceived(RemoteMessage remoteMessage) {
      Log.d("Remote Message", "RemoteMessage: " + remoteMessage.toString());
            // Check if message contains a data payload.
            if (remoteMessage.getData().size() > 0) {
                Log.d("Remote Message", "RemoteMessage: " + remoteMessage.getData());
                sendNotification(remoteMessage);
            }
    }
 
private void sendNotification(RemoteMessage message) {
        Intent intent = new Intent(this, MainActivity.class);
    intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
    PendingIntent pendingIntent = PendingIntent.getActivity(this, 0 /* Request code */, intent, PendingIntent.FLAG_ONE_SHOT);

     String channelId = getString(R.string.default_notification_channel_id);
     Uri defaultSoundUri = RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION);
     NotificationCompat.Builder notificationBuilder =
                new NotificationCompat.Builder(this, channelId)
                        .setSmallIcon(R.drawable.ic_stat_ic_notification)
                        .setContentTitle(getString(R.string.fcm_message))
                        .setContentText(message.getData().get("body"))
                        .setAutoCancel(true)
                        .setSound(defaultSoundUri)
                        .setContentIntent(pendingIntent);
  
    //Handle image url if present in the push message 
        String attachmentUrl = message.getData().get("attachment-url");
  
    if (attachmentUrl != null) { 
    Bitmap image = getBitmapFromURL(attachmentUrl); 
    if (image != null) { 
      notificationBuilder.setStyle(new        NotificationCompat.BigPictureStyle().bigPicture(image)); 
        } 
        } 

     NotificationManager notificationManager =
              (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);

     // Since android Oreo notification channel is needed.
     if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
        NotificationChannel channel = new NotificationChannel(channelId,
                    "Channel human readable title",
                    NotificationManager.IMPORTANCE_DEFAULT);
            notificationManager.createNotificationChannel(channel);
     }

     notificationManager.notify(0 /* ID of notification */, notificationBuilder.build());
    }
}
```

>[!IMPORTANT]
>
>Wanneer u deze optie instelt, worden grote afbeeldingen mogelijk niet weergegeven. `NotificationCompat.BigPictureStyle` Stel de native optie in om ervoor te zorgen dat grote afbeeldingen altijd worden weergegeven `Notification.BigPictureStyle`.

## Voorbeeld van uitgebreide pushmelding {#section_6819316BEDDE45108413B541CA2BB2DC}

Hier volgt een voorbeeld van een uitgebreide pushmelding met een afbeelding:

![](assets/rich-push-notification_example.png)

Zie [Inschakelen met RTF-berichten](https://developer.android.com/distribute/best-practices/engage/rich-notifications.html)voor meer informatie over uitgebreide pushmeldingen met Android.