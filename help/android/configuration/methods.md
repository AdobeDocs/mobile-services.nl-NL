---
description: Hier volgt een lijst met methoden die worden geleverd door de Android-bibliotheek.
keywords: android;library;mobile;sdk
seo-description: Hier volgt een lijst met methoden die worden geleverd door de Android-bibliotheek.
seo-title: Configuratiemethoden
solution: Marketing Cloud,Analytics
title: Configuratiemethoden
topic: Developer and implementation
uuid: 663aeb6c-1b97-4a3a-8c0e-dd4c2ec28c01
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 22%

---


# Configuratiemethoden{#configuration-methods}

Hier volgt een lijst met methoden die worden geleverd door de Android-bibliotheek.

## Eerste configuratie {#section_9169243ECC4744A899A8271F92090ECD}

De volgende methode moet één keer worden aangeroepen in de `onCreate` methode van uw hoofdactiviteit:

* `setContext`
Hier volgt het codevoorbeeld voor deze methode:

   ```java
    @Override
    public void onCreate(BundlesavedInstanceState){
      super.onCreate(savedInstanceState)
      setContentView(R.layout.main);
      Config.setContext(this.getApplicationContext());
    }
   ```

## SDK-instellingen (klasse Config) {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **registerAdobeDataCallback**

   * Registreert een object dat de `AdobeDataCallback` interface implementeert. De overschreven methode &#39;call&#39; wordt aangeroepen met een `Config.MobileDataEvent` waarde en de bijbehorende gegevens in een instructie `Map<String, Object>` voor de activeringsgebeurtenis. Voor meer details over welke gebeurtenissen deze callback zullen teweegbrengen, zie *MobileDataEventEnum* bij de bodem van dit onderwerp.

      >[!TIP]
      >
      >Voor deze methode is versie 4.9.0 of hoger vereist.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void registerAdobeDataCallback(final AdobeDataCallback&amp;nbsp;callback);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
        Config.registerAdobeDataCallback(new Config.AdobeDataCallback() {
          @Override
          public void call(Config.MobileDataEvent event, Map<String, Object> contextData) {
              // handle each event type accordingly 
              if (event == Config.MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL) {
                   // do something with acquisition data found in contextData parameter
                   HashMap<String, Object> acquisitionData = new HashMap<String, Object>(contextData);
              }
          }
      });
      ```

* **getVersion**

   * Retourneert de huidige versie van de Adobe Mobile-bibliotheek.
   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static String getVersion();
      ```

   * Hier volgt een codevoorbeeld voor deze methode:

      ```java
      String libraryVersion = Config.getVersion(); 
      ```

* **getPrivacyStatus**

   * Retourneert de opsomming van de privacystatus voor de huidige gebruiker.

      Hier volgen de statuswaarden voor privacy:

      * `MOBILE_PRIVACY_STATUS_OPT_IN`, waar de treffers onmiddellijk worden verzonden.
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`, waar het wordt weggegooid.
      * `MOBILE_PRIVACY_STATUS_UNKNOWN`Als tijdstempel is ingeschakeld in uw rapportsuite, worden treffers opgeslagen totdat de privacystatus verandert in aanmelden (hits worden verzonden) of Afmelden (hits worden genegeerd).

         Als de tijdstempel van uw rapportsuite niet is ingeschakeld, worden treffers verwijderd totdat de privacystatus verandert en u zich aanmeldt. De standaardwaarde wordt ingesteld in het `ADBMobileConfig.json` bestand.
   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static MobilePrivacyStatus getPrivacyStatus(); 
      ```

   * Hier volgt een codevoorbeeld voor deze methode:

      ```java
      MobilePrivacyStatus privacyStatus Config.getPrivacyStatus();
      ```


* **setPrivacyStatus**

   * Hiermee stelt u de privacystatus voor de huidige gebruiker in `status`.

      U kunt de privacystatus instellen op een van de volgende waarden:
      * `MOBILE_PRIVACY_STATUS_OPT_IN`, waar de treffers onmiddellijk worden verzonden. Deze treffers worden onmiddellijk verzonden.
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`, waar het wordt weggegooid. Deze treffers worden genegeerd.
      * `MOBILE_PRIVACY_STATUS_UNKNOWN`Als tijdstempel is ingeschakeld in uw rapportsuite, worden treffers opgeslagen totdat de privacystatus verandert in aanmelden (hits worden verzonden) of Afmelden (hits worden genegeerd).
Als de tijdstempel van uw rapportsuite niet is ingeschakeld, worden treffers verwijderd totdat de privacystatus verandert en u zich aanmeldt.
   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void setPrivacyStatus(MobilePrivacyStatus status); 
      ```

   * Hier volgt een codevoorbeeld voor deze methode:

      ```java
      Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
      ```


* **getLifetimeValue**

   * Retourneert de levensduurwaarde van de huidige gebruiker. De standaardwaarde is `0`.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static BigDecimal getLifetimeValue();
      ```

   * Hier volgt een codevoorbeeld voor deze methode:

      ```java
      BigDecimal currentLifetimeValue Config.getLifetimeValue(); 
      ```

* **getUserIdentifier**

   * Als een aangepaste id is ingesteld, wordt de aangepaste gebruikers-id geretourneerd. Als er geen aangepaste id is ingesteld, wordt deze geretourneerd `null`. De standaardwaarde is `null`.

      >[!TIP]
      >
      >Als uw app van de Experience Cloud 3.x naar de 4.x-SDK upgradet, wordt de vorige aangepaste of automatisch gegenereerde bezoeker-id opgehaald en opgeslagen als de aangepaste gebruikers-id. Op deze manier blijven bezoekersgegevens behouden tussen SDK-upgrades. Voor nieuwe installaties op 4.x SDK, tot het wordt geplaatst, is het gebruikersherkenningsteken `null`.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static String&amp getUserIdentifier();
      ```

   * Hier het codevoorbeeld voor deze methode:

      ```java
      String userId = Config.getUserIdentifier();
      ```

* **setUserIdentifier**

   * Hiermee stelt u de gebruikers-id in op `identifier`.
   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void setUserIdentifer(String identifier);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Config.setUserIdentifier("billybob"); 
      ```

* **getDebugLogging**

   * Retourneert de huidige voorkeur voor foutopsporing. De standaardwaarde is `false`.
   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static Boolean getDebugLogging(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Boolean debugging = Config.getDebugLogging(); 
      ```

* **setDebugLogging**
   * Hiermee stelt u de voorkeur voor foutopsporing in op `debugLogging`.
   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void setDebugLogging(Boolea debugLogging);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Config.setDebugLogging(true);
      ```

* **collectionLifecycleData**
   * Geeft aan de SDK aan dat levenscyclusgegevens moeten worden verzameld voor gebruik in alle oplossingen in de SDK. Zie [Levenscyclusstatistieken](/help/android/configuration/methods.md)voor meer informatie.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void collectLifecycleData(final Activity activity,final Map<String, Object>contextData); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      @Override
      protectedvoid  onResume()  {
        super.onResume();
        Config.collectLifecycleData(this);
        } 
      ```

      Met extra contextgegevens:

      ```java
      @Override
      public  void  onResume()  {
        HashMap<String, Object> contextData = new HashMap<String, Object>();
        contextData.put("myapp.category", "Game");        Config.collectLifecycleData(this, contextData);} 
      ```

* **collectLifecycleData (activity)**

   * (**Versie 4.2 of hoger**) Hiermee geeft u aan de SDK door dat levenscyclusgegevens moeten worden verzameld voor gebruik in alle oplossingen in de SDK. Zie [Levenscyclusstatistieken](/help/android/metrics.md)voor meer informatie.
   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void collectLifecycleData(final Activity activity);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      @Overrideprotected void onResume() {
        super.onResume()
        // assume being called in an Activity class Config.collectLifecycleData(this);
        } 
      ```

* **pauseCollecting &#x200B; LifecycleData**

   * Geeft aan de SDK aan dat de app is gepauzeerd, zodat de levenscycluswaarden correct worden berekend. Hiermee wordt bijvoorbeeld `onPause` een tijdstempel verzameld om de lengte van de vorige sessie te bepalen. Hierdoor wordt ook een vlag ingesteld zodat de levenscyclus weet dat de app niet vastloopt. Zie [Levenscyclusstatistieken](/help/android/metrics.md)voor meer informatie.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void pauseCollectingLifecycleData(); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      @Override
      protected void onPause() {
        super.onPause();
        Config.pauseCollectingLifecycleData();
      } 
      ```

* **setSmallIconResourceId(int resourceId)**

   * (**Versie 4.2 of later**) Hiermee stelt u het kleine pictogram in dat wordt gebruikt voor meldingen die door de SDK zijn gemaakt. Dit pictogram wordt weergegeven op de statusbalk en is de secundaire afbeelding die wordt weergegeven wanneer de gebruiker het volledige bericht ziet in het meldingscentrum.
   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **setLargeIconResourceId(int resourceId)**

   * (**Versie 4.2 of later**) Hiermee stelt u het grote pictogram in dat wordt gebruikt voor meldingen die door de SDK zijn gemaakt. Dit pictogram is de primaire afbeelding die wordt weergegeven wanneer de gebruiker de volledige melding in het meldingscentrum ziet.
   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void setLargeIconResourceId(final int  resourceId);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```Java
      Config.setLargeIconResourceId(R.drawable.appIcon);
      ```

* **overrideConfigStream(InputStream configInput)**

   * (**Versie 4.2 of hoger**) Hiermee kunt u een ander ADBMobile JSON-configuratiebestand laden wanneer de toepassing wordt gestart. De verschillende configuratie wordt gebruikt tot de toepassing wordt gesloten.
   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void overrideConfigStream(final InputStream configInput);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
       try {
          InputStream configInput = getAssets().open("ExampleJSONFile.json") 
          Config.overrideConfigStream(configInput)
          } catch (IOException ex) { 
          //do something with the exception if needed
      }
      ```

* **setPushIdentifier**

   * Hiermee stelt u het apparaattoken voor pushberichten in.
   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void setPushIdentifier(final String registrationId); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      ...// note the code to retreive the push token must run in the background
      InstanceID instanceID= InstanceID.getInstance(getApplicationContext());String token=instanceID.getToken("835015092242", GoogleCloudMessaging.INSTANCE_ID_SCOPE null);Config.setPushIdentifier(token);
      ...
      ```

* **submitAdvertisingIdentifierTask**

   * Biedt een Oproepbaar aan de SDK die de tekenreeks retourneert van de advertentie-id die door Google Play Services is geretourneerd. SDK stelt deze taak op een achtergronddraad in werking en plaatst een interne variabele voor het Advertising Identifier die op de waarde gebaseerd is die van Callable is teruggekeerd.

      >[!IMPORTANT]
      > 
      >Als u de advertentie-id wilt gebruiken in Acquisition of LiveCycle, roept u deze aan voordat u de id aanroept `Config.collectLifecycleData`.

      * Hier volgt de syntaxis voor deze methode:

         ```java
         public static void submitAdvertisingIdentifierTask(final Callable<String> task); 
         ```

      * Hier volgt het codevoorbeeld voor deze methode:

         ```java
         @Override
         public void  onResume() {
             super.onResume();
             final  Callable<String>; task = new Callable<String>(){
                 @Override
                 public String call() throws Exception {
                    AdvertisingIdClient.Info idInfo;
                    String adid = null;
                    Context appContext = CLASSNAME.this.getApplicationContext();
                    try {
                         idInfo = AdvertisingIdClient.getAdvertisingIdInfo(appContext);
                         if (idInfo != null) { 
                             adid = idInfo.getId();
                         } 
                    } catch  (Exception ex) {
                        Log.e("Error",  ex.getLocalizedMessage());
                    }
                    return  adid;
                 }
           };
           Config.submitAdvertisingIdentifierTask(task); 
           Config.collectLifecycleData(this);
         }
         ```


## AdobeDataCallback Interface {#section_600A63B3136F47DCB928071485C5117C}

```java
public interface AdobeDataCallback {  
    void call(MobileDataEvent event, Map<String, Object> contextData);  
} 
```

## MobileDataEvent Enum {#section_92732814141646E294782BC9020367EB}

```java
public enum MobileDataEvent {  
    MobileDataEvent.MOBILE_EVENT_LIFECYCLE, // triggers on a lifecycle hit  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL, // triggers on a app install that has acquisition data  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH // triggers on launch when the device previously installed via acquisition  
}
```
