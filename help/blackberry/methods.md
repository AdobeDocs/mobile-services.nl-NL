---
description: Klassen en methoden die worden geleverd door de BlackBerry-bibliotheek.
seo-description: Klassen en methoden die worden geleverd door de BlackBerry-bibliotheek.
seo-title: Adobe Mobile-klasse en -methodereferentie
title: Adobe Mobile-klasse en -methodereferentie
uuid: 1e42d759-be43-4bb3-ac1a-c7d64133d61c
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Adobe Mobile-klasse en -methodereferentie {#adobe-mobile-class-and-method-reference}

Klassen en methoden die worden geleverd door de BlackBerry-bibliotheek.

De SDK biedt momenteel ondersteuning voor Adobe Analytics en methoden bevinden zich in aparte klassen op basis van de oplossing.

## SDK-instellingen {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **getPrivacyStatus**

   Retourneert de opsomming van de privacystatus voor de huidige gebruiker.

   * ADBMobilePrivacyStatusOptIn - hits worden direct verzonden.
   * ADBMobilePrivacyStatusOptOut - hits worden genegeerd.
   * ADBMobilePrivacyStatusUnknown - Als uw rapportenreeks timestamp-toegelaten is, worden de klappen bewaard tot de privacystatus in opt-in verandert (dan worden de klappen verzonden) of opt-out (dan worden de klappen verworpen). Als uw rapportsuite niet is ingeschakeld voor tijdstempels, worden treffers genegeerd totdat de privacystatus verandert en u zich aanmeldt.

      De standaardwaarde wordt ingesteld in het `ADBMobileConfig.json` bestand.

   * Hier volgt de syntaxis voor deze methode:

      ```cpp
      static ADBMobilePrivacyStatus getPrivacyStatus();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```cpp
      ADBMobilePrivacyStatus privacyStatus = ADBMobile::getPrivacyStatus();
      ```

* **setPrivacyStatus**

   Hiermee stelt u de privacystatus voor de huidige gebruiker in `status`. Stel een van de volgende waarden in:

   * `ADBMobilePrivacyStatusOptIn` - treffers worden onmiddellijk verzonden.
   * `ADBMobilePrivacyStatusOptOut` - treffers worden genegeerd.
   * `ADBMobilePrivacyStatusUnknown` - Als uw rapportsuite is ingeschakeld voor tijdstempels, worden treffers opgeslagen totdat de status van de privacy verandert in aanmelden (resultaten worden verzonden) of Afmelden (resultaten worden verwijderd). Als uw rapportsuite niet is ingeschakeld voor tijdstempels, worden treffers genegeerd totdat de privacystatus verandert en u zich aanmeldt.

   * Hier volgt de syntaxis voor deze methode:

      ```cpp
      static void setPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```cpp
      ADBMobile::setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```

* **getUserIdentifier**

   Retourneert de gebruikers-id als er een aangepaste id is ingesteld. Retourneert `null` of er geen aangepaste id is ingesteld. De standaardwaarde is `null`.

   * Hier volgt de syntaxis voor deze methode:

      ```cpp
      static QString getUserIdentifier();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```cpp
      QString userId = ADBMobile::getUserIdentifier(); 
      ```

* **setUserIdentifier**

   Hiermee stelt u de gebruikers-id in op `identifier`.

   * Hier volgt de syntaxis voor deze methode:

      ```cpp
      static void setUserIdentifier(QString identifier);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```cpp
      ADBMobile::setUserIdentifier("billybob");
      ```

* **getDebugLogging**

   Retourneert de huidige voorkeur voor foutopsporing. De standaardwaarde is `false`.

   * Hier volgt de syntaxis voor deze methode:

      ```cpp
      static bool getDebugLogging();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```cpp
       bool debugging = ADBMobile::getDebugLogging(); 
      ```

* **setDebugLogging**

   Hiermee stelt u de voorkeur voor foutopsporing in op `debugLogging`.

   * Hier volgt de syntaxis voor deze methode:

      ```cpp
      static void setDebugLogging(bool debugLogging);
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```cpp
        ADBMobile::setDebugLogging(true); 
      ```

* **collectionLifecycleData**

   Geeft aan de SDK aan dat levenscyclusgegevens moeten worden verzameld voor gebruik in alle oplossingen in de SDK. Zie [Levenscyclusstatistieken](/help/blackberry/metrics.md)voor meer informatie.

   * Hier volgt de syntaxis voor deze methode:

      ```cpp
      static void collectLifecycleData();
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```cpp
      ApplicationUI::ApplicationUI(bb::cascades::Application *app):  QObject(app)  { 
      //... 
      ADBMobile::collectLifecycleData(); 
      }
      ```

## Analysemethoden {#section_91F4AD0A045D4E4E8F9A93450503E49E}

Elk van deze methoden wordt gebruikt om gegevens naar uw Adobe Analytics-rapportensuite te verzenden.

* **trackState**

   Traceert een toepassingsstatus met optionele contextgegevens. Frames zijn de weergaven die beschikbaar zijn in uw app, zoals &#39;thuisdashboard&#39;, &#39;app-instellingen&#39;, &#39;winkelwagentje&#39; enzovoort. Deze staten zijn vergelijkbaar met pagina&#39;s op een website en `trackState` roepen paginaweergaven met meer pagina&#39;s aan.

   >[!TIP]
   >
   >Dit is de enige volgende vraag die de paginameningen verhoogt.

   * Hier volgt de syntaxis voor deze methode:

      ```cpp
      static void trackState(QString state, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```cpp
         ADBMobile::trackState("loginScreen", null);
      ```

* **trackAction**

   Tracks an action in your app. Handelingen zijn de dingen die in uw app gebeuren en die u wilt meten, zoals &#39;logons&#39;, &#39;bannertiketten&#39;, &#39;feed-abonnementen&#39; en andere meetwaarden.

   * Hier volgt de syntaxis voor deze methode:

      ```cpp
      static void trackAction(QString action, QHash<QString, QString> contextData = QHash<QString, QString>()); 
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```cpp
        ADBMobile::trackAction("heroBannerTouched", null); 
      ```

* **trackLocation**

   Verzendt de huidige x y-coördinaten. Vervang gebeurtenis door de gebeurtenis die van de abonnee aan BPS wordt ontvangen.

   * Hier volgt de syntaxis voor deze methode:

      ```cpp
      static void trackLocation(bps_event_t *geoEvent, QHash<QString, QString> contextData = QHash<QString, QString> ());
      ```

   * Hier volgt het codevoorbeeld voor deze methode:

      ```cpp
        ADBMobile::trackLocation(event, null);
      ```

## `ADBMobileConfig.json` configuratiebestandsverwijzing {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

Het `ADBMobileConfig.json` bestand moet in de map *assets* worden geplaatst.

* **Rsids**

   (Vereist) Een of meer rapportensuites om analysegegevens te ontvangen. Meerdere rapportsuite-id&#39;s moeten worden gescheiden door komma&#39;s zonder tussenruimte.

   Hier volgt het codevoorbeeld voor deze variabele:

   ```js
   "rsids" : "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2"
   ```

* **server**

   (Vereist). Analyseserver. Deze variabele zou met het serverdomein, zonder een `https://` of `https://` protocolprefix moeten worden bevolkt. Het protocolvoorvoegsel wordt automatisch behandeld door de bibliotheek die op de `ssl` variabele wordt gebaseerd. Als `ssl` `true`dit het geval is, wordt een veilige verbinding gemaakt met deze server. Als `ssl` `false`dit het geval is, wordt een niet-veilige verbinding gemaakt met deze server.

* **charset**

   Definieert de tekenset die u gebruikt voor de gegevens die naar Analytics worden verzonden. De charset wordt gebruikt om binnenkomende gegevens om te zetten in UTF-8 voor opslag en rapportage.

* **ssl**

   Schakelt het verzenden van meetgegevens via SSL (HTTPS) in (`true`) of uit (`false`). De standaardwaarde is `false`.

* **offlineEnabled**

   Wanneer deze optie is ingeschakeld (`true`), worden treffers in de wachtrij geplaatst terwijl het apparaat offline is en later wordt verzonden wanneer het apparaat online is. Uw rapportsuite moet zijn ingeschakeld voor tijdstempels om offline tracering te kunnen gebruiken.

   >[!TIP]
   >
   >Als tijdstempels op uw rapportreeks worden toegelaten, `offlineEnabled` moet *uw* configuratiebezit `true`. als uw rapportreeks niet timestamp toegelaten is, `offlineEnabled` moet *uw* configuratiebezit vals zijn. Als dit niet correct wordt gevormd, zullen de gegevens worden verloren. Neem contact op met de [Enterprise Support](https://helpx.adobe.com/contact/enterprise-support.ec.html)als u niet zeker weet of een rapportensuite met tijdstempel is ingeschakeld.

   Als u momenteel AppMeasurement-gegevens rapporteert aan een rapportsuite die ook gegevens uit JavaScript verzamelt, moet u mogelijk een aparte rapportsuite voor mobiele gegevens instellen of een aangepaste tijdstempel opnemen voor alle JavaScript-treffers die de `s.timestamp` variabele gebruiken.

   De standaardwaarde is `false`.

* **lifecycleTimeout**

   Hiermee geeft u de tijdsduur in seconden op die moet verstrijken tussen het starten van de app voordat de start als een nieuwe sessie wordt beschouwd. Deze time-out is ook van toepassing wanneer uw toepassing naar de achtergrond wordt verzonden en opnieuw wordt geactiveerd. De tijd die uw toepassing op de achtergrond doorbrengt, wordt niet opgenomen in de sessieduur.

   De standaardwaarde is 300 seconden.

* **batchLimit**

   Maximumaantal offline treffers dat in de wachtrij is opgeslagen. De standaardwaarde is 0 (Geen limiet).

* **privacyDefault**

   * `optedin` - treffers worden onmiddellijk verzonden.
   * `optedout` - treffers worden genegeerd.
   * `optunknown` - Als uw rapportsuite is ingeschakeld voor tijdstempels, worden treffers opgeslagen totdat de status van de privacy verandert in aanmelden (resultaten worden verzonden) of Afmelden (resultaten worden verwijderd).

      Als uw rapportsuite niet is ingeschakeld voor tijdstempels, worden treffers genegeerd totdat de privacystatus verandert en u zich aanmeldt.
   Met deze variabele wordt alleen de beginwaarde ingesteld. Als deze waarde ooit in code wordt geplaatst of veranderd, dan wordt de nieuwe waarde gebruikt door:gaan tot het wordt veranderd, of de app wordt verwijderd en dan opnieuw geïnstalleerd.

   De standaardwaarde is `optedin`.

Hieronder ziet u een voorbeeld van een `ADBMobileConfig.json` bestand:

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 5, 
        "privacyDefault" : "optedin", 
    } 
}
```
