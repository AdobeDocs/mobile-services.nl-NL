---
description: In de volgende tabel worden de verschillende toepassings-id's beschreven die door de iOS SDK- en Adobe Mobile-services worden gebruikt.
solution: Experience Cloud Services,Analytics
title: Toepassings-id's
topic-fix: Developer and implementation
uuid: 24ebc716-23c7-4ee8-8256-b534210367e0
exl-id: 82f0a097-b2eb-4313-8624-dd442e3da039
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 1%

---

# Toepassings-id&#39;s {#app-ids}

In de volgende tabel worden de verschillende toepassings-id&#39;s beschreven die door de iOS SDK- en Adobe Mobile-services worden gebruikt.

| Id | Beschrijving |
|--- |--- |
| ID verzonden met levenscyclusmetriek | Dit is een combinatie van de toepassingsnaam en de bundelversie die naar de App Store wordt verzonden.  Deze waarde wordt gebruikt voor het Versierapport in Adobe Mobile-services en u kunt deze waarde gebruiken om de resultaten te filteren op een specifieke releaseversie van uw app. |
| App Store-id | Deze id wordt toegewezen aan uw app door de App Store en wordt geleverd in Adobe Mobile-services wanneer u acquisitie-koppelingen maakt. |
| AppID in ADBMobile JSON Config | Deze id is een unieke id die door Adobe Mobile-services aan de toepassingsinstantie wordt toegewezen voor alle bijbehorende metagegevens in uw systeem.  Deze id wordt gebruikt om de unieke URL&#39;s voor het bijhouden of bijhouden van acquisities te maken. Deze id wordt automatisch toegevoegd aan het JSON-configuratiebestand van ADBMobile wanneer deze wordt gedownload van de gebruikersinterface. U vindt deze id in Toepassingsinstellingen beheren onder de overnameinstellingen voor uw app. |
