---
description: 'Voordat u een rapportsuite configureert en Android-toepassingsgegevens verzamelt, moet u de volgende vereiste taken uitvoeren '
solution: Experience Cloud Services,Analytics
title: Voordat u begint
topic-fix: Developer and implementation
uuid: 0ca9e937-8d40-4570-9dbf-9aecc6ecedf6
exl-id: e9c0fd94-b61d-4f56-97b8-f71aac096c93
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
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

1. Een van de secties in [Aanmelden bij de gebruikersinterface van Adobe Mobile Services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8).
1. Maak een analyseaccount voor elke ontwikkelaar van de app.

App-ontwikkelaars hebben nu toegang tot de rapportsuite(s) die u hebt gemaakt.

>[!IMPORTANT]
>
>Als u een nieuwe rapportsuite wilt maken en SDK&#39;s wilt downloaden, moet u een analysebeheerder zijn.

### App-ontwikkelaars

1. Controleer of de beheerder van de Analytics de stappen in het dialoogvenster *Analysebeheerders* in [Rolspecifieke taken](../getting-started/requirements.md#section_8B9EA1FA189F4C6DB7D829F0B5844FBC).
1. Controleer of uw beheerder van Analytics een van de secties in [Aanmelden bij de gebruikersinterface van Adobe Mobile Services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8).
1. Nadat de rapportreeks is gevormd, voltooi stappen in [De SDK downloaden](../getting-started/requirements.md#section_044C17DF82BC4FD8A3E409C456CE9A46).

Voor meer informatie over rollen en toestemmingen, zie [Rollen en machtigingen](/help/using/gs/c-mob-roles-and-permissions.md).

## Aanmelden bij de gebruikersinterface van Adobe Mobile Services {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile-services is de primaire rapportageinterface voor analyses en doelwitten van mobiele apps. Nadat u deze stappen voltooit, kunt u een configuratiedossier downloaden dat met uw server van de gegevensinzameling, rapportreeks, en vele andere montages vooraf wordt gevormd.

U kunt zich op een van de volgende manieren aanmelden bij de gebruikersinterface van Adobe Mobile Services:

### Experience Cloud

Aanmelden bij de [Experience Cloud](https://experiencecloud.adobe.com) met uw Adobe ID. Deze methode veronderstelt dat uw bedrijf provisioned in de Experience Cloud is, en u hebt uw rekening Analytics verbonden. Zie voor meer informatie [Gebruikers en producten van Experience Cloud beheren](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html) in de handleiding Experience Cloud Central Interface Components.

>[!TIP]
>
>Als u niet zeker weet of uw bedrijf provisioned in de Experience Cloud is, gebruik uw bestaande rekening van Adobe Analytics.

### Adobe Analytics

Klikken **[!UICONTROL Sign in with Analytics]** en voer uw bedrijfsnaam, gebruikersnaam en wachtwoord voor Analytics in.

## Een rapportsuite maken {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Een rapportsuite maken om toepassingsgegevens te verzamelen en een app te definiëren:

1. Aanmelden bij [Adobe mobiele services](https://mobilemarketing.adobe.com).
1. Klik op **[!UICONTROL Create an App]**.

   Als deze knop niet wordt weergegeven, klikt u op **[!UICONTROL Manage Apps]** > **[!UICONTROL Add]**.

1. In de **[!UICONTROL Report Suite]** vervolgkeuzelijst, selecteert u **[!UICONTROL New Report Suite]**.

1. Voer de naam van uw app in en selecteer een type rapportsuite.

   Een voorbeeld van een rapportsuite-id is `mycomobileappdev`. U moet afzonderlijke rapportsuite en apps instellen voor de ontwikkelings- en productieversies, zodat u deze stappen kunt herhalen wanneer u klaar bent om de productieversie in te stellen.
1. In **[!UICONTROL Report Suite ID]**, controleert u of de naam van uw rapportsuite wordt weergegeven.
1. In **[!UICONTROL Copy Settings From]**, controleert of **[!UICONTROL Mobile App Template]** is geselecteerd.

   Met deze sjabloon kunnen tijdstempels offline gegevens verzamelen en worden de variabelen van de mobiele oplossing geactiveerd om levenscyclusmetriek vast te leggen.

1. Selecteer uw tijdzone, uw valuta en klik **[!UICONTROL Save]**.

## De SDK downloaden {#section_044C17DF82BC4FD8A3E409C456CE9A46}

De mobiele SDK downloaden:

1. Meld u aan bij de gebruikersinterface van Mobile Services door te typen [https://mobilemarketing.adobe.com/](https://mobilemarketing.adobe.com/) in een browser.
1. Klik in het linkerdeelvenster op de knop **[!UICONTROL All Apps]** en selecteer uw app.
U kunt uw toepassing ook selecteren in het rechterdeelvenster.

   >[!IMPORTANT]
   >
   >Als u de app in het rechterdeelvenster wilt weergeven, moet u eerst een app maken. Voor informatie over het maken van een app raadpleegt u [Een nieuwe app toevoegen](/help/using/manage-apps/t-new-app.md).

1. Klik in uw app in het linkerdeelvenster op **[!UICONTROL Manage App Settings]**.

   >[!IMPORTANT]
   >
   >Als u de **[!UICONTROL Manage App Settings]** zorgt u ervoor dat u bent aangemeld bij Adobe Mobile Services. Klik op de knop ![oplossingsschakelaar](assets/solution-switcher.png) in de rechterbovenhoek van de pagina en zorg ervoor dat **[!UICONTROL Adobe Mobile Services]** wordt linksboven weergegeven.

1. Onder aan de pagina App Settings (Toepassingsinstellingen beheren) vindt u in het dialoogvenster **[!UICONTROL App SDK Downloads]** de SDK en de voorbeeldtoepassing voor uw platform downloaden.

>[!TIP]
>
>Er wordt automatisch een configuratiebestand voor uw app opgenomen in de SDK-download, zodat u dat bestand niet afzonderlijk hoeft te downloaden. Als u de SDK echter al hebt gedownload en u wilt de bijgewerkte instellingen ophalen, downloadt u het configuratiebestand opnieuw.

Als u Android Studio gebruikt, kunt u ook het volgende toevoegen aan de apps van uw app `build.gradle` bestand:

```java
compile 'com.adobe.mobile:adobeMobileLibrary:4.13.7'
```

De volgende informatie onthouden:

* Vervang het versienummer in het codevoorbeeld door de juiste versie van de Android-SDK&#39;s.
* Download het configuratiedossier en neem het in uw project op.
