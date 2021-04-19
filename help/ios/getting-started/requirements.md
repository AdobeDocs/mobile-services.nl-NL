---
description: Voer de volgende stappen uit om een rapportsuite te configureren voor het verzamelen van iOS-toepassingsgegevens.
seo-description: Voer de volgende stappen uit om een rapportsuite te configureren voor het verzamelen van iOS-toepassingsgegevens.
seo-title: Voordat u begint
solution: Experience Cloud,Analytics
title: Voordat u begint
topic-fix: Developer and implementation
uuid: 04133f68-3618-41fd-8a13-aec5b6f04df6
exl-id: 83da7cf5-3211-484d-bfe8-7b3b4999eea2
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 4%

---

# Voordat u {#before-you-start} start

Voer de volgende stappen uit om een rapportsuite te configureren voor het verzamelen van iOS-toepassingsgegevens.

## Rolspecifieke taken {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analysebeheerders en toepassingsontwikkelaars moeten de volgende taken uitvoeren:

### Analysebeheerders

Een rapportsuite configureren en gegevens van mobiele apps verzamelen:

1. Voltooi een van de secties in [Meld u aan bij de gebruikersinterface van Mobiele Adobe-services](/help/ios/getting-started/getting-started.md).
1. Maak een analyseaccount voor elke ontwikkelaar van de app.

App-ontwikkelaars hebben nu toegang tot de rapportsuite(s) die u hebt gemaakt.

>[!IMPORTANT]
>
>Als u een nieuwe rapportsuite wilt maken en SDK&#39;s wilt downloaden, moet u een analysebeheerder zijn.

### App-ontwikkelaars

1. Controleer of de beheerder van de Analyse de stappen in de sectie *Analysebeheerders* hierboven heeft uitgevoerd.

1. Verifieer dat uw beheerder van Analytics één van de secties in *login aan de Mobiele Diensten UI van de Adobe heeft voltooid UI* hieronder.
1. Nadat de rapportreeks is gevormd, voltooi stappen in *Download SDK* hieronder sectie.

Voor meer informatie over rollen en toestemmingen, zie [Rollen en Toestemmingen](/help/using/gs/c-mob-roles-and-permissions.md).

## Aanmelden bij de gebruikersinterface van Adobe Mobile Services {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile-services is de primaire rapportageinterface voor analyses en doelwitten van mobiele apps. Nadat u deze stappen voltooit kunt u een configuratiedossier downloaden dat met uw server van de gegevensinzameling, rapportreeks, en vele andere montages vooraf wordt gevormd.

U kunt zich op een van de volgende manieren aanmelden bij de Adobe Mobile Services:

* **Experience Cloud**

   Meld u aan bij [Experience Cloud](https://marketing.adobe.com) met uw Adobe ID.

   Bij deze methode wordt ervan uitgegaan dat uw bedrijf is ingericht en dat u een koppeling hebt gemaakt tussen uw account voor Analytics. Zie [Gebruikers en producten van Experience Cloud beheren](https://docs.adobe.com/content/help/nl-NL/core-services/interface/manage-users-and-products/admin-getting-started.html) voor meer informatie over provisioning. Zie [Organisaties en account linking](https://docs.adobe.com/content/help/nl-NL/core-services/interface/manage-users-and-products/organizations.html) voor meer informatie over het koppelen van uw account.

   >[!TIP]
   >
   >Als u niet zeker weet of uw bedrijf provisioned in de Experience Cloud is, gebruik uw bestaande rekening van Adobe Analytics.

* **Adobe Analytics**

   Klik **[!UICONTROL Sign in with Analytics]** en ga uw het bedrijfsnaam van Analytics, uw gebruikersbenaming, en uw wachtwoord in.

## Een rapportsuite maken {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Een rapportsuite maken om toepassingsgegevens te verzamelen en een app te definiëren:

1. Klik op **[!UICONTROL Create New App]**.

   Als deze knop niet wordt weergegeven, klikt u op **[!UICONTROL Manage Apps]** > **[!UICONTROL Add]**.

1. Selecteer **[!UICONTROL New Report Suite]** in de vervolgkeuzelijst **[!UICONTROL Report Suite]**.

1. Voer de naam van uw app in en selecteer een unieke rapportsuite-id.

   Een voorbeeld van een rapportsuite-id is `mycomobileappdev`. U moet afzonderlijke rapportensuites en apps voor de ontwikkelings en productieversies opzetten. Herhaal deze stappen als u klaar bent om de productieversie in te stellen.
1. Laat **[!UICONTROL Mobile App Template]** geselecteerd.

   Met deze sjabloon kunnen tijdstempels offline gegevens verzamelen en worden de variabelen van de mobiele oplossing geactiveerd om levenscyclusmetriek vast te leggen.

1. Selecteer **[!UICONTROL Timezone]**, uw **[!UICONTROL Currency]**, en klik **[!UICONTROL Save]**.

## SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46} downloaden

De mobiele SDK downloaden:

1. Meld u aan bij Mobiele services en open uw app op een van de volgende manieren:

   * Selecteer uw toepassing in de vervolgkeuzelijst **[!UICONTROL All Apps]**.
   * Zoek in het rechterdeelvenster naar de toepassing en open deze.

1. Klik op **[!UICONTROL Manage App Settings]**.
1. Blader in de sectie **[!UICONTROL App SDK Downloads]** naar de sectie **[!UICONTROL App SDK Downloads]**.

1. Download de SDK en de voorbeeldapp voor uw platform.

>[!TIP]
>
>Er wordt automatisch een configuratiebestand voor uw app opgenomen in de SDK-download, zodat u dat bestand niet afzonderlijk hoeft te downloaden. Als u de SDK echter al hebt gedownload en u wilt de bijgewerkte instellingen ophalen, downloadt u het configuratiebestand opnieuw.
