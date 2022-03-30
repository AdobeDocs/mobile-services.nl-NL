---
description: Met deze informatie kunt u de Android-bibliotheek implementeren en levenscyclusmetriek verzamelen, zoals opstarten, upgrades, sessies, betrokken gebruikers, enzovoort.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Core-implementatie en levenscyclus
topic-fix: Developer and implementation
uuid: af4d11ac-8245-46a0-9b3a-4a0a29cfbbb2
exl-id: 67aba85a-42a0-473a-bb05-e5fcb35263d9
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
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

1. Download en decomprimeer de `[Your_App_Name_]AdobeMobileLibrary-4.*-Android.zip` en controleert u of de volgende softwarecomponenten bestaan:

   * `adobeMobileLibrary.jar`, de bibliotheek die wordt gebruikt met Android-apparaten en -simulatoren.

   * `ADBMobileConfig.json`, dit is het SDK-configuratiebestand dat voor uw app is aangepast.
   >[!IMPORTANT]
   >
   >Als u de SDK buiten de gebruikersinterface van de Adobe Mobile-services downloadt, wordt `ADBMobileConfig.json` bestand moet handmatig worden geconfigureerd. Als Analytics en de SDK van Mobile nieuw voor u zijn en u een ontwikkelrapport wilt instellen en een vooraf ingevulde versie van het configuratiebestand wilt downloaden, raadpleegt u [Voordat u begint](/help/android/getting-started/requirements.md).

## Voeg SDK en config dossier aan uw IDEA of project van de Clipse IntelliJ toe {#section_B89510FBB4C646AEA73A185B966E54D3}

**IntelliJ IDEA-project**

Om SDK en config dossier aan uw project toe te voegen:

1. Voeg de `ADBMobileConfig.json` aan de `assets` in uw project.

1. Klik met de rechtermuisknop op het project in het navigatievenster voor het project.
1. Selecteer **[!UICONTROL Open Module Settings]**.
1. Selecteer onder **[!UICONTROL Project Settings]** de optie **[!UICONTROL Libraries]**.
1. Klik op de knop **[!UICONTROL +]** om een nieuwe bibliotheek toe te voegen.
1. Selecteren **[!UICONTROL Java]** en navigeer naar de `adobeMobileLibrary.jar` bestand.
1. Selecteer de modules waar u de mobiele bibliotheek wilt gebruiken.
1. Klikken **[!UICONTROL Apply]** en **[!UICONTROL OK]** om het venster van de Montages van de Module te sluiten.

**Eclipse-project**

Om SDK en config dossier aan uw project toe te voegen:

1. Voeg de `ADBMobileConfig.json` aan de `assets` in uw project.
1. In **[!UICONTROL Eclipse IDE]** klikt u met de rechtermuisknop op de projectnaam.
1. Klik op  **[!UICONTROL Build Path]** > **[!UICONTROL Add External Archives]**.
1. Selecteer `adobeMobileLibrary.jar`.
1. Klik op **[!UICONTROL Open]**.
1. Klik nogmaals met de rechtermuisknop op het project en selecteer **[!UICONTROL Build Path]** > **[!UICONTROL Configure Build Path]**.
1. Op de **[!UICONTROL Order and Export]** -tab, zorg ervoor dat **`adobeMobileLibrary.jar`** is geselecteerd.

## Toepassingsmachtigingen toevoegen {#section_2EAF73ABF6424647B219A63B33B02CD5}

De bibliotheek AppMeturement vereist de volgende toestemmingen om gegevens te verzenden en offline het volgen vraag op te nemen:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

Voeg de volgende regels toe aan uw `AndroidManifest.xml` bestand, dat zich bevindt in de projectmap van de toepassing:

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

Nadat u de levenscyclus hebt ingeschakeld, wordt elke keer dat uw app wordt gestart, een hit verzonden om het starten, upgrades, sessies, betrokken gebruikers en vele andere metingen te meten. Zie voor meer informatie [Levenscycluscijfers](/help/android/metrics.md).

**Voer de volgende stappen uit in elke activiteit van uw toepassing:**

1. De bibliotheek importeren:

   ```java
   import com.adobe.mobile.*;
   ```

1. In de `onResume` functie, start de gegevensverzameling van de levenscyclus:

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
       // -or- Config.collectLifecycleData(this, contextData); 
   }
   ```

1. In de `onPause` functie, onderbreek de gegevensverzameling van de levenscyclus:

   ```java
   @Override 
   public void onPause() { 
       Config.pauseCollectingLifecycleData(); 
   }
   ```

>[!IMPORTANT]
>
>U moet deze vraag aan elke activiteit toevoegen om nauwkeurige neerstortingsrapportering te verzekeren. Zie voor meer informatie [App vastlopen bijhouden](/help/android/analytics-main/crashes.md).

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

Aanvullende contextgegevenswaarden die worden verzonden met `collectLifecycleData` moet worden toegewezen aan aangepaste variabelen in Adobe Mobile-services:

![](assets/map-variable-lifecycle.png)

Andere levenscyclusmetriek worden automatisch verzameld. Zie voor meer informatie [Levenscycluscijfers](/help/android/metrics.md).

## Volgende handelingen {#section_BF709684E1DD40EA9169BC1D0D4B37C2}

Voer de volgende taken uit:

* [App-statussen bijhouden](/help/android/analytics-main/states.md)
* [App-acties bijhouden](/help/android/analytics-main/actions.md)
