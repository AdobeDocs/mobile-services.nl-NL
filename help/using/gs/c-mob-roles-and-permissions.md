---
description: In Adobe Analytics kunt u rollen beheren op de startpagina van Admin Tools.
seo-description: In Adobe Analytics kunt u rollen beheren op de startpagina van Admin Tools.
seo-title: Rollen en machtigingen
title: Rollen en machtigingen
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
translation-type: tm+mt
source-git-commit: c7cac006340e01d0fd1f6afe3419e6fd17294a98

---


# Rollen en machtigingen{#roles-and-permissions}

In Adobe Analytics kunt u rollen beheren op de startpagina van Admin Tools.

## Overzicht {#section_91B8192891E14E5285718C8118912500}

De volgende rollen beheren toestemmingen in Mobiele Diensten UI:

### Analysebeheer

Een Analysebeheerder beheert gebruikersgroepen en wijst toestemmingen toe, één waarvan Mobiele App Admin is. Met Experience Cloud Admin koppelt u uw Adobe-id aan uw Adobe Analytics-account. Hiermee kunt u zich aanmelden bij de gebruikersinterface voor mobiele services met uw Adobe-id. Zie [Beheer - Gebruikersbeheer en Veelgestelde vragen](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html)voor meer informatie over de Experience Cloud Administrator.

>[!TIP]
>
>Een bestaande analytische beheerder kan de rol Analytics Admin aan om het even welke gebruiker toewijzen.

Zie de volgende inhoud voor meer informatie over deze rol:

* [Overzicht van gebruikersbeheer](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/users.html)

* [Wijzigingen in machtigingen voor gebruikers en groepen](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/permissions-changes.html)

### Mobiele toepassingsbeheerder

Deze rol is Admin voor de Mobiele UI van de Diensten.

>[!IMPORTANT]
>
>Voor sommige functies, zoals pushberichten, moet de Analysebeheerder het **[!UICONTROL Segment Creation]** selectievakje in Gebruikersbeheer inschakelen.

## Toegang beheren {#section_E6939C2695AA4A0DBF432D50B2670920}

Hier is wat extra informatie over de toegang tot van opties in de Mobiele UI van de Diensten:

### Apps en rapportsuites

Alle mobiele service-apps zijn gekoppeld aan rapportageopets. Als gebruikers geen toegang hebben tot een rapportsuite, hebben ze geen toegang tot de bijbehorende app van die rapportsuite.

### Mobiele services en analysefuncties

Als uw bedrijf geen contract van Analytics heeft om tot een eigenschap in UI, zoals het Push Overseinen toegang te hebben, zal geen gebruiker in uw bedrijf toegang tot die eigenschap, ongeacht toestemmingsniveau hebben.

## Rollen en machtigingen {#section_20AA029D5B8C413C8659777E79B11620}

Hier zijn de rollen in Mobiele Diensten UI, met hun relevante toestemmingen:

### Analysebeheer

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

### Mobiele toepassingsbeheerder

* Alle gebruikersmachtigingen
* App maken met bestaande rapportsuite
* Toepassingsinstellingen beheren

   * Opties voor Mobile SDK van app configureren
   * UI-instellingen van app configureren
   * Gekoppelde App Store-apps configureren
   * Opties voor Universal Link van app configureren
   * Push Services-certificaten en API-sleutels configureren
   * Maken/bijwerken/activeren/deactiveren/Dupliceren/archiveren/Postbacks verwijderen
   * Koppelingsbestemmingen maken/bijwerken/archiveren/verwijderen

* Marketing-koppelingen maken/bijwerken/archiveren
* Koppelingen voor verouderde overname maken/importeren/bijwerken/verwijderen
* Configuratie van Plaatsen maken/importeren/bijwerken/verwijderen (interessepunten)
* Pushberichten maken/bijwerken/verzenden/plannen/annuleren/dupliceren/archiveren/verwijderen
* In-app-berichten maken/bijwerken/activeren/deactiveren/dupliceren/archiveren/verwijderen

Zie voor meer informatie over groepen en gebruikers:

* [Gebruikersgroepinstellingen](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-groups/groups.html)
* [Een gebruiker aan een groep toevoegen](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Gebruiker van mobiele services

Deze rol heeft mening-slechts toestemmingen en kan terugkoppelen in de Mobiele UI van de Diensten verstrekken.

* Feedback geven op gebruikersinterface voor mobiele services
* Apps weergeven

   >[!IMPORTANT]
   >
   >Gebruikers kunnen de rapportsuite alleen bekijken in Adobe Analytics.

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
