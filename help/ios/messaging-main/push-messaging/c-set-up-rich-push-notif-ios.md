---
description: U kunt afbeeldingsbestanden koppelen aan uw Apple-meldingen. Door visuele componenten toe te voegen, kan de betrokkenheid van uw gebruikers met pushberichten aanzienlijk toenemen.
seo-description: U kunt afbeeldingsbestanden koppelen aan uw Apple-meldingen. Door visuele componenten toe te voegen, kan de betrokkenheid van uw gebruikers met pushberichten aanzienlijk toenemen.
seo-title: Rich Push-berichten ontvangen
title: Rich Push-berichten ontvangen
uuid: 0dbda409-cf49-4eb8-90ee-baf27911dc07
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Rich push-berichten ontvangen {#receive-rich-push-notifications}

U kunt afbeeldingsbestanden koppelen aan uw Apple-meldingen. Door visuele componenten toe te voegen, kan de betrokkenheid van uw gebruikers met pushberichten aanzienlijk toenemen.

Rijke pushmeldingen ontvangen in uw iOS-app:

1. Implementeer pushberichten voor de app door de stappen in [Push Messaging](/help/ios/messaging-main/push-messaging/push-messaging.md)te voltooien.
1. Controleer of u een pushbericht voor tekst naar uw app kunt verzenden.
1. Voeg een Uitbreiding van de Dienst van het Bericht toe door de volgende stappen te voltooien:

   1. Selecteer **[!UICONTROL File]** > **[!UICONTROL New]** > **[!UICONTROL Target]**.
   1. Selecteer **[!UICONTROL Notification Service Extension]**.
   1. Controleer of het `NotificationService.m` bestand bestaat.

1. Open het `NotificationService.m` bestand en controleer of de volgende gedelegeerde methoden bestaan:

   * Één methode om een berichtverzoek te ontvangen.
   * Één methode om de afloop van de de dienstuitbreiding te behandelen.

      Voor uitgebreide pushberichten wordt de eerste methode gebruikt:

      ```objective-c
      (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent *contentToDeliver))contentHandler;
      ```

      In deze methode kunt u de media-URL ophalen `userInfo` met de `attachment-url` toets. Nadat u het bestand naar een lokale map hebt gedownload, voegt u het lokale pad toe aan `bestAttemptContent.attachments`.

      Hier volgt een voorbeeld van de code in deze methode:

      ```objective-c
      - (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
      self.contentHandler = contentHandler;
      self.bestAttemptContent = [request.content mutableCopy];
         NSDictionary* userInfo = request.content.userInfo;
      if(userInfo[@"attachment-url"]){
         NSURL* url = [[NSURL alloc] initWithString:userInfo[@"attachment-url"]];
         NSURLSessionDownloadTask* task = [[NSURLSession sharedSession] downloadTaskWithURL:url completionHandler:^(NSURL * _Nullable location, NSURLResponse * _Nullable response, NSError * _Nullable error) {
             if(!location){
                 return;
             }
             NSString* tmpDirectory = NSTemporaryDirectory();
             NSString* tmpFilePath = [NSString stringWithFormat:@"file://%@%d%d%@", tmpDirectory, arc4random_uniform(100000),
                                    arc4random_uniform(100000), [url lastPathComponent]];
             NSURL* tmpUrl = [[NSURL alloc] initWithString:tmpFilePath];
             NSError * fileError = nil;
             [[NSFileManager defaultManager] moveItemAtURL:location toURL:tmpUrl error:&amp;fileError];
             if(fileError){
                 return;
             }
             UNNotificationAttachment* attachment = [UNNotificationAttachment attachmentWithIdentifier:@"video" URL:tmpUrl options:nil error:&amp;fileError];
             if(fileError){
                 return;
             }
             self.bestAttemptContent.attachments = @[attachment];
             self.contentHandler(self.bestAttemptContent);
         }];
         [task resume];
       }
      }
      ```


Zie [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment)voor meer informatie over uitgebreide pushmeldingen met iOS.
