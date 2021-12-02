---
description: In Adobe Analytics kunt u rollen beheren op de startpagina van Admin Tools.
title: Rollen en machtigingen
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
source-git-commit: f6a62a46a90c30edaf999085873bf21f2a03a68e
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 2%

---

# Rollen en machtigingen{#roles-and-permissions}

In Adobe Analytics kunt u rollen beheren op de startpagina van Admin Tools.

## Overzicht {#section_91B8192891E14E5285718C8118912500}

De volgende rollen beheren toestemmingen in Mobiele Diensten UI:

### Analysebeheer

Een Analysebeheerder beheert gebruikersgroepen en wijst toestemmingen toe, één waarvan Mobiele App Admin is. De Experience Cloud Admin verbindt uw Adobe ID met uw rekening van Adobe Analytics, die u toestaat om aan te melden bij de Mobiele UI van de Diensten door uw Adobe ID te gebruiken. Voor meer informatie over de Beheerder van de Experience Cloud, zie [Gebruikers en producten van Experience Cloud beheren](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html) in de handleiding Experience Cloud Central Interface Components.

>[!TIP]
>
>Een bestaande analytische beheerder kan de rol Analytics Admin aan om het even welke gebruiker toewijzen.

Raadpleeg de volgende inhoud in de documentatie van Adobe Analytics voor meer informatie over deze rol:

* [Overzicht van User Management](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)
* [Wijzigingen in gebruikers- en groepstoestemmmingen](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)

### Mobiele toepassingsbeheerder

Deze rol is Admin voor de Mobiele UI van de Diensten.

>[!IMPORTANT]
>
>Voor bepaalde functies, zoals pushberichten, moet de Analysebeheerder de optie **[!UICONTROL Segment Creation]** in Gebruikersbeheer.

## Toegang beheren {#section_E6939C2695AA4A0DBF432D50B2670920}

Hier is wat extra informatie over de toegang tot van opties in de Mobiele UI van de Diensten:

### Apps en rapportsuites

Alle mobiele service-apps zijn gekoppeld aan rapportageopets. Als gebruikers geen toegang hebben tot een rapportsuite, hebben ze geen toegang tot de bijbehorende app van die rapportsuite.

### Mobiele services en analysefuncties

Als uw bedrijf geen contract van Analytics heeft om tot een eigenschap in UI, zoals het Push Overseinen toegang te hebben, zal geen gebruiker in uw bedrijf toegang tot die eigenschap, ongeacht toestemmingsniveau hebben.

## Rollen en machtigingen {#section_20AA029D5B8C413C8659777E79B11620}

Hier zijn de rollen in Mobiele Diensten UI, met hun relevante toestemmingen:

### Machtigingen Analysebeheer

* Alle gebruikers- en mobiele toepassingsbeheermachtigingen
* App maken met nieuwe rapportsuite
* App van mobiele services verwijderen

   >[!IMPORTANT]
   >
   >Hoewel de app is verwijderd uit de gebruikersinterface voor mobiele services, bestaat de rapportsuite nog steeds in Analytics.

* Toepassingsinstellingen beheren

   * Levenscyclusrapportage inschakelen
   * Locatierapportage inschakelen
   * Variabelen en statistieken maken/bijwerken/verwijderen

### Machtigingen voor beheer van mobiele apps

* Alle gebruikersmachtigingen
* App maken met bestaande rapportsuite
* Toepassingsinstellingen beheren

   * Opties voor Mobile SDK van app configureren
   * UI-instellingen van app configureren
   * Gekoppelde App Store-toepassingen configureren
   * Opties voor Universal Link van app configureren
   * Push Services-certificaten en API-sleutels configureren
   * Maken/bijwerken/activeren/deactiveren/Dupliceren/archiveren/Postbacks verwijderen
   * Koppelingsbestemmingen maken/bijwerken/archiveren/verwijderen

* Marketing-koppelingen maken/bijwerken/archiveren
* Koppelingen voor verouderde overname maken/importeren/bijwerken/verwijderen
* Configuratie van Plaatsen maken/importeren/bijwerken/verwijderen (interessepunten)
* Pushberichten maken/bijwerken/verzenden/plannen/annuleren/dupliceren/archiveren/verwijderen
* In-app-berichten maken/bijwerken/activeren/deactiveren/dupliceren/archiveren/verwijderen

Raadpleeg de volgende inhoud in de documentatie van Adobe Analytics voor meer informatie over groepen en gebruikers:

* [Instellingen gebruikersgroep (verouderd)](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)
* [Een gebruiker aan een groep toevoegen](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)

### Gebruiker van mobiele services

Deze rol heeft mening-slechts toestemmingen en kan terugkoppelen in de Mobiele UI van de Diensten verstrekken.

* Feedback geven op gebruikersinterface voor mobiele services
* Apps weergeven

   >[!IMPORTANT]
   >
   >Gebruikers kunnen alleen de rapportsuites zien waartoe zij in Adobe Analytics toegang hebben.

* App-instellingen weergeven

   * App SDK-configuratie downloaden
   * Alle instellingen voor gebruikersinterface en SDK weergeven
   * De configuratie Variabelen en Metriek weergeven
   * Postbacks weergeven
   * Koppelingsdoelen weergeven

* Rapporten weergeven en uitvoeren
* Marketingkoppelingen weergeven
* Koppelingen voor verouderde overname weergeven en exporteren
* Configuratie van Plaatsen weergeven en exporteren (interessepunten)
* Push-berichten weergeven
* In-app berichten weergeven
