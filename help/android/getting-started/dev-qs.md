---
description: Met deze informatie kunt u de Android-bibliotheek implementeren en levenscyclusmetriek verzamelen, zoals opstarten, upgrades, sessies, betrokken gebruikers, enzovoort.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud,Analytics
title: Core-implementatie en levenscyclus
topic-fix: Developer and implementation
uuid: af4d11ac-8245-46a0-9b3a-4a0a29cfbbb2
exl-id: 67aba85a-42a0-473a-bb05-e5fcb35263d9
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '513'
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

1. Download en decomprimeer het `[Your_App_Name_]AdobeMobileLibrary-4.*-Android.zip`-bestand en controleer of de volgende softwarecomponenten bestaan:

   * `adobeMobileLibrary.jar`, de bibliotheek die wordt gebruikt met Android-apparaten en -simulatoren.

   * `ADBMobileConfig.json`, dit is het SDK-configuratiebestand dat voor uw app is aangepast.
   >[!IMPORTANT]
   >
   >Als u de SDK buiten de gebruikersinterface van de mobiele services van Adobe downloadt, moet het `ADBMobileConfig.json`-bestand handmatig worden geconfigureerd. Als u aan Analytics en Mobiele SDK nieuw bent, en u een reeks van het ontwikkelingsrapport wilt opstelling en een pre-bevolkte versie van het configuratiedossier downloaden, zie [Voor u ](/help/android/getting-started/requirements.md) begint.

## Voeg SDK en config dossier aan uw IDEA of project van de Clipse IntelliJ toe {#section_B89510FBB4C646AEA73A185B966E54D3}

**IntelliJ IDEA-project**

Om SDK en config dossier aan uw project toe te voegen:

1. Voeg het `ADBMobileConfig.json` dossier aan `assets` omslag in uw project toe.

1. Klik met de rechtermuisknop op het project in het navigatievenster voor het project.
1. Selecteer **[!UICONTROL Open Module Settings]**.
1. Selecteer onder **[!UICONTROL Project Settings]** de optie **[!UICONTROL Libraries]**.
1. Klik op het pictogram **[!UICONTROL +]** om een nieuwe bibliotheek toe te voegen.
1. Selecteer **[!UICONTROL Java]** en navigeer aan het `adobeMobileLibrary.jar` dossier.
1. Selecteer de modules waar u de mobiele bibliotheek wilt gebruiken.
1. Klik **[!UICONTROL Apply]** en **[!UICONTROL OK]** om het venster van de Montages van de Module te sluiten.

**Eclipse-project**

Om SDK en config dossier aan uw project toe te voegen:

1. Voeg het `ADBMobileConfig.json` dossier aan `assets` omslag in uw project toe.
1. Klik in **[!UICONTROL Eclipse IDE]** met de rechtermuisknop op de projectnaam.
1. Klik op  **[!UICONTROL Build Path]** > **[!UICONTROL Add External Archives]**.
1. Selecteer `adobeMobileLibrary.jar`.
1. Klik op **[!UICONTROL Open]**.
1. Klik nogmaals met de rechtermuisknop op het project en selecteer **[!UICONTROL Build Path]** > **[!UICONTROL Configure Build Path]**.
1. Controleer op het tabblad **[!UICONTROL Order and Export]** of **`adobeMobileLibrary.jar`** is geselecteerd.

## Toepassingsmachtigingen toevoegen {#section_2EAF73ABF6424647B219A63B33B02CD5}

De bibliotheek AppMeturement vereist de volgende toestemmingen om gegevens te verzenden en offline het volgen vraag op te nemen:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

Om deze toestemmingen toe te voegen, voeg de volgende lijnen aan uw `AndroidManifest.xml` dossier toe, dat in de folder van het toepassingsproject wordt gevestigd:

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

## De toepassingscontext instellen {#set-application-context}

De volgende code moet worden toegevoegd aan de methode `onCreate` van uw hoofdactiviteit:

```java
   @Override
   public void onCreate(BundlesavedInstanceState){
     super.onCreate(savedInstanceState)
     setContentView(R.layout.main);
     Config.setContext(this.getApplicationContext());
   }
```

## Levenscyclusmetriek implementeren {#section_BA686C09021F474AADDE8690BBB910F7}

Nadat u de levenscyclus hebt ingeschakeld, wordt elke keer dat uw app wordt gestart, een hit verzonden om het starten, upgrades, sessies, betrokken gebruikers en vele andere metingen te meten. Zie [Levenscyclusmetriek](/help/android/metrics.md) voor meer informatie.

**Voer de volgende stappen uit in elke activiteit van uw toepassing:**

1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. Start in de functie `onResume` de levenscyclusgegevensverzameling:

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
       // -or- Config.collectLifecycleData(this, contextData); 
   }
   ```

1. In de functie `onPause` pauzeert u de levenscyclusgegevensverzameling:

   ```java
   @Override 
   public void onPause() { 
       Config.pauseCollectingLifecycleData(); 
   }
   ```

>[!IMPORTANT]
>
>U moet deze vraag aan elke activiteit toevoegen om nauwkeurige neerstortingsrapportering te verzekeren. Zie [App Crashes bijhouden](/help/android/analytics-main/crashes.md) voor meer informatie.

## Extra gegevens opnemen met levenscyclusaanroepen

Om extra gegevens met metrische vraag van de levenscyclus te omvatten, ga een extra parameter tot `collectLifecycleData` over die contextgegevens bevat:

```java
@Override 
public void onResume() {
    HashMap<String, Object> contextData = new HashMap<String, Object>(); 
    contextData.put("myapp.category", "Game"); 
    Config.collectLifecycleData(this, contextData); 
}
```

De extra waarden van contextgegevens die met `collectLifecycleData` worden verzonden moeten aan douanevariabelen in de Mobiele diensten van Adobe worden in kaart gebracht:

![](assets/map-variable-lifecycle.png)

Andere levenscyclusmetriek worden automatisch verzameld. Zie [Levenscyclusmetriek](/help/android/metrics.md) voor meer informatie.

## Volgende handelingen {#section_BF709684E1DD40EA9169BC1D0D4B37C2}

Voer de volgende taken uit:

* [App-statussen bijhouden](/help/android/analytics-main/states.md)
* [App-acties bijhouden](/help/android/analytics-main/actions.md)
