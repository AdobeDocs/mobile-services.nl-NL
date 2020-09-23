---
description: Met deze informatie kunt u de Android-bibliotheek implementeren en levenscyclusmetriek verzamelen, zoals opstarten, upgrades, sessies, betrokken gebruikers, enzovoort.
keywords: android;library;mobile;sdk
seo-description: Met deze informatie kunt u de Android-bibliotheek implementeren en levenscyclusmetriek verzamelen, zoals opstarten, upgrades, sessies, betrokken gebruikers, enzovoort.
seo-title: Core-implementatie en levenscyclus
solution: Experience Cloud,Analytics
title: Core-implementatie en levenscyclus
topic: Developer and implementation
uuid: af4d11ac-8245-46a0-9b3a-4a0a29cfbbb2
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 2%

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
   >Als u de SDK buiten de gebruikersinterface van de Adobe Mobile-services downloadt, moet het `ADBMobileConfig.json` bestand handmatig worden geconfigureerd. Zie [Voor u begint](/help/android/getting-started/requirements.md)als u nog niet eerder met Analytics en de Mobile SDK werkt en u een ontwikkelrapport wilt instellen en een vooraf ingevulde versie van het configuratiebestand wilt downloaden.

## Voeg SDK en config dossier aan uw IDEA of project van de Clipse IntelliJ toe {#section_B89510FBB4C646AEA73A185B966E54D3}

**IntelliJ IDEA-project**

Om SDK en config dossier aan uw project toe te voegen:

1. Voeg het `ADBMobileConfig.json` bestand toe aan de `assets` map in uw project.

1. Klik met de rechtermuisknop op het project in het navigatievenster voor het project.
1. Selecteer **[!UICONTROL Open Module Settings]**.
1. Selecteer onder **[!UICONTROL Project Settings]** de optie **[!UICONTROL Libraries]**.
1. Click the **[!UICONTROL +]** icon to add a new library.
1. Selecteer **[!UICONTROL Java]** en navigeer naar het `adobeMobileLibrary.jar` bestand.
1. Selecteer de modules waar u de mobiele bibliotheek wilt gebruiken.
1. Click **[!UICONTROL Apply]** and **[!UICONTROL OK]** to close the Module Settings window.

**Eclipse-project**

Om SDK en config dossier aan uw project toe te voegen:

1. Voeg het `ADBMobileConfig.json` bestand toe aan de `assets` map in uw project.
1. Klik met de rechtermuisknop op de projectnaam **[!UICONTROL Eclipse IDE]** in.
1. Klik op  **[!UICONTROL Build Path]** > **[!UICONTROL Add External Archives]**.
1. Selecteer `adobeMobileLibrary.jar`.
1. Klik op **[!UICONTROL Open]**.
1. Klik nogmaals met de rechtermuisknop op het project en selecteer **[!UICONTROL Build Path]** > **[!UICONTROL Configure Build Path]**.
1. Controleer of op het **[!UICONTROL Order and Export]** tabblad deze optie **`adobeMobileLibrary.jar`** is geselecteerd.

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

De extra waarden van contextgegevens die met worden verzonden `collectLifecycleData` moeten aan douanevariabelen in de Mobiele diensten van Adobe worden in kaart gebracht:

![](assets/map-variable-lifecycle.png)

Andere levenscyclusmetriek worden automatisch verzameld. Zie [Levenscyclusstatistieken](/help/android/metrics.md)voor meer informatie.

## Volgende handelingen {#section_BF709684E1DD40EA9169BC1D0D4B37C2}

Voer de volgende taken uit:

* [App-statussen bijhouden](/help/android/analytics-main/states.md)
* [App-acties bijhouden](/help/android/analytics-main/actions.md)

