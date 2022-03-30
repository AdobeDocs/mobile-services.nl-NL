---
description: Deze informatie helpt u met de Veiligheid van het Vervoer van de App (ATS) werken, die een nieuwe reeks veiligheidsvereisten voor iOS 9 is.
solution: Experience Cloud Services,Analytics
title: Beveiliging van toepassingsvervoer
topic-fix: Developer and implementation
uuid: e9ee13cf-9802-492e-8b11-95f028e34e61
exl-id: 2fe94e76-06d6-4ad1-95ba-193ae3df4d58
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 2%

---

# Beveiliging van toepassingsvervoer {#app-transport-security}

Deze informatie helpt u met de Veiligheid van het Vervoer van de App (ATS) werken, die een nieuwe reeks veiligheidsvereisten voor iOS 9 is.

Vanaf iOS 9 introduceerde Apple de Veiligheid van het Vervoer van de App, een reeks vereisten die aan beste praktijken voor veilige verbindingen in overeenstemming is. Zie voor meer informatie *NSAppTransportSecurity* in [Verwijzing naar eigenschappenlijst voor informatie](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/).

Als u wilt dat de Adobe Mobile SDK versie 4.7 of hoger naadloos werkt met ATS, gebruikt u de optie SSL inschakelen op de pagina Toepassingsinstellingen beheren. Zie voor meer informatie [Toepassingsinstellingen beheren](/help/using/c-manage-app-settings/c-manage-app-settings.md) of [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md).

Selecteer in Adobe Mobile Services de optie **[!UICONTROL Use HTTPS]** in de pagina Toepassingsinstellingen beheren worden alle resultaten van Analytics, Audience Manager, Target en Adobe Experience Platform Identity Services verzonden via HTTPS.

Als alternatief kunt u de volgende servers in uw lijst met &#39;toegestane&#39; plaatsen:

| Product | Instructies |
|--- |--- |
| Analytics | Als u uw Analyseserver wilt toestaan, voegt u het domein van de trackingserver toe aan het bestand info.plist als een uitzonderingsdomein voor ATS.  Het trackingserverdomein vindt u in de sectie Analytics van het dialoogvenster  `ADBMobileConfig.json` of in de sectie Analytics op de pagina Manage App Settings. |
| Audience Manager | Uw domein van de Audience Manager wordt gevonden in het serverbezit van het publiekManager voorwerp in uw `ADBMobileConfig.json` bestand.  Als u Audience Manager in uw app gebruikt en SSL niet is ingeschakeld, voegt u deze server als een uitzonderingsdomein voor ATS toe in uw app  `Info.plist` file |
| Target | U kunt uw eindpunt van het Doel aan uw Info.plist- dossier als uitzonderingsdomein voor ATS toevoegen.  Om uw eindpunt van het Doel te vinden, vind `clientCodeproperty` in het doelobject van uw `ADBMobileConfig.json` bestand. Uw eindpunt wordt `https://{clientCode}.tt.omtrdc.net`.  Als uw `clientCodeproperty` is `"myCompany"`wordt uw eindpunt `https://myCompany.tt.omtrdc.net`. |
| Adobe Experience Platform Identity Service | U kunt de server van de Experience Cloud als uitzonderingsdomein voor ATS in uw toevoegen  `Info.plist` bestand. Dit domein is `dpm.demdex.net`. |
| Mobile Services: Verwerving | De verwervingsserver toestaan als een uitzonderingsdomein voor ATS in uw  `Info.plist` bestand. Dit domein is `c00.adobe.com`. |
| Mobile Services: In-app berichten | Als u in-app berichten gebruikt, moet u mogelijk ingangen toevoegen aan het uitzonderingsdomein voor ATS voor elke URL die u gebruikt en die geen HTTPS is. Deze lijst bevat gehoste afbeeldingen en elke URL die is ingesloten in uw aangepaste HTML voor een volledig scherm.  Voor meer informatie over het instellen van uitzonderingen in een domein `info.plist` bestand, zie de *NSExceptionDomains* rij in *Tabel 2: Primaire sleutels in het woordenboek Transportbeveiliging*. Zie ook *Tabel 3 Woordenboeksleutels voor uitzonderingsdomeinen* in [Verwijzing naar eigenschappenlijst voor informatie](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/). |

>[!TIP]
>
>Deze overwegingen zijn van invloed op de verbindingen die worden gemaakt door de Adobe Mobile SDK en hebben geen invloed op de webweergave of andere verbindingen die worden gemaakt door uw app.
