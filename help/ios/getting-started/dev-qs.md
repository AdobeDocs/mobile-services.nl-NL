---
description: Met deze informatie kunt u de iOS-bibliotheek implementeren en levenscyclusmetriek verzamelen, zoals opstarten, upgrades, sessies, betrokken gebruikers enzovoort.
solution: Experience Cloud Services,Analytics
title: Core-implementatie en levenscyclus
topic-fix: Developer and implementation
uuid: 96d06325-e424-4770-8659-4b5431318ee3
exl-id: 5fb2d534-c2e8-480a-aaee-0e71dd55feb6
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 1%

---

# Kernimplementatie en levenscyclus {#core-implementation-and-lifecycle}

Met deze informatie kunt u de iOS-bibliotheek implementeren en levenscyclusmetriek verzamelen, zoals opstarten, upgrades, sessies, betrokken gebruikers enzovoort.

## De SDK downloaden {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>Voor de SDK is iOS 8 of hoger vereist.

**Voorwaarde**

Voordat u de SDK downloadt, voert u de stappen uit in *Een rapportsuite maken* in [Kernimplementatie en levenscyclus](/help/ios/getting-started/requirements.md) een ontwikkelrapport instellen en een vooraf ingevulde versie van het configuratiebestand downloaden.

De SDK downloaden:

>[!IMPORTANT]
>
>Vanaf versie 4.21.0 wordt de SDK gedistribueerd via XCFrameworks. Volg onderstaande stappen als u 4.21.0 of hoger gebruikt.
>
>Versie 4.21.0 van de SDK vereist Xcode 12.0 of hoger en, indien van toepassing, Cocoapods 1.10.0 of hoger.

1. Downloaden, decomprimeer de `[Your_App_Name_]AdobeMobileLibrary-4.*-iOS.zip` en controleert u of de volgende softwarecomponenten in de `AdobeMobileLibrary` map:

   * `ADBMobile.h` - het objectc-headerbestand dat wordt gebruikt voor iOS SDK.
   * `ADBMobileConfig.json` - het SDK-configuratiebestand dat voor uw app is aangepast.
   * `AdobeMobile.xcframework` - bevat twee vetbinaire getallen, elk voor iOS-apparaten (armv7, armv7, arm64) en simulatoren (i386, x86_64, arm64).

      Dit XCF-kader moet worden gekoppeld wanneer u een iOS-app als doel instelt.

   * `AdobeMobileExtension.xcframework` - bevat twee vetbinaire getallen, elk voor iOS-apparaten (armv7, armv7, arm64) en simulatoren (i386, x86_64, arm64).

      Dit XCFFramework moet worden gekoppeld wanneer een iOS-extensie als doel wordt ingesteld.

   * `AdobeMobileWatch.xcframework` - bevat twee vetbinaire getallen, elk voor watchOS-apparaten (arm64_32, armv7k) en simulatoren (i386, x86_64, arm64).

      Dit XCFFramework moet worden gekoppeld wanneer u zich richt op een Apple Watch (watchOS)-app.

   * `AdobeMobileTV.xcframework` - bevat twee vetbinaire getallen, elk voor tvOS-apparaten (arm64) en simulatoren (x86_64, arm64).

      Dit XCF-framework moet worden gekoppeld wanneer het programma is gericht op een Apple TV-app (tvOS).

>[!IMPORTANT]
>
>In versies ouder dan 4.21.0, wordt SDK verdeeld via binaire getallen. Voer de onderstaande stappen uit als u een versie ouder dan 4.21.0 gebruikt.

1. Downloaden, decomprimeer de `[Your_App_Name_]AdobeMobileLibrary-4.*-iOS.zip` en controleer of u over de volgende softwareonderdelen beschikt:

   * `ADBMobile.h`, het objectc-headerbestand dat wordt gebruikt voor iOS AppMeasurement.
   * `ADBMobileConfig.json`, dit is het SDK-configuratiebestand dat voor uw app is aangepast.
   * `AdobeMobileLibrary.a`, een binaire bitcode met vet die de bibliotheekbuilds voor iOS-apparaten bevat (armv7, armv7s, arm64) en simulatoren (i386, x86_64).

      Dit binaire getal met vet moet worden gekoppeld wanneer het doel is bedoeld voor een iOS-app.

   * `AdobeMobileLibrary_Extension.a`, een binaire bitcode met vet die de bibliotheekbuilds bevat voor iOS-apparaten (armv7, armv7s, arm64) en simulatoren (i386, x86_64).

      Dit binaire vetweefsel moet worden gekoppeld wanneer het doel is bedoeld voor een iOS-extensie.

   * `AdobeMobileLibrary_Watch.a`, een binaire bitcode met vet die de bibliotheekbuilds voor Apple Watch devices (armv7k) en simulators bevat (i386, x86_64).

      Dit binaire bestand met vet moet worden gekoppeld wanneer het doel is bedoeld voor een Apple Watch-app (watchOS 2).

   * `AdobeMobileLibrary_TV.a`, een binaire bitcode met vet die de bibliotheek bevat voor nieuwe Apple TV-apparaten (arm64) en simulator (x86_64).

      Dit binaire bestand met vet moet worden gekoppeld wanneer het doel is bedoeld voor een Apple TV-app (tvOS).

>[!IMPORTANT]
>
>Als u de SDK buiten de gebruikersinterface van de Adobe Mobile-services downloadt, wordt `ADBMobileConfig.json` bestand moet handmatig worden geconfigureerd. Als u nog niet eerder met Analytics en de Mobile SDK hebt gewerkt, raadpleegt u [Voordat u begint](/help/ios/getting-started/requirements.md) een ontwikkelrapport instellen en een vooraf ingevulde versie van het configuratiebestand downloaden.

## SDK en configuratiebestand toevoegen aan uw project {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Start de Xcode-IDE en open uw app.
1. In de Navigator van het Project, sleep `AdobeMobileLibrary` en zet deze onder uw project neer.
1. Controleer het volgende:

   * De **[!UICONTROL Copy Items if needed]** selectievakje is ingeschakeld.
   * **[!UICONTROL Create groups]** is geselecteerd.
   * Geen enkel selectievakje in het dialoogvenster **[!UICONTROL Add to targets]** is geselecteerd.

   ![](assets/step_3.png)

1. Klik op **[!UICONTROL Finish]**.
1. In **[!UICONTROL Project Navigator]** selecteert u **`ADBMobileConfig.json`**.
1. In **[!UICONTROL File Inspector]** voegt u het JSON-bestand toe aan de doelen in uw project die de Adobe SDK gebruiken.

   ![](assets/step_4.png)

1. In **[!UICONTROL Project Navigator]** Voer de volgende stappen uit:

   1. Klik op uw app.
   1. Op de **[!UICONTROL General]** selecteert u de gewenste doelen en koppelt u de vereiste frameworks en bibliotheken in het dialoogvenster **[!UICONTROL Linked Frameworks]** en **[!UICONTROL Libraries]** secties.
   * **iOS App-doelen**
      * `SystemConfiguration.framework`
      * `WebKit.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary.a`
      * `CoreLocation.framework` (optioneel, maar vereist voor geo-tracking-mogelijkheden)
   * **iOS Extension Target**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Extension.a`
   * **Apple Watch (watchOS 2) Target**

      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Watch.a`
   * **Doel Apple TV (tvOS)**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_TV.a`

   >[!CAUTION]
   >
   > Meer dan één koppeling `AdobeMobileLibrary*.a` bestand in hetzelfde doel heeft onverwacht gedrag of kan niet worden gemaakt.

   >[!IMPORTANT]
   >
   > Als u versie 4.21.0 of hoger gebruikt, moet u ervoor zorgen dat de Adobe XCFrameworks niet zijn ingesloten.

   ![](assets/no-embed.png)

1. Bevestig dat uw app zonder fouten wordt gemaakt.

## Levenscyclusmetriek implementeren {#section_532702562A7A43809407C9A2CBA80E1E}

>[!IMPORTANT]
>
>iOS stuurt levenscyclusinformatie met of zonder dat er contact met `collectlifecycledata`, en `collectlifecycledata` is slechts een manier om eerder in de opstartreeks van de toepassing levenscyclus in werking te stellen.

Nadat u de levenscyclus hebt ingeschakeld, wordt elke keer dat uw app wordt gestart, een hit verzonden om het starten, upgrades, sessies, betrokken gebruikers en andere gebruikers te meten [Levenscycluscijfers](/help/ios/metrics.md).

Voeg een `collectLifecycleData`/ `collectLifecycleDataWithAdditionalData` oproepen binnen `application:didFinishLaunchingWithOptions`:

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
 [ADBMobile collectLifecycleData];
    return YES;
}
```

### Extra gegevens opnemen met levenscyclusaanroepen

Om extra gegevens met metrische vraag van de levenscyclus te omvatten, gebruik `collectLifecycleDataWithAdditionalData`:

>[!IMPORTANT]
>
>Alle gegevens die via `collectLifecycleDataWithAdditionalData:` blijft bestaan in `NSUserDefaults` door de SDK. De SDK slaat de waarden in de `NSDictionary` parameter die niet tot de `NSString` of `NSNumber` typen.

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    NSMutableDictionary *contextData = [NSMutableDictionary dictionary];
    [contextData setObject:@"Game" forKey:@"myapp.category"];
    [ADBMobile collectLifecycleDataWithAdditionalData:contextData];
    return YES;
}
```

Aanvullende contextgegevenswaarden die worden verzonden met `collectLifecycleDataWithAdditionalData` moet worden toegewezen aan aangepaste variabelen in Adobe Mobile-services:

![](assets/map-variable-lifecycle.png)

Andere levenscyclusmetriek worden automatisch verzameld. Zie voor meer informatie [Levenscycluscijfers](/help/ios/metrics.md).

## Volgende handelingen {#section_A24DC703359D4B5C8F493D6421306FD3}

Voer de volgende taken uit:

* [App-statussen bijhouden](/help/ios/analytics-main/states.md)
* [App-acties bijhouden](/help/ios/analytics-main/actions.md)
