---
description: U kunt een nieuwe koppelingsbestemming maken die gebruikers naar een web of een diepe koppeling in uw app stuurt.
keywords: mobiel
solution: Experience Cloud Services,Analytics
title: Nieuw koppelingsdoel maken
topic-fix: Metrics
uuid: 390e3dea-0221-4f97-980d-a90ca9f162fa
exl-id: 2d2f5938-1461-43e2-a375-45c18afc9d5a
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# Een nieuw doel voor een koppeling maken {#create-new-link-destination}

U kunt een nieuwe koppelingsbestemming maken die gebruikers naar een web of een diepe koppeling in uw app stuurt.

1. Klik in de gebruikersinterface van Mobile Services op **[!UICONTROL Manage Apps]**.
1. Klik op de naam van de app om de bijbehorende pagina App Information weer te geven.
1. Klik op **[!UICONTROL Manage Link Destinations]**.
1. Klik op **[!UICONTROL Create New]**.
1. Typ gegevens in de volgende velden:
   * **[!UICONTROL Title]**

      Typ een beschrijvende naam voor de bestemming van de App Link. De titelvertoningen slechts op de Manage pagina van de Doelen van de Verbinding in de Diensten UI van Adobe Mobile. Een beschrijvende naam helpt u of anderen in uw organisatie om snel een specifieke verbindingsbestemming te vinden en kan inzicht in zijn doel verstrekken.

   * **[!UICONTROL Link Type]**

      Hier volgt een lijst met de beschikbare typen koppelingen:

      * **[!UICONTROL App Deep Link]**

         Een diepe koppeling naar het URI-schema opgeven (bijvoorbeeld `yourapp://section`). Verbindbestemmingen van de app zijn diepe verbindingen van het schema van URI die gebruikers aan een diepe verbinding in uw app leiden. U kunt gebruikers bijvoorbeeld naar een specifieke productlijn in de mobiele app van een online detailhandelaar leiden.

      * **[!UICONTROL Web Link]**

         Typ bijvoorbeeld een web-HTTP- of HTTPS-URL.`https://adobe.com`. Webkoppelingsdoelen leiden gebruikers naar een URL. U kunt gebruikers bijvoorbeeld naar een productlijn op de website van een online detailhandelaar leiden.

      * **[!UICONTROL Hybrid Link]**

         Typ een iOS Universal Link of een Android App Link (bijvoorbeeld `https://yourwebsite.com`). Hybride koppelingen ondersteunen iOS Universal Links of Android App Links.
   * **[!UICONTROL App]**
Selecteer de app die is gekoppeld aan de koppeling die u wilt opgeven.

      >[!TIP]
      >
      >Deze informatie is alleen vereist als u een Deep Link voor app of een Hybride Link hebt geselecteerd in **[!UICONTROL Link Type]**. Als de app niet in de selectielijst wordt weergegeven, klikt u op **[!UICONTROL Add New App]** om te verwijzen naar een nieuwe app uit een App Store.

   * **[!UICONTROL Link type]**

      Typ de werkelijke URL voor de geselecteerde koppeling. Het label van dit veld is afhankelijk van het type koppeling dat u hebt geselecteerd.

   * **[!UICONTROL Notes]**

      Typ optionele notities voor uw doel. De extra nota&#39;s tonen slechts op de Manage pagina van de Doelen van de Verbinding in de Diensten UI van Adobe Mobile. De extra nota&#39;s kunnen u of anderen in uw organisatie snel helpen een specifieke verbindingsbestemming vinden en kunnen inzicht in zijn doel, de campagne verstrekken waaraan het wordt gebonden, of iets anders verstrekken dat u belangrijk vindt.


1. Klikken **Opslaan**.
