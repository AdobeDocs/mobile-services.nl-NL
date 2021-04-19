---
description: Vanaf Android SDK versie 4.5 is een nieuwe Android-extensie toegevoegd waarmee u gegevens kunt verzamelen van uw Android Wearable-app.
seo-description: Vanaf Android SDK versie 4.5 is een nieuwe Android-extensie toegevoegd waarmee u gegevens kunt verzamelen van uw Android Wearable-app.
seo-title: Aan de slag met Android-kabels
solution: Experience Cloud,Analytics
title: Aan de slag met Android-kabels
topic-fix: Developer and implementation
uuid: bfe5d41e-b17c-4634-80ac-7a38671ecb81
exl-id: 79cfaa48-d9b2-4518-8b31-d7041898a71b
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Android-oormerken: aan de slag{#android-wearables-getting-started}

Vanaf Android SDK versie 4.5 is een nieuwe Android-extensie toegevoegd waarmee u gegevens kunt verzamelen van uw Android Wearable-app.

## De SDK voor een handheld-app configureren (Android Studio) {#section_262237484EC44C58953891B105F0D000}

Voor meer informatie over het invoeren van SDK in uw project, zie [de Implementatie van de Kern en Levenscyclus](/help/android/getting-started/dev-qs.md).

1. Voeg het `ADBMobileConfig.json` dossier aan de activa omslag van uw project toe.
1. Voeg het `adobeMobileLibrary-*.jar` dossier aan de libs omslag toe of zorg ervoor dit dossier door het project van verwijzingen wordt voorzien.

   >[!TIP]
   >
   >Mogelijk moet u het onbewerkte project synchroniseren nadat u het bestand `.jar` hebt toegevoegd.

1. In de `onCreate` methode, sta SDK toegang tot uw toepassingscontext toe door `Config.setContext` te gebruiken:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext()); 
   }
   ```

1. Voeg de volgende code aan het `AndroidManifest.xml` dossier toe:

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

1. Zorg ervoor dat uw project de Google Play-services-bibliotheek bevat.
1. `WearableListenerService` implementeren of de corresponderende code toevoegen aan uw `WearableListenerService`:

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

1. `WearListenerService` toevoegen aan het `AndroidManifest.xml`-bestand:

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

## De SDK configureren voor een draagbare app (Android Studio) {#section_2268EC03E20B4A228A28BDCFEA2E9AE4}

1. Voer een van de volgende taken uit:

   * Voeg hetzelfde `ADBMobileConfig.json`-bestand toe aan de map assets van het te exporteren project.
   * Wijzig de configuratie van de greep om de `ADBMobileConfig.json` in de map assets van de handheld-app te gebruiken:

      ```java
      android { 
      
          sourceSets { 
              main { 
                  assets.srcDirs = ['src/main/assets','../mobile/src/main/assets'] 
              } 
         } 
      }
      ```

1. Voeg het `adobeMobileLibrary-*.jar` dossier aan de libs omslag toe of zorg ervoor het door het project van verwijzingen wordt voorzien.

   Mogelijk moet u het verloopproject synchroniseren nadat u het jar-bestand hebt toegevoegd.

1. In de `onCreate` methode, sta SDK toegang tot uw toepassingscontext toe gebruikend `Config.setContext`:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main);      
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext(), Config.ApplicationType.APPLICATION_TYPE_WEARABLE); 
   }
   ```

1. Voeg de volgende code toe aan `AndroidManifest.xml`:

   ```java
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. Zorg ervoor dat uw project de Google Play-services-bibliotheek bevat.
1. `WearableListenerService` implementeren of de corresponderende code toevoegen aan uw `WearableListenerService`:

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerWearable.onDataChanged(dataEvents); 
       } 
   
   }
   ```

1. `WearListenerService` toevoegen aan het `AndroidManifest.xml`-bestand:

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
