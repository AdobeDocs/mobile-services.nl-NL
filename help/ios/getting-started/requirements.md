---
description: Voer de volgende stappen uit om een rapportsuite te configureren voor het verzamelen van gegevens over iOS-apps.
solution: Experience Cloud Services,Analytics
title: Voordat u begint
topic-fix: Developer and implementation
uuid: 04133f68-3618-41fd-8a13-aec5b6f04df6
exl-id: 83da7cf5-3211-484d-bfe8-7b3b4999eea2
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 3%

---

# Voordat u begint {#before-you-start}

Voer de volgende stappen uit om een rapportsuite te configureren voor het verzamelen van gegevens over iOS-apps.

## Rolspecifieke taken {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analysebeheerders en toepassingsontwikkelaars moeten de volgende taken uitvoeren:

### Analysebeheerders

Een rapportsuite configureren en gegevens van mobiele apps verzamelen:

1. Een van de secties in [Aanmelden bij de gebruikersinterface van Adobe Mobile Services](/help/ios/getting-started/getting-started.md).
1. Maak een analyseaccount voor elke ontwikkelaar van de app.

App-ontwikkelaars hebben nu toegang tot de rapportsuite(s) die u hebt gemaakt.

>[!IMPORTANT]
>
>Als u een nieuwe rapportsuite wilt maken en SDK&#39;s wilt downloaden, moet u een analysebeheerder zijn.

### App-ontwikkelaars

1. Controleer of de beheerder van de Analytics de stappen in het dialoogvenster *Analysebeheerders* hierboven.

1. Controleer of uw beheerder van Analytics een van de secties in het dialoogvenster *Aanmelden bij de gebruikersinterface van Adobe Mobile Services* hieronder.
1. Nadat de rapportreeks is gevormd, voltooi stappen in *De SDK downloaden* hieronder.

Voor meer informatie over rollen en toestemmingen, zie [Rollen en machtigingen](/help/using/gs/c-mob-roles-and-permissions.md).

## Aanmelden bij de gebruikersinterface van Adobe Mobile Services {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile-services is de primaire rapportageinterface voor analyses en doelwitten van mobiele apps. Nadat u deze stappen voltooit kunt u een configuratiedossier downloaden dat met uw server van de gegevensinzameling, rapportreeks, en vele andere montages vooraf wordt gevormd.

U kunt zich op een van de volgende manieren aanmelden bij de Adobe Mobile Services:

* **Experience Cloud**

   Aanmelden bij de [Experience Cloud](https://experience.adobe.com) met uw Adobe ID.

   Bij deze methode wordt ervan uitgegaan dat uw bedrijf is ingericht en dat u een koppeling hebt gemaakt tussen uw account voor Analytics. Voor meer informatie over levering, zie [Gebruikers en producten van Experience Cloud beheren](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html) in de handleiding Experience Cloud Central Interface Components. Ga voor meer informatie over het koppelen van uw account naar [Organisaties in de Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html).

   >[!TIP]
   >
   >Als u niet zeker weet of uw bedrijf provisioned in de Experience Cloud is, gebruik uw bestaande rekening van Adobe Analytics.

* **Adobe Analytics**

   Klikken **[!UICONTROL Sign in with Analytics]** en voer uw bedrijfsnaam, gebruikersnaam en wachtwoord voor Analytics in.

## Een rapportsuite maken {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Een rapportsuite maken om toepassingsgegevens te verzamelen en een app te definiëren:

1. Klik op **[!UICONTROL Create New App]**.

   Als deze knop niet wordt weergegeven, klikt u op **[!UICONTROL Manage Apps]** > **[!UICONTROL Add]**.

1. In de **[!UICONTROL Report Suite]** vervolgkeuzelijst, selecteert u **[!UICONTROL New Report Suite]**.

1. Voer de naam van uw app in en selecteer een unieke rapportsuite-id.

   Een voorbeeld van een rapportsuite-id is `mycomobileappdev`. U moet afzonderlijke rapportensuites en apps voor de ontwikkelings en productieversies opzetten. Herhaal deze stappen als u klaar bent om de productieversie in te stellen.
1. Verlaten **[!UICONTROL Mobile App Template]** geselecteerd.

   Met deze sjabloon kunnen tijdstempels offline gegevens verzamelen en worden de variabelen van de mobiele oplossing geactiveerd om levenscyclusmetriek vast te leggen.

1. Selecteer uw **[!UICONTROL Timezone]**, uw **[!UICONTROL Currency]** en klik op **[!UICONTROL Save]**.

## De SDK downloaden {#section_044C17DF82BC4FD8A3E409C456CE9A46}

De mobiele SDK downloaden:

1. Meld u aan bij Mobile Services en open uw app op een van de volgende manieren:

   * In de **[!UICONTROL All Apps]** selecteert u uw app.
   * Zoek in het rechterdeelvenster naar de toepassing en open deze.

1. Klik op **[!UICONTROL Manage App Settings]**.
1. In de **[!UICONTROL App SDK Downloads]** sectie, naar de **[!UICONTROL App SDK Downloads]** sectie.

1. Download de SDK en de voorbeeldapp voor uw platform.

>[!TIP]
>
>Er wordt automatisch een configuratiebestand voor uw app opgenomen in de SDK-download, zodat u dat bestand niet afzonderlijk hoeft te downloaden. Als u de SDK echter al hebt gedownload en u wilt de bijgewerkte instellingen ophalen, downloadt u het configuratiebestand opnieuw.
