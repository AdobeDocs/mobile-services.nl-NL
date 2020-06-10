---
description: Deze informatie helpt u met de Veiligheid van het Vervoer van de App (ATS) werken, die een nieuwe reeks veiligheidsvereisten voor iOS 9 is.
seo-description: Deze informatie helpt u met de Veiligheid van het Vervoer van de App (ATS) werken, die een nieuwe reeks veiligheidsvereisten voor iOS 9 is.
seo-title: Beveiliging van toepassingsvervoer
solution: Marketing Cloud,Analytics
title: Beveiliging van toepassingsvervoer
topic: Developer and implementation
uuid: e9ee13cf-9802-492e-8b11-95f028e34e61
translation-type: tm+mt
source-git-commit: e6af295ddc5fea2a3e649b659894e6c6123a3457
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---


# Beveiliging van toepassingsvervoer {#app-transport-security}

Deze informatie helpt u met de Veiligheid van het Vervoer van de App (ATS) werken, die een nieuwe reeks veiligheidsvereisten voor iOS 9 is.

Vanaf iOS 9 introduceerde Apple de Beveiliging van het Vervoer van de App, een reeks vereisten die aan beste praktijken voor veilige verbindingen in overeenstemming is. Voor meer informatie, zie *NSAppTransportSecurity* in de Zeer belangrijke Verwijzing [van de Lijst van het Bezit van de](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/)Informatie.

Als u wilt dat de Adobe Mobile SDK versie 4.7 of hoger naadloos werkt met ATS, gebruikt u de optie SSL inschakelen op de pagina Toepassingsinstellingen beheren. Zie [Toepassingsinstellingen](/help/using/c-manage-app-settings/c-manage-app-settings.md) beheren of [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md)voor meer informatie.

In Adobe Mobile Services worden alle hits van Analytics, Audience Manager, Target en Adobe Experience Platform Identity Services via HTTPS verzonden door de optie **[!UICONTROL Use HTTPS]** in de pagina Toepassingsinstellingen beheren te selecteren.

Als alternatief kunt u de volgende servers in uw lijst met &#39;toegestane&#39; plaatsen:

| Product | Instructies |
|--- |--- |
| Analyse | Als u uw Analyseserver wilt toestaan, voegt u het domein van de trackingserver toe aan het bestand info.plist als een uitzonderingsdomein voor ATS.  Het domein van de trackingserver vindt u in de sectie Analytics van het `ADBMobileConfig.json` bestand of in de sectie Analytics op de pagina Manage App Settings. |
| Audience Manager | Uw domein van de Manager van de Publiek wordt gevonden in het serverbezit van het publiekManager voorwerp in uw `ADBMobileConfig.json` dossier.  Als u Audience Manager gebruikt in uw app en SSL niet is ingeschakeld, voegt u deze server als een uitzonderingsdomein voor ATS toe in uw `Info.plist` bestand |
| Doel | U kunt uw eindpunt van het Doel aan uw Info.plist- dossier als uitzonderingsdomein voor ATS toevoegen.  Als u het eindpunt van het Doel wilt vinden, zoekt u het `clientCodeproperty` in het doelobject van het `ADBMobileConfig.json` bestand. Uw eindpunt zal zijn `https://{clientCode}.tt.omtrdc.net`.  Bijvoorbeeld, als uw `clientCodeproperty` is `“myCompany”`, zal uw eindpunt zijn `https://myCompany.tt.omtrdc.net`. |
| Adobe Experience Platform Identity Service | U kunt de Experience Cloud-server toevoegen als een uitzonderingsdomein voor ATS in uw `Info.plist` bestand. Dit domein is `dpm.demdex.net`. |
| Mobiele services: Verwerving | Toestaan dat de overnameserver een uitzonderingsdomein is voor ATS in uw `Info.plist` bestand. Dit domein is `c00.adobe.com`. |
| Mobiele services: In-app berichten | Als u in-app berichten gebruikt, moet u mogelijk ingangen toevoegen aan het uitzonderingsdomein voor ATS voor elke URL die u gebruikt en die geen HTTPS is. Deze lijst bevat gehoste afbeeldingen en elke URL die is ingesloten in uw aangepaste HTML-bericht voor volledig scherm.  Zie de rij `info.plist` NSExceptionDomains *in* Tabel 2 voor meer informatie over het instellen van uitzonderingen in een *bestand: Primaire sleutels* van het woordenboek van de Veiligheid van het Vervoer van de toepassing. Zie ook *Tabel 3 Woordenboeksleutels* van uitzonderingsdomeinen in de Sleutelverwijzing [van de Lijst van het Bezit van de](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/)Informatie. |

>[!TIP]
>
>Deze overwegingen zijn van invloed op de verbindingen die door de SDK van Adobe Mobile worden gemaakt en hebben geen invloed op de webweergave of andere verbindingen die door uw app worden gemaakt.

