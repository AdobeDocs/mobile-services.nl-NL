---
description: Hier volgt een lijst met Adobe Analytics-methoden die worden geleverd door de Android-bibliotheek.
keywords: android;library;mobile;sdk
seo-description: Hier volgt een lijst met Adobe Analytics-methoden die worden geleverd door de Android-bibliotheek.
seo-title: Analysemethoden
solution: Marketing Cloud,Analytics
title: Analysemethoden
topic: Developer and implementation
uuid: ac7c640e-9dcc-4724-b561-019cc025d5a7
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 28%

---


# Analysemethoden {#analytics-methods}

Hier volgt een lijst met Adobe Analytics-methoden die worden geleverd door de Android-bibliotheek.

De SDK biedt momenteel ondersteuning voor meerdere Adobe Experience Cloud-oplossingen [waaronder Analytics], Target], Audience Manager] en Adobe Experience Platform Identity Service]. Methoden worden vooraf ingesteld op basis van de oplossing, waarbij de methoden Experience Cloud ID bijvoorbeeld vooraf zijn ingesteld `analytics`.

Elk van de volgende methoden wordt gebruikt om gegevens naar uw Adobe Analytics-rapportenpakket te verzenden:

* **trackState**

   Traceert een toepassingsstatus met optionele contextgegevens. Frames zijn de weergaven die beschikbaar zijn in uw app, zoals `home dashboard`, `app settings`, `cart`enzovoort. Deze staten zijn vergelijkbaar met pagina&#39;s op een website en `trackState` roepen paginaweergaven met meer pagina&#39;s aan.

   Als `state` het leeg is, wordt `app name app version (build)` getoond in rapporten. Als u deze waarde in rapporten ziet, zorg ervoor dat u `state` in elke `trackState` vraag plaatst.

   >[!TIP]
   >
   >Dit is de enige volgende vraag die de paginameningen verhoogt.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void trackState(String state, Map<String, Object> contextData);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Analytics.trackState("loginScreen", null);
      ```

* **trackAction** volgt een handeling in uw app.

   Handelingen die u wilt meten, zoals `logons`, `banner taps`, `feed subscriptions`en andere metriek, die in uw app voorkomen.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void trackAction(String state, Map<String, Object> contextData);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Analytics.trackAction("heroBannerTouched", null);
      ```

* **getTrackingIdentifier** retourneert de automatisch gegenereerde bezoeker-id voor Analytics.

   Dit is een app-specifieke, unieke bezoekersidentiteitskaart die bij de aanvankelijke lancering wordt geproduceerd en van dat punt vooruit wordt opgeslagen en gebruikt. De id blijft behouden tussen upgrades van apps en wordt verwijderd wanneer de app wordt verwijderd.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static String getTrackingIdentifier();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      String trackingId = Analytics.getTrackingIdentifier();
      ```

* **trackLocation**

   Verzendt de huidige breedtegraad, lengtegraad en locatie naar een bepaald belangenpunt. Zie [Geo-locatie en aandachtspunten](/help/android/location/geo-poi.md)voor meer informatie.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void trackLocation(Location location, Map<String, Object> contextData);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Analytics.trackLocation(userLocation, null);
      ```

* **trackLifetime &#x200B; ValueIncrease**

   Hiermee voegt u `amount` de levensduurwaarde van de gebruiker toe.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void trackLifetimeValueIncrease(BigDecimal amount, Map<String, Object> contextData);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Analytics.trackLifetimeValueIncrease(new BigDecimal(30), null);
      ```

* **trackTimed &#x200B; ActionStart**

   Start een getimede actie met naam `action`.

   Als u deze methode aanroept voor een actie die al is gestart, wordt de vorige getimede actie overschreven.

   >[!TIP]
   >
   >Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

   ```java
   public static void trackTimedActionStart(String action, Map<String, Object> contextData);
   ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Analytics.trackTimedActionStart("cartToCheckout", null)
      ```


* **trackTimed &#x200B; ActionUpdate**

   Geef door `contextData` om de contextgegevens bij te werken die aan de `action`koppeling zijn gekoppeld. De ingevoerde `data` code wordt toegevoegd aan de bestaande gegevens voor de actie en als dezelfde sleutel al is gedefinieerd voor `action`, worden de gegevens overschreven.

   >[!TIP]
   >
   >Deze aanvraag verzendt geen treffer.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void trackTimedActionUpdate(String action, Map<String, Object> contextData);
      ```

   * Hier volgt een codevoorbeeld voor deze methode:

      ```java
      HashMap cdata = new HashMap<String Object> ();
      cdata.put("quantity",3);
      Analytics.trackTimedActionUpdate("cartToCheckout", cdata);
      ```

* **trackTimed &#x200B; ActionEnd**

   Een getimede actie beëindigen. Als u `block`dat opgeeft, hebt u toegang tot de uiteindelijke tijdwaarden en kunt u dit manipuleren `data` voordat u de laatste hit verzendt.

   >[!TIP]
   >
   >Als u `block`dat opgeeft, moet u terugkeren `true` om een hit te verzenden. Als u `null` `block` voor gaat, wordt de laatste treffer verzonden.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void trackTimedActionEnd(String action, TimedActionBlock<Boolean> logic);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Analytics.trackTimedActionEnd("cartToCheckout",new
      Analytics.TimedActionBlock<Boolean>(){
          @Override
          public Boolean call(long inAppDuration, long totalDuration, Map<String, Object> contextData) {
              contextData.put("price", 49.95);
              return true;
          }
      });
      ```

* **sendQueuedHits**

   **Vereist SDK 4.1.**

   Ongeacht het aantal treffers in een wachtrij, dwingt deze methode de bibliotheek alle treffers in de offline wachtrij te verzenden.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void sendQueuedHits();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Analytics.sendQueuedHits();
      ```

* **getQueueSize**

   Keert het aantal opgeslagen het volgen vraag in de off-line rij terug.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static long getQueueSize();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      long queueSize = Analytics.getQueueSize();
      ```

* **clearQueue**

   Wist alle treffers van de off-line rij.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void clearQueue();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Analytics.clearQueue();
      ```

      >[!WARNING]
      >
      > Wees voorzichtig wanneer u de wachtrij handmatig wist. Dit proces kan niet ongedaan worden gemaakt.

* **processReferrer**

   Verwerkt campagnegegevens van de referentie van de Google Play Store voor later gebruik.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void processReferrer(final Context context, final Intent intent);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Analytics.processReferrer(getApplicationContext(), intent);
      ```

* **processGooglePlayInstallReferrerUrl**

   >[!IMPORTANT]
   >
   > Deze API is beschikbaar vanaf SDK versie 4.18.0

   Hiermee worden acquisitiegegevens opgehaald via de opgegeven URL van de Google Play-installatieverwijzing.

   De gegevens die via deze API worden verzameld, worden verzonden bij installatieaanvragen die naar Analytics worden verzonden en zijn beschikbaar in de Adobe Data Callback.

   Als de SDK de referentiegegevens al heeft verzameld, resulteert het aanroepen van deze methode in een no-op.

   Raadpleeg de documentatie bij Google voor informatie over het ophalen van de referentie-URL: https://developer.android.com/google/play/installreferrer/library.

   * Hier volgt de syntaxis voor deze methode:

      ```java
      public static void processGooglePlayInstallReferrerUrl(final String referrerUrl);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```java
      Analytics.processGooglePlayInstallReferrerUrl(referrerUrl);
      ```
