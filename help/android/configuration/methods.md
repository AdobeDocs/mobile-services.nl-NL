---
description: Hier volgt een lijst met methoden die worden geleverd door de Android-bibliotheek.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Configuratiemethoden
topic-fix: Developer and implementation
uuid: 663aeb6c-1b97-4a3a-8c0e-dd4c2ec28c01
exl-id: f35b9d32-f967-42e9-bd00-ad85f3bd6bc4
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 23%

---

# Configuratiemethoden{#configuration-methods}

Hier volgt een lijst met methoden die worden geleverd door de Android-bibliotheek.

## Initiële configuratie {#section_9169243ECC4744A899A8271F92090ECD}

De volgende methode moet eenmaal worden aangeroepen in het dialoogvenster `onCreate` methode van uw hoofdactiviteit:

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

   * Hiermee wordt een object geregistreerd dat het `AdobeDataCallback` interface. De overschreven methode &quot;call&quot; wordt aangeroepen met een `Config.MobileDataEvent` en de bijbehorende gegevens in een `Map<String, Object>` voor de activeringsgebeurtenis. Voor meer informatie over welke gebeurtenissen deze callback zullen teweegbrengen, zie *MobileDataEventEnum* onder aan dit onderwerp.

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

         Als de tijdstempel van uw rapportsuite niet is ingeschakeld, worden treffers verwijderd totdat de privacystatus verandert en u zich aanmeldt. De standaardwaarde wordt ingesteld in het dialoogvenster `ADBMobileConfig.json` bestand.
   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static MobilePrivacyStatus getPrivacyStatus(); 
      ```

   * Hier volgt een codevoorbeeld voor deze methode:

      ```java
      MobilePrivacyStatus privacyStatus Config.getPrivacyStatus();
      ```


* **setPrivacyStatus**

   * Hiermee wordt de privacystatus voor de huidige gebruiker ingesteld op `status`.

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

   * Hiermee wordt de gebruikersnaam ingesteld op `identifier`.
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
   * Hiermee wordt de voorkeur voor foutopsporing ingesteld op `debugLogging`.
   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void setDebugLogging(Boolea debugLogging);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Config.setDebugLogging(true);
      ```

* **collectionLifecycleData**
   * Geeft aan de SDK aan dat levenscyclusgegevens moeten worden verzameld voor gebruik in alle oplossingen in de SDK. Zie voor meer informatie [Levenscycluscijfers](/help/android/configuration/methods.md).

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

   * (**Versie 4.2 of hoger**) Geeft aan de SDK aan dat levenscyclusgegevens moeten worden verzameld voor gebruik in alle oplossingen in de SDK. Zie voor meer informatie [Levenscycluscijfers](/help/android/metrics.md).
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

   * Geeft aan de SDK aan dat de app is gepauzeerd, zodat de levenscycluswaarden correct worden berekend. Bijvoorbeeld: `onPause` Hiermee wordt een tijdstempel verzameld om de lengte van de vorige sessie te bepalen. Hierdoor wordt ook een vlag ingesteld zodat de levenscyclus weet dat de app niet vastloopt. Zie voor meer informatie [Levenscycluscijfers](/help/android/metrics.md).

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

   * (**Versie 4.2 of hoger**) Hiermee stelt u het kleine pictogram in dat wordt gebruikt voor meldingen die door de SDK zijn gemaakt. Dit pictogram wordt weergegeven op de statusbalk en is de secundaire afbeelding die wordt weergegeven wanneer de gebruiker het volledige bericht ziet in het meldingscentrum.
   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **setLargeIconResourceId(int resourceId)**

   * (**Versie 4.2 of hoger**) Hiermee stelt u het grote pictogram in dat wordt gebruikt voor meldingen die door de SDK zijn gemaakt. Dit pictogram is de primaire afbeelding die wordt weergegeven wanneer de gebruiker de volledige melding in het meldingscentrum ziet.
   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void setLargeIconResourceId(final int  resourceId);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```Java
      Config.setLargeIconResourceId(R.drawable.appIcon);
      ```

* **overrideConfigStream(InputStream configInput)**

   * (**Versie 4.2 of hoger**) Hiermee kunt u een ander JSON-configuratiebestand voor ADBMobile laden wanneer de toepassing wordt gestart. De verschillende configuratie wordt gebruikt tot de toepassing wordt gesloten.
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

   * Verstrekt Oproepbaar aan SDK die het koord van Advertising Identifier terugkeert dat van de Diensten van Google Play is teruggekeerd. SDK stelt deze taak op een achtergronddraad in werking en plaatst een interne variabele voor het Advertising Identifier die op de waarde gebaseerd is die van Callable is teruggekeerd.

      >[!IMPORTANT]
      > 
      >Als u de advertentie-id wilt gebruiken in Acquisition of LiveCycle, roept u deze aan voordat u de `Config.collectLifecycleData`.

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
