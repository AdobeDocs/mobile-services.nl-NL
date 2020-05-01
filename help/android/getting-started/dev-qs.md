---
description: Met deze informatie kunt u de Android-bibliotheek implementeren en levenscyclusmetriek verzamelen, zoals opstarten, upgrades, sessies, betrokken gebruikers, enzovoort.
keywords: android;library;mobile;sdk
seo-description: Met deze informatie kunt u de Android-bibliotheek implementeren en levenscyclusmetriek verzamelen, zoals opstarten, upgrades, sessies, betrokken gebruikers, enzovoort.
seo-title: Core-implementatie en levenscyclus
solution: Marketing Cloud,Analytics
title: Core-implementatie en levenscyclus
topic: Developer and implementation
uuid: af4d11ac-8245-46a0-9b3a-4a0a29cfbbb2
translation-type: tm+mt
source-git-commit: dae60a21286edc28c84b7638da214b824abf0cd3

---


# Kernimplementatie en levenscyclus {#core-implementation-and-lifecycle}

Met deze informatie kunt u de Android-bibliotheek implementeren en levenscyclusmetriek verzamelen, zoals opstarten, upgrades, sessies, betrokken gebruikers, enzovoort.

## De SDK downloaden {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>Als u de SDK wilt downloaden, moet u Android 2.2 of hoger gebruiken.

1. Voer de stappen in de volgende secties uit om een ontwikkelrapport in te stellen en een vooraf ingevulde versie van het configuratiebestand te downloaden:

   * [Een rapportsuite maken](/help/android/getting-started/requirements.md)
   * [De SDK downloaden](/help/android/getting-started/requirements.md)

1. Download en decomprimeer het `[Your_App_Name_]AdobeMobileLibrary-4.*-Android.zip` bestand en controleer of de volgende softwarecomponenten bestaan:

   * `adobeMobileLibrary.jar`, de bibliotheek die wordt gebruikt met Android-apparaten en -simulatoren.

   * `ADBMobileConfig.json`, dit is het SDK-configuratiebestand dat voor uw app is aangepast.
   >[!IMPORTANT]
   >
   >Als u de SDK buiten de gebruikersinterface van Adobe Mobile-services downloadt, moet het `ADBMobileConfig.json` bestand handmatig worden geconfigureerd. Zie [Voor u begint](/help/android/getting-started/requirements.md)als u nog niet eerder met Analytics en de Mobile SDK werkt en u een ontwikkelrapport wilt instellen en een vooraf ingevulde versie van het configuratiebestand wilt downloaden.

## Voeg SDK en config dossier aan uw IDEA of project van de Verduistering toe IntelliJ {#section_B89510FBB4C646AEA73A185B966E54D3}

**IntelliJ IDEA-project**

Om SDK en config dossier aan uw project toe te voegen:

1. Voeg het `ADBMobileConfig.json` bestand toe aan de `assets` map in uw project.

1. Klik met de rechtermuisknop op het project in het navigatievenster voor het project.
1. Selecteer Instellingen **[!UICONTROL van module]** Openen.
1. Selecteer onder **[!UICONTROL Projectinstellingen]** de optie **[!UICONTROL Bibliotheken]**.
1. Klik op het pictogram **[!UICONTROL +]** om een nieuwe bibliotheek toe te voegen.
1. Selecteer **[!UICONTROL Java]** en navigeer naar het `adobeMobileLibrary.jar` bestand.
1. Selecteer de modules waar u de mobiele bibliotheek wilt gebruiken.
1. Click **[!UICONTROL Apply]** and **[!UICONTROL OK]** to close the Module Settings window.

**Eclipse-project**

Om SDK en config dossier aan uw project toe te voegen:

1. Voeg het `ADBMobileConfig.json` bestand toe aan de `assets` map in uw project.
1. In **[!UICONTROL winde]** Eclipse, klik de projectnaam met de rechtermuisknop aan.
1. Klik op **[!UICONTROL Pad]** samenstellen > Externe archieven **[!UICONTROL toevoegen]**.
1. Selecteer `adobeMobileLibrary.jar`.
1. Klik op **[!UICONTROL Openen]**.
1. Klik nogmaals met de rechtermuisknop op het project en selecteer **[!UICONTROL Pad]** samenstellen > **[!UICONTROL Pad]** samenstellen configureren.
1. Controleer of op het tabblad **[!UICONTROL Volgorde en Exporteren]** **`adobeMobileLibrary.jar`** is geselecteerd.

## Toepassingsmachtigingen toevoegen {#section_2EAF73ABF6424647B219A63B33B02CD5}

De bibliotheek AppMeturement vereist de volgende toestemmingen om gegevens te verzenden en offline het volgen vraag op te nemen:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

U voegt deze machtigingen toe door de volgende regels toe te voegen aan het `AndroidManifest.xml` bestand dat zich in de projectmap van de toepassing bevindt:

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

## De toepassingscontext instellen {#set-application-context}

De volgende code moet worden toegevoegd aan de `onCreate` methode van uw hoofdactiviteit:

```java
   @Override
   public void onCreate(BundlesavedInstanceState){
     super.onCreate(savedInstanceState)
     setContentView(R.layout.main);
     Config.setContext(this.getApplicationContext());
   }
```

## Levenscyclusmetriek implementeren {#section_BA686C09021F474AADDE8690BBB910F7}

Nadat u de levenscyclus hebt ingeschakeld, wordt elke keer dat uw app wordt gestart, een hit verzonden om het starten, upgrades, sessies, betrokken gebruikers en vele andere metingen te meten. Zie [Levenscyclusstatistieken](/help/android/metrics.md)voor meer informatie.

**Voer de volgende stappen uit in elke activiteit van uw toepassing:**

1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. Start in de `onResume` functie de levenscyclusgegevensverzameling:

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
       // -or- Config.collectLifecycleData(this, contextData); 
   }
   ```

1. In de `onPause` functie pauzeert u de levenscyclusgegevensverzameling:

   ```java
   @Override 
   public void onPause() { 
       Config.pauseCollectingLifecycleData(); 
   }
   ```

>[!IMPORTANT]
>
>U moet deze vraag aan elke activiteit toevoegen om nauwkeurige neerstortingsrapportering te verzekeren. Zie App Crashes [bijhouden voor meer informatie](/help/android/analytics-main/crashes.md).

## Extra gegevens opnemen met levenscyclusaanroepen

Om extra gegevens met metrische vraag van de levenscyclus te omvatten, ga een extra parameter tot over `collectLifecycleData` die contextgegevens bevat:

```java
@Override 
public void onResume() {
    HashMap<String, Object> contextData = new HashMap<String, Object>(); 
    contextData.put("myapp.category", "Game"); 
    Config.collectLifecycleData(this, contextData); 
}
```

Aanvullende waarden voor contextgegevens die worden verzonden met, `collectLifecycleData` moeten worden toegewezen aan aangepaste variabelen in Adobe Mobile-services:

![](assets/map-variable-lifecycle.png)

Andere levenscyclusmetriek worden automatisch verzameld. Zie [Levenscyclusstatistieken](/help/android/metrics.md)voor meer informatie.

## Volgende handelingen {#section_BF709684E1DD40EA9169BC1D0D4B37C2}

Voer de volgende taken uit:

* [App-statussen bijhouden](/help/android/analytics-main/states.md)
* [App-acties bijhouden](/help/android/analytics-main/actions.md)

