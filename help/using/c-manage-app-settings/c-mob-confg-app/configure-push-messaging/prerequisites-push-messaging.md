---
description: U moet deze taken voltooien alvorens het Push Overseinen in toepassingen te vormen.
keywords: mobiel
solution: Experience Cloud Services,Analytics
title: Vereisten voor het inschakelen van pushberichten
topic-fix: Metrics
uuid: 194e6e07-b794-4152-a838-a4125c3292d4
exl-id: 543155a4-f687-48a6-8690-5c8da8490c62
source-git-commit: dbe3af75010fbf5195a3f93fc43cb696aaa32b65
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 1%

---

# Vereisten om pushberichten in te schakelen {#prerequisites-to-enable-push-messaging}

U moet deze taken voltooien alvorens pushberichten in uw toepassingen te vormen.

## De Experience Cloud voor uw bedrijf inschakelen

Uw Adobe Analytics Company moet Experience Cloud toegelaten zijn. U kunt de status verifiëren van uw Adobe-accountmanager.

## De mobiele SDK installeren en configureren

* **De mobiele SDK installeren**

   Als u pushberichten wilt configureren, moet u ten minste versie 4.6 of hoger van de Mobile SDK downloaden en installeren. Zie voor meer informatie [SDK&#39;s downloaden](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/download-sdk.md).

* **Pushservices configureren**

   U moet de pushservices configureren in de Mobile SDK.

## Meld u aan bij de Mobile Core Service met uw Adobe ID

>[!IMPORTANT]
>
>Om de functionaliteit van de Diensten van de Duw te gebruiken moeten de gebruikers zich bij de Mobiele Dienst van de Kern aanmelden door hun Adobe ID te gebruiken en hun account van de Analytics moet met hun Adobe IDs worden verbonden. De functie Push Services is niet beschikbaar als gebruikers zich aanmelden met hun bestaande Adobe Analytics-accounts.

Voer de volgende stappen uit als gebruikers geen Adobe-id hebben:

1. (**Experience Cloud-beheerder**) Gebruikers uitnodigen voor de Experience Cloud.

1. (**Gebruiker**) Maak een persoonlijke Adobe ID aan de hand van de instructies die u van de beheerder van de Experience Cloud hebt ontvangen.

   Er wordt automatisch een e-mailbericht verzonden naar elke gebruiker nadat de beheerder de vorige stap heeft voltooid.

1. (**Gebruikers**) Meld u aan bij Mobile met de Adobe ID.

## Gebruikersaccounts koppelen in de Experience Cloud

Elke gebruiker moet de de oplossingsrekening van Analytics van de organisatie van Experience Cloud verbinden.

1. Aanmelden bij de [Adobe Experience Cloud](https://experience.adobe.com) met een Adobe ID.

1. Selecteer in de rechterbovenhoek de bedrijfsnaam Analytics.

1. Klikken **[!UICONTROL Add Organization]** en selecteert u **[!UICONTROL Adobe SiteCatalyst/Adobe Social]** in de vervolgkeuzelijst.

1. Typ de bedrijfsnaam, uw gegevens van de nalatenschap voor het opgegeven bedrijf en klik op **[!UICONTROL Link Account]**.

   De Adobe ID is nu gekoppeld aan uw aanmeldingsgegevens voor uw account, bedrijf en account voor Analytics.

Zie voor meer informatie [Organisaties in de Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=nl) in de handleiding Experience Cloud Central Interface Components.

## Pushservices en de SDK ID-service configureren in de mobiele gebruikersinterface

Voordat u de id-service voor uw app inschakelt, moet u **[!UICONTROL Push Services]** is uitgeschakeld. Maar nadat u de dienst van identiteitskaart toelaat, wordt de sectie van de Diensten van de Duw toegelaten. Voor meer informatie over het inschakelen van pushservices raadpleegt u [Opties voor SDK-id-services configureren](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-visitor.md).

>[!IMPORTANT]
>
>U moet op **[!UICONTROL Save]** om uw wijzigingen op te slaan en de pushservices te vernieuwen.
>
>U kunt één app store-app voor Apple en één voor Google configureren in elke rapportsuite. Als u aanvullende apps nodig hebt, bijvoorbeeld één voor een productieomgeving en één voor een ontwikkelomgeving, stelt u een nieuwe app store-app en een nieuwe rapportsuite in voor elke omgeving.

* Voor **Apple**, sleep en zet uw persoonlijke sleutel en/of certificaat neer. Als uw persoonlijke sleutel met een wachtwoord is gecodeerd, typt u het wachtwoord.

   * Voor de **Persoonlijke sleutel**, sleep het bestand met de persoonlijke sleutel naar het vak.

      U kunt ook op **[!UICONTROL Browse]** om het bestand te selecteren. Dit bestand bevat de persoonlijke sleutel. Het certificaat kan ook in dit bestand worden opgenomen (`.p12`, `pkcs12`, `.pfx`, `.key`, `.pem`).

   * Voor de **Wachtwoord persoonlijke sleutel** Als het persoonlijke-sleutelbestand gecodeerd is, typt u het wachtwoord.

      (Voorwaardelijk) Voor de **Certificaat**, sleept u het certificaatbestand naar het vak. U kunt ook op **[!UICONTROL Browse]** om het bestand te selecteren. Dit veld is niet vereist als het bestand met de persoonlijke sleutel ook het certificaat bevat ( `.cert`, `.cer`, `.crt`, `.pem`).

* Voor **Google**, geeft u de API-sleutel voor de app op.

   Klikken **[!UICONTROL Test]** om te controleren of de app en de mobiele services correct zijn geconfigureerd. Deze optie is nuttig voor het zuiveren en het oplossen van problemen.

   Typ de pushtokens van het apparaat die u het bericht wilt verzenden. U kunt het bericht naar meerdere apparaten verzenden door tokens op te geven in een lijst met komma&#39;s als scheidingsteken.

   ![push-testbericht](assets/push_test_list.png)
