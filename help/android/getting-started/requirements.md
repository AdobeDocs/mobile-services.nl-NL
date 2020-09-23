---
description: 'Voordat u een rapportsuite configureert en Android-toepassingsgegevens verzamelt, moet u de volgende vereiste taken uitvoeren '
seo-description: 'Voordat u een rapportsuite configureert en Android-toepassingsgegevens verzamelt, moet u de volgende vereiste taken uitvoeren '
seo-title: Voordat u begint
solution: Experience Cloud,Analytics
title: Voordat u begint
topic: Developer and implementation
uuid: 0ca9e937-8d40-4570-9dbf-9aecc6ecedf6
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 3%

---


# Voordat u begint {#before-you-start}

Voordat u een rapportsuite configureert en gegevens van de Android-app verzamelt, moet u de volgende vereiste taken uitvoeren:

## Rolspecifieke taken {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analysebeheerders en toepassingsontwikkelaars moeten de volgende taken uitvoeren:

### Analysebeheerders

Een rapportsuite configureren en gegevens van mobiele apps verzamelen:

1. Voltooi een van de secties in [Login aan de gebruikersinterface](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8)van de Mobiele Diensten van de Adobe.
1. Maak een analyseaccount voor elke ontwikkelaar van de app.

App-ontwikkelaars hebben nu toegang tot de rapportsuite(s) die u hebt gemaakt.

>[!IMPORTANT]
>
>Als u een nieuwe rapportsuite wilt maken en SDK&#39;s wilt downloaden, moet u een analysebeheerder zijn.

### App-ontwikkelaars

1. Zorg ervoor dat uw beheerder Analytics de stappen in de Beheerders *van* Analytics in [Rol-Specifieke Taken](../getting-started/requirements.md#section_8B9EA1FA189F4C6DB7D829F0B5844FBC)heeft voltooid.
1. Verifieer dat uw beheerder van de Analyse één van de secties in [Login aan de Mobiele Diensten UI](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8)van Adobe heeft voltooid.
1. Nadat de rapportreeks is gevormd, voltooi stappen in de [Download SDK](../getting-started/requirements.md#section_044C17DF82BC4FD8A3E409C456CE9A46).

Voor meer informatie over rollen en toestemmingen, zie [Rollen en Toestemmingen](/help/using/gs/c-mob-roles-and-permissions.md).

## Aanmelden bij de gebruikersinterface van Adobe Mobile Services {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile-services is de primaire rapportageinterface voor analyses en doelwitten van mobiele apps. Nadat u deze stappen voltooit, kunt u een configuratiedossier downloaden dat met uw server van de gegevensinzameling, rapportreeks, en vele andere montages vooraf wordt gevormd.

U kunt zich op een van de volgende manieren aanmelden bij de gebruikersinterface van Adobe Mobile Services:

### Experience Cloud

Meld u aan bij de [Experience Cloud](https://experiencecloud.adobe.com) met uw Adobe ID. Deze methode veronderstelt dat uw bedrijf provisioned in de Experience Cloud is, en u hebt uw rekening Analytics verbonden. Zie Gebruikers en producten [van Experience Cloud](https://docs.adobe.com/content/help/nl-NL/core-services/interface/manage-users-and-products/admin-getting-started.html)beheren voor meer informatie.

>[!TIP]
>
>Als u niet zeker weet of uw bedrijf provisioned in de Experience Cloud is, gebruik uw bestaande rekening van Adobe Analytics.

### Adobe Analytics

Klik en ga uw het bedrijfsnaam van Analytics, uw gebruikersbenaming, en uw wachtwoord in. **[!UICONTROL Sign in with Analytics]**

## Een rapportsuite maken {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Een rapportsuite maken om toepassingsgegevens te verzamelen en een app te definiëren:

1. Meld u aan bij de gebruikersinterface voor mobiele services door [https://mobilemarketing.adobe.com/](https://mobilemarketing.adobe.com/) in een browser te typen.
1. Klik op **[!UICONTROL Create an App]**.

   Als deze knop niet wordt weergegeven, klikt u op **[!UICONTROL Manage Apps]** > **[!UICONTROL Add]**.

1. In the **[!UICONTROL Report Suite]** drop-down, select **[!UICONTROL New Report Suite]**.

1. Voer de naam van uw app in en selecteer een type rapportsuite.

   Een voorbeeld van een rapportsuite-id is `mycomobileappdev`. U moet afzonderlijke rapportsuite en apps instellen voor de ontwikkelings- en productieversies, zodat u deze stappen kunt herhalen wanneer u klaar bent om de productieversie in te stellen.
1. Controleer **[!UICONTROL Report Suite ID]** in of de naam van de rapportsuite wordt weergegeven.
1. Controleer **[!UICONTROL Copy Settings From]** in of **[!UICONTROL Mobile App Template]** is geselecteerd.

   Met deze sjabloon kunnen tijdstempels offline gegevens verzamelen en worden de variabelen van de mobiele oplossing geactiveerd om levenscyclusmetriek vast te leggen.

1. Selecteer uw tijdzone, uw valuta en klik **[!UICONTROL Save]**.

## De SDK downloaden {#section_044C17DF82BC4FD8A3E409C456CE9A46}

De mobiele SDK downloaden:

1. Meld u aan bij de gebruikersinterface voor mobiele services door [https://mobilemarketing.adobe.com/](https://mobilemarketing.adobe.com/) in een browser te typen.
1. Klik in het linkerdeelvenster op de **[!UICONTROL All Apps]** vervolgkeuzelijst en selecteer uw app.
U kunt uw toepassing ook selecteren in het rechterdeelvenster.

   >[!IMPORTANT]
   >
   >Als u de app in het rechterdeelvenster wilt weergeven, moet u eerst een app maken. Zie Een nieuwe app [toevoegen voor informatie over het maken van een app.](https://docs.adobe.com/content/help/en/mobile-services/using/manage-apps-ug/t-new-app.html)

1. Klik in het linkerdeelvenster van uw app op **[!UICONTROL Manage App Settings]**.

   >[!IMPORTANT]
   >
   >Als u de **[!UICONTROL Manage App Settings]** optie niet ziet, zorg ervoor dat u in de Mobiele Diensten van Adobe wordt geregistreerd. Om te verifiëren, klik het pictogram van de ![oplossingsschakelaar](assets/solution-switcher.png) in de hoogste juiste kant van de pagina en zorg ervoor dat in de bovenkant linkerkant **[!UICONTROL Adobe Mobile Services]** wordt getoond.

1. Download onder aan de pagina Toepassingsinstellingen beheren in de **[!UICONTROL App SDK Downloads]** sectie de SDK en de voorbeeldtoepassing voor uw platform.

>[!TIP]
>
>Er wordt automatisch een configuratiebestand voor uw app opgenomen in de SDK-download, zodat u dat bestand niet afzonderlijk hoeft te downloaden. Als u de SDK echter al hebt gedownload en u wilt de bijgewerkte instellingen ophalen, downloadt u het configuratiebestand opnieuw.

Als u Android Studio gebruikt, kunt u ook het volgende toevoegen aan het `build.gradle` bestand van uw app:

```java
compile 'com.adobe.mobile:adobeMobileLibrary:4.13.7'
```

De volgende informatie onthouden:

* Vervang het versienummer in het codevoorbeeld door de juiste versie van de Android-SDK&#39;s.
* Download het configuratiedossier en neem het in uw project op.