---
description: U kunt in-app berichten leveren die worden geactiveerd vanuit analysegegevens of gebeurtenissen. Na de implementatie worden berichten dynamisch aan de app geleverd en is geen code-update vereist.
seo-description: U kunt in-app berichten leveren die worden geactiveerd vanuit analysegegevens of gebeurtenissen. Na de implementatie worden berichten dynamisch aan de app geleverd en is geen code-update vereist.
seo-title: In-app berichten
solution: Marketing Cloud,Analytics
title: In-app berichten
topic: Developer and implementation
uuid: 351ee3d2-80b9-4f2d-9696-21f274d89f5a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# In-app berichten {#in-app-messaging}

U kunt in-app berichten leveren die worden geactiveerd vanuit analysegegevens of gebeurtenissen. Na de implementatie worden berichten dynamisch aan de app geleverd en is geen code-update vereist.

## Nieuwe Adobe Experience Cloud SDK-release

Op zoek naar informatie en documentatie over de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze meest recente documentatie.

>[!IMPORTANT]
>
>Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via het [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga naar [Starten](https://launch.adobe.com/)om aan de slag te gaan.
* Ga naar [Github om te zien wat er in de repositories van Experience Platform SDK staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> Als u de Adobe Experience Platform Mobile SDK&#39;s gebruikt met Adobe Launch, **moet** u ook de Adobe Analytics Mobile Services-extensie installeren als u Adobe Mobile Services-functies wilt gebruiken, zoals in-app berichten en pushmeldingen. Zie [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services)voor meer informatie. Voor meer informatie over het gebruiken van duw overseinen en in-app overseinen met de Ervaring Cloud SDKs, zie [Opstelling dupoverseinen](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) en [opstelling in-app overseinen](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

>[!IMPORTANT]
>
>Als u in-app berichten wilt gebruiken, **moet** u SDK versie 4.2 of hoger hebben.

U kunt in Adobe Mobile-services berichten en regels maken die bepalen wanneer berichten worden weergegeven. Zie Een bericht [in de app](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md)maken voor meer informatie. Als u in-app berichten wilt weergeven, moet de SDK worden bijgewerkt. U kunt deze stappen zelfs voltooien als u nog geen berichten hebt bepaald. Nadat u berichten hebt gedefinieerd, worden deze dynamisch aan uw app geleverd en weergegeven zonder dat de App Store wordt bijgewerkt.

## In-app berichten inschakelen {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Voor meer informatie, zie *Voeg het Dossier SDK en Config aan uw IDEA IntelliJ of Project* Eclipse in de implementatie en de levenscyclus [van de](/help/android/getting-started/dev-qs.md)Kern toe.

1. Werk het `AndroidManifest.xml` dossier bij om de volledige het schermactiviteit te verklaren en de Handler van het Bericht toe te laten:

   ```java
   <activity  
   android:name="com.adobe.mobile.MessageFullScreenActivity"  
   android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

   Als u een modale lay-out hebt geselecteerd, selecteert u een van de volgende thema&#39;s voor het bericht:

   * `Theme.Translucent.NoTitleBar.Fullscreen`
   * `Theme.Translucent.NoTitleBar`
   * `Theme.Translucent`
   Bijvoorbeeld:

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
   android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. In elke `collectLifecycleData` vraag, ga over `this` om een verwijzing naar uw huidige activiteit te verstrekken:

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
   }
   ```

1. Controleer of het `ADBMobileConfig.json` bestand de vereiste instellingen voor in-app berichten bevat.

   >[!IMPORTANT]
   >
   >`messages` of `remotes` is vereist.

   Als u wilt dat in-app-berichten tijdens het starten dynamisch worden bijgewerkt, moet het `remotes` object aanwezig zijn en correct zijn geconfigureerd:

   ```js
   “messages”: [ 
       { 
           “messageId”: “de45c43c-37bf-441f-8cbd-cc3ba3469ebe”, 
           “template”: “fullscreen”, 
           “showOffline”: false, 
           “showRule”: “always”, 
           “endDate”: 2524730400, 
           “startDate”: 0, 
           “audiences”: [], 
           “triggers”: [], 
           “payload”: { // contents change depending on template 
               “html”: “<html>html code goes here</html>” 
           }, 
       }, 
       … 
   ] 
   “remotes” : { 
       “analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”, 
       “messages”: “https://assets.adobedtm.com/…/yourfile.json” 
   }
   ```

   Als dit object niet is geconfigureerd, downloadt u een bijgewerkt `ADBMobileConfig.json` bestand van Adobe Mobile-services. Zie [Voor u begint](/help/android/getting-started/requirements.md)voor meer informatie.

## In-app berichten bijhouden {#section_B85CDF6929564AAEA79338B55E5CB1E8}

De SDK&#39;s van Android Mobile volgen de volgende metingen voor uw berichten in de app:

* Voor volledig scherm en waakzame stijl binnen-app berichten:

   * **Afbeeldingen**: wanneer de gebruiker een bericht in de app activeert.
   * **Klik op doorhalingen**: wanneer de gebruiker op **[!UICONTROL Click through]**.
   * **Annuleren**: wanneer de gebruiker op **[!UICONTROL Cancel]**.

* Voor aangepaste, volledig scherm in-app berichten moet de HTML-inhoud in het bericht de juiste code bevatten om de SDK een melding te geven van de volgende knoppen:

   * **Voorbeelden van doorklikken** (omleiden) volgen:

      `adbinapp://confirm/?url=https://www.yoursite.com`
   * **Bijhouden van voorbeeld annuleren** (sluiten):

      `adbinapp://cancel`

## Lokale fallback-afbeelding {#section_DEACC1CE549B4573B556A44A52409941}

Wanneer u een bericht op volledig scherm maakt, kunt u desgewenst een fallback-afbeelding opgeven. Als uw bericht de bedoelde afbeelding niet van het web kan ophalen, probeert de SDK de afbeelding met dezelfde naam te laden in de map met assets van uw toepassing. Zo kunt u uw bericht weergeven in de oorspronkelijke vorm, zelfs als de gebruiker offline is of als de vooraf ingestelde afbeelding onbereikbaar is.

>[!IMPORTANT]
>
>De naam van het fallback-afbeeldingselement wordt opgegeven wanneer u het bericht configureert in Adobe Mobile-services en u moet ervoor zorgen dat de opgegeven bron beschikbaar is.

## Meldingspictogrammen configureren {#section_DDA28BDBCBB748BCBECF3AB50A177D48}

Met de volgende methoden kunt u de kleine en grote pictogrammen configureren die in het systeemvak worden weergegeven, en het grote pictogram dat wordt weergegeven wanneer meldingen in de meldingslade worden weergegeven.

* **Config.setSmallIconResourceId(int resourceId)**

   Stel het kleine pictogram in dat wordt gebruikt voor meldingen die door de SDK worden gemaakt. Dit pictogram verschijnt in de statusbar en is het secundaire beeld dat wordt getoond wanneer de gebruiker het volledige bericht in het berichtcentrum ziet.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **Config.setLargeIconResourceId(int resourceId)**

   Stel het grote pictogram in dat wordt gebruikt voor meldingen die door de SDK worden gemaakt. Dit pictogram is de primaire afbeelding die wordt weergegeven wanneer de gebruiker het volledige bericht ziet in het meldingscentrum.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void setLargeIconResourceId(final int resourceId); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Config.setLargeIconResourceId(R.drawable.appIcon); 
      ```
