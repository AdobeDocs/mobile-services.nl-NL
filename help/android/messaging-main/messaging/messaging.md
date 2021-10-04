---
description: U kunt in-app berichten leveren die worden geactiveerd vanuit analysegegevens of gebeurtenissen. Na de implementatie worden berichten dynamisch aan de app geleverd en is geen code-update vereist.
solution: Experience Cloud,Analytics
title: In-app berichten
topic-fix: Developer and implementation
uuid: 351ee3d2-80b9-4f2d-9696-21f274d89f5a
exl-id: ca9414d1-86e6-4bb2-a2d6-57df37df2403
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 3%

---

# In-app berichten {#in-app-messaging}

U kunt in-app berichten leveren die worden geactiveerd vanuit analysegegevens of gebeurtenissen. Na de implementatie worden berichten dynamisch aan de app geleverd en is geen code-update vereist.

## Nieuwe Adobe Experience Cloud SDK-release

Op zoek naar informatie en documentatie met betrekking tot de Adobe Experience Platform Mobile SDK? Klik [hier](https://aep-sdks.gitbook.io/docs/) voor onze recentste documentatie.

>[!IMPORTANT]
>
>Vanaf september 2018 hebben we een nieuwe, grote versie van de SDK uitgebracht. Deze nieuwe Adobe Experience Platform Mobile SDK&#39;s kunnen worden geconfigureerd via [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* Ga om aan de slag te gaan naar [Launch](https://launch.adobe.com/).
* Ga naar [Github om te zien wat er in de SDK-opslagruimten van het Experience Platform staat: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
> Als u Adobe Experience Platform Mobile SDKs met de Lancering van de Adobe gebruikt, **must** ook installeert de uitbreiding van de Mobiele Diensten van Adobe Analytics om de eigenschappen van de Mobiele Diensten van de Adobe te gebruiken zoals in-app overseinen en dupberichten. Zie [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services) voor meer informatie. Voor meer informatie over het gebruiken van duw overseinen en in-app overseinen met de Experience Cloud SDKs, zie [Pushoverseinen van de opstelling](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) en [Opstelling in-app overseinen](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

>[!IMPORTANT]
>
>Om in-app overseinen te gebruiken, **must** heeft SDK versie 4.2 of later.

U kunt berichten en de regels in de Mobiele diensten van Adobe tot stand brengen die bepalen wanneer de berichten worden getoond. Zie [Een bericht in de app maken](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md) voor meer informatie. Als u in-app berichten wilt weergeven, moet de SDK worden bijgewerkt. U kunt deze stappen zelfs voltooien als u nog geen berichten hebt bepaald. Nadat u berichten hebt gedefinieerd, worden deze dynamisch aan uw app geleverd en weergegeven zonder dat de App Store wordt bijgewerkt.

## In-app berichten inschakelen {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Voeg de bibliotheek aan uw project toe en implementeer levenscyclus.

   Voor meer informatie, zie *Voeg het dossier SDK en Config aan uw Project IntelliJ IDEA of Eclipse* in [de implementatie van de Kern en levenscyclus](/help/android/getting-started/dev-qs.md) toe.

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

1. In elke `collectLifecycleData` vraag, ga `this` over om een verwijzing naar uw huidige activiteit te verstrekken:

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
   }
   ```

1. Controleer of het `ADBMobileConfig.json`-bestand de vereiste instellingen bevat voor berichten in de app.

   >[!IMPORTANT]
   >
   >`messages` of  `remotes` is vereist.

   Voor berichten in de app die bij het starten dynamisch moeten worden bijgewerkt, moet het `remotes`-object aanwezig zijn en correct zijn geconfigureerd:

   ```js
   "messages": [ 
       { 
           "messageId": "de45c43c-37bf-441f-8cbd-cc3ba3469ebe", 
           "template": "fullscreen", 
           "showOffline": false, 
           "showRule": "always", 
           "endDate": 2524730400, 
           "startDate": 0, 
           "audiences": [], 
           "triggers": [], 
           "payload": { // contents change depending on template 
               "html": "<html>html code goes here</html>" 
           }, 
       }, 
       … 
   ] 
   "remotes" : { 
       "analytics.poi": "https://assets.adobedtm.com/…/yourfile.json", 
       "messages": "https://assets.adobedtm.com/…/yourfile.json" 
   }
   ```

   Als dit voorwerp niet wordt gevormd, download een bijgewerkt `ADBMobileConfig.json` dossier van de Mobiele diensten van Adobe. Voor meer informatie, zie [Voor u ](/help/android/getting-started/requirements.md) begint.

## In-app berichten bijhouden {#section_B85CDF6929564AAEA79338B55E5CB1E8}

De SDK&#39;s van Android Mobile volgen de volgende metingen voor uw berichten in de app:

* Voor volledig scherm en waakzame stijl binnen-app berichten:

   * **Afbeeldingen**: wanneer de gebruiker een bericht in de app activeert.
   * **Klik op doorhalingen**: wanneer de gebruiker op  **[!UICONTROL Click through]**.
   * **Annuleren**: wanneer de gebruiker op  **[!UICONTROL Cancel]**.

* Voor aangepaste, volledig scherm in-app berichten moet de HTML-inhoud in het bericht de juiste code bevatten om de SDK een melding te geven van de volgende knoppen:

   * **Voorbeeld van doorklikken**  (omleiden) bijhouden:

      `adbinapp://confirm/?url=https://www.yoursite.com`
   * **Bijhouden van voorbeeld annuleren**  (sluiten):

      `adbinapp://cancel`

## Lokale fallback-afbeelding {#section_DEACC1CE549B4573B556A44A52409941}

Wanneer u een bericht op volledig scherm maakt, kunt u desgewenst een fallback-afbeelding opgeven. Als uw bericht de bedoelde afbeelding niet van het web kan ophalen, probeert de SDK de afbeelding met dezelfde naam te laden in de map met assets van uw toepassing. Zo kunt u uw bericht weergeven in de oorspronkelijke vorm, zelfs als de gebruiker offline is of als de vooraf ingestelde afbeelding onbereikbaar is.

>[!IMPORTANT]
>
>De naam van het fallback afbeeldingselement wordt opgegeven wanneer u het bericht configureert in de services van Adobe Mobile en u moet ervoor zorgen dat de opgegeven bron beschikbaar is.

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
