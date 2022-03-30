---
description: Vanaf Android SDK versie 4.5 is een nieuwe Android-extensie toegevoegd waarmee u gegevens kunt verzamelen van uw Android Wearable-app.
solution: Experience Cloud Services,Analytics
title: Aan de slag met Android-kabels
topic-fix: Developer and implementation
uuid: bfe5d41e-b17c-4634-80ac-7a38671ecb81
exl-id: 79cfaa48-d9b2-4518-8b31-d7041898a71b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Android-oormerken: aan de slag{#android-wearables-getting-started}

Vanaf Android SDK versie 4.5 is een nieuwe Android-extensie toegevoegd waarmee u gegevens kunt verzamelen van uw Android Wearable-app.

## De SDK voor een handheld-app configureren (Android Studio) {#section_262237484EC44C58953891B105F0D000}

Voor meer informatie over het invoeren van SDK in uw project, zie [Core-implementatie en levenscyclus](/help/android/getting-started/dev-qs.md).

1. Voeg de `ADBMobileConfig.json` bestand naar de map assets van uw project.
1. Voeg de `adobeMobileLibrary-*.jar` bestand naar de map libs of zorg ervoor dat naar dit bestand wordt verwezen door het project.

   >[!TIP]
   >
   >Mogelijk moet u het verloopproject synchroniseren nadat u het `.jar` bestand.

1. In de `onCreate` de SDK-toegang tot uw toepassingscontext toestaan door `Config.setContext`:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext()); 
   }
   ```

1. Voeg de volgende code toe aan de `AndroidManifest.xml` bestand:

   ```java
       <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /> 
       <uses-permission android:name="android.permission.INTERNET" /> 
       <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
   
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. Zorg ervoor dat uw project de Google-bibliotheek voor afspeelservices bevat.
1. Implementeren `WearableListenerService` of voeg de corresponderende code toe aan uw `WearableListenerService`:

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onMessageReceived(MessageEvent messageEvent) { 
           super.onMessageReceived(messageEvent); 
       } 
   
       private GoogleApiClient mGoogleApiClient; 
   
       @Override 
       public void onCreate() { 
           super.onCreate(); 
           mGoogleApiClient = new GoogleApiClient.Builder(this) 
                   .addApi(Wearable.API) 
                   .build(); 
           mGoogleApiClient.connect(); 
       } 
       @Override 
       public void onDestroy() { 
           super.onDestroy(); 
           mGoogleApiClient.disconnect(); 
       } 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerHandheld.onDataChanged(dataEvents, mGoogleApiClient, this); 
       } 
   }
   ```

1. Toevoegen `WearListenerService` aan de `AndroidManifest.xml` bestand:

   ```java
   If you are using Google Play Services  < 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                   <action android:name="com.google.android.gms.wearable.BIND_LISTENER" /> 
               </intent-filter> 
       </service> 
   </application> 
   If you are using Google Play Services >= 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                     <action android:name="com.google.android.gms.wearable.DATA_CHANGED" /> 
                    <data android:scheme="wear" android:host="*" android:pathPrefix="/abdmobile" /> 
               </intent-filter> 
       </service> 
   </application> 
   
   Please find more information from google's blog https://android-developers.googleblog.com/2016/04/deprecation-of-bindlistener.html. 
   Permalink Edit
   ```

## De SDK voor een draagbare app configureren (Android Studio) {#section_2268EC03E20B4A228A28BDCFEA2E9AE4}

1. Voer een van de volgende taken uit:

   * Hetzelfde toevoegen `ADBMobileConfig.json` bestand naar de map assets van uw draagbare project.
   * Wijzig de configuratie van de grijswaarden om de  `ADBMobileConfig.json` in de map assets van de handheld app:

      ```java
      android { 
      
          sourceSets { 
              main { 
                  assets.srcDirs = ['src/main/assets','../mobile/src/main/assets'] 
              } 
         } 
      }
      ```

1. Voeg de `adobeMobileLibrary-*.jar` bestand naar de map libs of zorg ervoor dat er naar deze map wordt verwezen door het project.

   Mogelijk moet u het verloopproject synchroniseren nadat u het jar-bestand hebt toegevoegd.

1. In de `onCreate` de SDK-toegang tot uw toepassingscontext toestaan met `Config.setContext`:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main);      
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext(), Config.ApplicationType.APPLICATION_TYPE_WEARABLE); 
   }
   ```

1. De volgende code toevoegen aan `AndroidManifest.xml`:

   ```java
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. Zorg ervoor dat uw project de Google-bibliotheek voor afspeelservices bevat.
1. Implementeren `WearableListenerService` of voeg de corresponderende code toe aan uw `WearableListenerService`:

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerWearable.onDataChanged(dataEvents); 
       } 
   
   }
   ```

1. Toevoegen `WearListenerService` aan de `AndroidManifest.xml` bestand:

   ```java
   If you are using Google Play Services  < 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                   <action android:name="com.google.android.gms.wearable.BIND_LISTENER" /> 
               </intent-filter> 
       </service> 
   </application> 
   If you are using Google Play Services >= 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                     <action android:name="com.google.android.gms.wearable.DATA_CHANGED" /> 
                    <data android:scheme="wear" android:host="*" android:pathPrefix="/abdmobile" /> 
               </intent-filter> 
       </service> 
   </application> 
   Please find more information from google's blog https://android-developers.googleblog.com/2016/04/deprecation-of-bindlistener.html. 
   Permalink Edit
   ```
