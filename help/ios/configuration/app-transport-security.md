---
description: Deze informatie helpt u met de Veiligheid van het Vervoer van de App (ATS) werken, die een nieuwe reeks veiligheidsvereisten voor iOS 9 is.
seo-description: Deze informatie helpt u met de Veiligheid van het Vervoer van de App (ATS) werken, die een nieuwe reeks veiligheidsvereisten voor iOS 9 is.
seo-title: Beveiliging van toepassingsvervoer
solution: Experience Cloud,Analytics
title: Beveiliging van toepassingsvervoer
topic-fix: Developer and implementation
uuid: e9ee13cf-9802-492e-8b11-95f028e34e61
exl-id: 2fe94e76-06d6-4ad1-95ba-193ae3df4d58
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 2%

---

# Toepassingstransportbeveiliging {#app-transport-security}

Deze informatie helpt u met de Veiligheid van het Vervoer van de App (ATS) werken, die een nieuwe reeks veiligheidsvereisten voor iOS 9 is.

Vanaf iOS 9 introduceerde Apple de Beveiliging van het Vervoer van de App, een reeks vereisten die aan beste praktijken voor veilige verbindingen in overeenstemming is. Zie *NSAppTransportSecurity* in [Information Property List Key Reference](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/) voor meer informatie.

Gebruik de optie SSL inschakelen op de pagina Toepassingsinstellingen beheren als u wilt dat de Adobe Mobile SDK versie 4.7 of hoger naadloos werkt met ATS. Zie [Toepassingsinstellingen beheren](/help/using/c-manage-app-settings/c-manage-app-settings.md) of [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md) voor meer informatie.

In de Mobiele Diensten van de Adobe, door de **[!UICONTROL Use HTTPS]** optie in te selecteren beheert de pagina van de Montages van de Toepassing, worden alle treffers van Analytics, Audience Manager, Doel, en de Diensten van de Identiteit van Adobe Experience Platform verzonden via HTTPS.

Als alternatief kunt u de volgende servers in uw lijst met &#39;toegestane&#39; plaatsen:

| Product | Instructies |
|--- |--- |
| Analytics | Als u uw Analyseserver wilt toestaan, voegt u het domein van de trackingserver toe aan het bestand info.plist als een uitzonderingsdomein voor ATS.  Het domein van de trackingserver vindt u in de sectie Analytics van het `ADBMobileConfig.json`-bestand of in de sectie Analytics op de pagina Manage App Settings. |
| Audience Manager | Uw domein van de Audience Manager wordt gevonden in het serverbezit van het publiekManager voorwerp in uw `ADBMobileConfig.json` dossier.  Als u Audience Manager in uw app gebruikt en SSL niet is ingeschakeld, voegt u deze server als een uitzonderingsdomein voor ATS toe in uw `Info.plist`-bestand |
| Target | U kunt uw eindpunt van het Doel aan uw Info.plist- dossier als uitzonderingsdomein voor ATS toevoegen.  Als u het eindpunt van het doel wilt vinden, zoekt u `clientCodeproperty` in het doelobject van het `ADBMobileConfig.json`-bestand. Uw eindpunt zal `https://{clientCode}.tt.omtrdc.net` zijn.  Als uw `clientCodeproperty` bijvoorbeeld `“myCompany”` is, is uw eindpunt `https://myCompany.tt.omtrdc.net`. |
| Adobe Experience Platform Identity Service | U kunt de server van de Experience Cloud als uitzonderingsdomein voor ATS in uw `Info.plist` dossier toevoegen. Dit domein is `dpm.demdex.net`. |
| Mobiele services: Verwerving | Toestaan dat de overnameserver een uitzonderingsdomein is voor ATS in uw `Info.plist`-bestand. Dit domein is `c00.adobe.com`. |
| Mobiele services: In-app berichten | Als u in-app berichten gebruikt, moet u mogelijk ingangen toevoegen aan het uitzonderingsdomein voor ATS voor elke URL die u gebruikt en die geen HTTPS is. Deze lijst bevat gehoste afbeeldingen en elke URL die is ingesloten in uw aangepaste HTML-bericht voor volledig scherm.  Zie de rij *NSExceptionDomains* in *Tabel 2 voor meer informatie over het instellen van uitzonderingen in een `info.plist`-bestand: Primaire sleutels van het woordenboek van de Veiligheid van het Vervoer van de toepassing*. Zie ook *Tabel 3 Woordenboeksleutels voor uitzonderingsdomeinen* in [Verwijzing naar lijst met eigenschappen van informatie](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/). |

>[!TIP]
>
>Deze overwegingen zijn van invloed op de verbindingen die worden gemaakt door de SDK van Adobe Mobile en hebben geen invloed op de webweergave of andere verbindingen die worden gemaakt door uw app.
