---
description: 'Voordat u een rapportsuite configureert en Android-toepassingsgegevens verzamelt, moet u de volgende vereiste taken uitvoeren '
solution: Experience Cloud,Analytics
title: Voordat u begint
topic-fix: Developer and implementation
uuid: 0ca9e937-8d40-4570-9dbf-9aecc6ecedf6
exl-id: e9c0fd94-b61d-4f56-97b8-f71aac096c93
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 1%

---

# Voordat u begint {#before-you-start}

Voordat u een rapportsuite configureert en gegevens van de Android-app verzamelt, moet u de volgende vereiste taken uitvoeren:

## Rolspecifieke taken {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analysebeheerders en toepassingsontwikkelaars moeten de volgende taken uitvoeren:

### Analysebeheerders

Een rapportsuite configureren en gegevens van mobiele apps verzamelen:

1. Voltooi een van de secties in [Meld u aan bij de gebruikersinterface van Mobiele Adobe-services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8).
1. Maak een analyseaccount voor elke ontwikkelaar van de app.

App-ontwikkelaars hebben nu toegang tot de rapportsuite(s) die u hebt gemaakt.

>[!IMPORTANT]
>
>Als u een nieuwe rapportsuite wilt maken en SDK&#39;s wilt downloaden, moet u een analysebeheerder zijn.

### App-ontwikkelaars

1. Zorg ervoor dat uw beheerder Analytics de stappen in *Analytics Administrators* in [Role-Specific Tasks](../getting-started/requirements.md#section_8B9EA1FA189F4C6DB7D829F0B5844FBC) heeft voltooid.
1. Verifieer dat uw beheerder van Analytics één van de secties in [login aan de Mobiele Diensten UI van de Adobe heeft voltooid ](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8).
1. Nadat de rapportreeks is gevormd, voltooi stappen in [Download SDK](../getting-started/requirements.md#section_044C17DF82BC4FD8A3E409C456CE9A46).

Voor meer informatie over rollen en toestemmingen, zie [Rollen en Toestemmingen](/help/using/gs/c-mob-roles-and-permissions.md).

## Aanmelden bij de gebruikersinterface van Adobe Mobile Services {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile-services is de primaire rapportageinterface voor analyses en doelwitten van mobiele apps. Nadat u deze stappen voltooit, kunt u een configuratiedossier downloaden dat met uw server van de gegevensinzameling, rapportreeks, en vele andere montages vooraf wordt gevormd.

U kunt zich op een van de volgende manieren aanmelden bij de gebruikersinterface van Adobe Mobile Services:

### Experience Cloud

Meld u aan bij [Experience Cloud](https://experiencecloud.adobe.com) met uw Adobe ID. Deze methode veronderstelt dat uw bedrijf provisioned in de Experience Cloud is, en u hebt uw rekening Analytics verbonden. Zie [Experience Cloud-gebruikers en -producten beheren](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html) in de handleiding Experience Cloud Central Interface Components.

>[!TIP]
>
>Als u niet zeker weet of uw bedrijf provisioned in de Experience Cloud is, gebruik uw bestaande rekening van Adobe Analytics.

### Adobe Analytics

Klik **[!UICONTROL Sign in with Analytics]** en ga uw het bedrijfsnaam van Analytics, uw gebruikersbenaming, en uw wachtwoord in.

## Een rapportsuite maken {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Een rapportsuite maken om toepassingsgegevens te verzamelen en een app te definiëren:

1. Meld u aan bij [Mobiele services Adobe](https://mobilemarketing.adobe.com).
1. Klik op **[!UICONTROL Create an App]**.

   Als deze knop niet wordt weergegeven, klikt u op **[!UICONTROL Manage Apps]** > **[!UICONTROL Add]**.

1. Selecteer **[!UICONTROL New Report Suite]** in de vervolgkeuzelijst **[!UICONTROL Report Suite]**.

1. Voer de naam van uw app in en selecteer een type rapportsuite.

   Een voorbeeld van een rapportsuite-id is `mycomobileappdev`. U moet afzonderlijke rapportsuite en apps instellen voor de ontwikkelings- en productieversies, zodat u deze stappen kunt herhalen wanneer u klaar bent om de productieversie in te stellen.
1. Controleer in **[!UICONTROL Report Suite ID]** of de naam van de rapportsuite wordt weergegeven.
1. Controleer in **[!UICONTROL Copy Settings From]** of **[!UICONTROL Mobile App Template]** is geselecteerd.

   Met deze sjabloon kunnen tijdstempels offline gegevens verzamelen en worden de variabelen van de mobiele oplossing geactiveerd om levenscyclusmetriek vast te leggen.

1. Selecteer uw tijdzone, uw valuta, en klik **[!UICONTROL Save]**.

## De SDK downloaden {#section_044C17DF82BC4FD8A3E409C456CE9A46}

De mobiele SDK downloaden:

1. Meld u aan bij de gebruikersinterface voor mobiele services door [https://mobilemarketing.adobe.com/](https://mobilemarketing.adobe.com/) in een browser te typen.
1. Klik in het linkerdeelvenster op de vervolgkeuzelijst **[!UICONTROL All Apps]** en selecteer uw app.
U kunt uw toepassing ook selecteren in het rechterdeelvenster.

   >[!IMPORTANT]
   >
   >Als u de app in het rechterdeelvenster wilt weergeven, moet u eerst een app maken. Zie [Nieuwe app toevoegen](/help/using/manage-apps/t-new-app.md) voor informatie over het maken van een app.

1. Klik in het linkerdeelvenster van uw app op **[!UICONTROL Manage App Settings]**.

   >[!IMPORTANT]
   >
   >Als u niet de **[!UICONTROL Manage App Settings]** optie ziet, zorg ervoor dat u in de Mobiele Diensten van de Adobe wordt geregistreerd. Als u wilt controleren, klikt u op de ![oplossingsschakelaar](assets/solution-switcher.png)-pictogram rechtsboven op de pagina en controleert u of **[!UICONTROL Adobe Mobile Services]** linksboven wordt weergegeven.

1. Download onder aan de pagina Toepassingsinstellingen beheren in de sectie **[!UICONTROL App SDK Downloads]** de SDK en de voorbeeldtoepassing voor uw platform.

>[!TIP]
>
>Er wordt automatisch een configuratiebestand voor uw app opgenomen in de SDK-download, zodat u dat bestand niet afzonderlijk hoeft te downloaden. Als u de SDK echter al hebt gedownload en u wilt de bijgewerkte instellingen ophalen, downloadt u het configuratiebestand opnieuw.

Als u Android Studio gebruikt, kunt u ook het volgende toevoegen aan het `build.gradle`-bestand van uw app:

```java
compile 'com.adobe.mobile:adobeMobileLibrary:4.13.7'
```

De volgende informatie onthouden:

* Vervang het versienummer in het codevoorbeeld door de juiste versie van de Android-SDK&#39;s.
* Download het configuratiedossier en neem het in uw project op.
