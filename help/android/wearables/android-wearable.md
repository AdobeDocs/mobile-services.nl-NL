---
description: Vanaf Android SDK versie 4.5 is een nieuwe Android-extensie toegevoegd waarmee u gegevens kunt verzamelen van uw Android Wearable-app.
seo-description: Vanaf Android SDK versie 4.5 is een nieuwe Android-extensie toegevoegd waarmee u gegevens kunt verzamelen van uw Android Wearable-app.
seo-title: Aan de slag met Android-kabels
solution: Marketing Cloud,Analytics
title: Aan de slag met Android-kabels
topic: Developer and implementation
uuid: bfe5d41e-b17c-4634-80ac-7a38671ecb81
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Android-oormerken: aan de slag{#android-wearables-getting-started}

Vanaf Android SDK versie 4.5 is een nieuwe Android-extensie toegevoegd waarmee u gegevens kunt verzamelen van uw Android Wearable-app.

## De SDK voor een handheld-app configureren (Android Studio) {#section_262237484EC44C58953891B105F0D000}

Voor meer informatie over het invoeren van SDK in uw project, zie de Implementatie van de [Kern en Levenscyclus](/help/android/getting-started/dev-qs.md).

1. Voeg het `ADBMobileConfig.json` bestand toe aan de map assets van uw project.
1. Voeg het `adobeMobileLibrary-*.jar` bestand toe aan de map libs of zorg ervoor dat naar dit bestand wordt verwezen door het project.

   >[!TIP]
   >
   >Mogelijk moet u het onbewerkte project synchroniseren nadat u het `.jar` bestand hebt toegevoegd.

1. In de `onCreate` methode verleent de SDK toegang tot uw toepassingscontext door te gebruiken `Config.setContext`:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext()); 
   }
   ```

1. Voeg de volgende code toe aan het `AndroidManifest.xml` bestand:

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
1. Implementeer `WearableListenerService` of voeg de corresponderende code toe aan uw `WearableListenerService`:

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

1. Toevoegen `WearListenerService` aan `AndroidManifest.xml` bestand:

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

   * Voeg hetzelfde `ADBMobileConfig.json` bestand toe aan de map assets van het draagbare project.
   * Wijzig de configuratie van de greep om de inhoud `ADBMobileConfig.json` in de map assets van de handheld-app te gebruiken:

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

1. In de `onCreate` methode verleent u de SDK toegang tot uw toepassingscontext met behulp van `Config.setContext`:

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
1. Implementeer `WearableListenerService` of voeg de corresponderende code toe aan uw `WearableListenerService`:

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerWearable.onDataChanged(dataEvents); 
       } 
   
   }
   ```

1. Toevoegen `WearListenerService` aan `AndroidManifest.xml` bestand:

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

