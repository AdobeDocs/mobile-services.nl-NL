---
description: U moet deze taken voltooien alvorens het Push Overseinen in toepassingen te vormen.
keywords: mobile
seo-description: U moet deze taken voltooien alvorens het Push Overseinen in toepassingen te vormen.
seo-title: Vereisten voor het inschakelen van pushberichten
solution: Marketing Cloud,Analytics
title: Vereisten voor het inschakelen van pushberichten
topic: Metrics
uuid: 194e6e07-b794-4152-a838-a4125c3292d4
translation-type: tm+mt
source-git-commit: 92b1e430293fbded666e8af3f01393898c0e5811

---


# Vereisten om pushberichten in te schakelen {#prerequisites-to-enable-push-messaging}

U moet deze taken voltooien alvorens pushberichten in uw toepassingen te vormen.

## De Experience Cloud voor uw bedrijf inschakelen

Adobe Analytics Company moet Experience Cloud enabled zijn. U kunt de status van uw Adobe-accountmanager verifiëren.

## De mobiele SDK installeren en configureren

* **De mobiele SDK installeren**

   Als u pushberichten wilt configureren, moet u ten minste versie 4.6 of hoger van de Mobile SDK downloaden en installeren. Zie SDK&#39;s [downloaden voor meer informatie](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/download-sdk.md).

* **Pushservices configureren**

   U moet de pushservices configureren in de Mobile SDK.
Zie de volgende inhoud voor meer informatie:

   * [Push Messaging in Android](/help/android/messaging-main/push-messaging/push-messaging.md)
   * [Push Messaging in iOS](/help/ios/messaging-main/push-messaging/push-messaging.md)

## Meld u aan bij de Mobile Core Service met uw Adobe-id

>[!IMPORTANT]
>
>Gebruikers die de functie Push Services willen gebruiken, moeten zich aanmelden bij de Mobile Core Service met hun Adobe-id en hun account Analytics moet aan hun Adobe-id zijn gekoppeld. De functie Push Services is niet beschikbaar als gebruikers zich aanmelden met hun bestaande Adobe Analytics-accounts.

Voer de volgende stappen uit als gebruikers geen Adobe-id hebben:

1. (**Experience Cloud Administrator**) Vraag gebruikers uit naar de Experience Cloud.

1. (**Gebruiker**) Maak een persoonlijke Adobe-id aan de hand van de instructies die u hebt ontvangen van de Experience Cloud-beheerder.

   Er wordt automatisch een e-mailbericht verzonden naar elke gebruiker nadat de beheerder de vorige stap heeft voltooid.

1. (**Gebruikers**) Meld u aan bij Mobile met hun Adobe-id.

## Gebruikersaccounts koppelen in de Experience Cloud

Elke gebruiker moet het account van de Analytics-oplossing koppelen vanuit de Experience Cloud-organisatie.

1. Als u zich met een Adobe-id wilt aanmelden bij de Experience Cloud, typt u [https://marketing.adobe.com](https://marketing.adobe.com) in een browser.

1. Selecteer in de rechterbovenhoek de bedrijfsnaam Analytics.

1. Klik **[!UICONTROL Add Organization]** en selecteer **[!UICONTROL Adobe SiteCatalyst/Adobe Social]** van de drop-down lijst.

1. Typ de bedrijfsnaam, uw gegevens van de nalatenschap voor het opgegeven bedrijf en klik op **[!UICONTROL Link Account]**.

   De Adobe-id is nu gekoppeld aan uw aanmeldingsgegevens voor uw account, bedrijf en account voor Analytics.

Voor meer informatie, zie de Verbinding van de Rekening van het Oplossen van [problemen](https://marketing.adobe.com/resources/help/en_US/mcloud/organizations.html).

## Pushservices en de SDK ID-service configureren in de mobiele gebruikersinterface

Voordat u de id-service voor uw app inschakelt, is de **[!UICONTROL Push Services]** sectie uitgeschakeld. Maar nadat u de dienst van identiteitskaart toelaat, wordt de sectie van de Diensten van de Duw toegelaten. Voor meer informatie over het toelaten van de dupdiensten, zie de dienstopties [van SDK](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-visitor.md)vormen ID.

>[!IMPORTANT]: U moet klikken **[!UICONTROL Save]** om uw wijzigingen op te slaan en de pushservices te vernieuwen.
>
>U kunt in elke rapportsuite één app store-app configureren voor Apple en één voor Google. Als u aanvullende apps nodig hebt, bijvoorbeeld één voor een productieomgeving en één voor een ontwikkelomgeving, stelt u een nieuwe app store-app en een nieuwe rapportsuite in voor elke omgeving.

* Sleep voor **Apple** de persoonlijke sleutel en/of het certificaat naar de gewenste plaats. Als uw persoonlijke sleutel met een wachtwoord is gecodeerd, typt u het wachtwoord.

   * Sleep voor de **persoonlijke sleutel** het bestand met de persoonlijke sleutel naar het vak.

      U kunt ook klikken **[!UICONTROL Browse]** om het bestand te selecteren. Dit bestand bevat de persoonlijke sleutel. Het certificaat kan ook in dit bestand worden opgenomen (`.p12`, `pkcs12`, `.pfx`, `.key`, `.pem`).

   * Typ het wachtwoord als het bestand met de persoonlijke sleutel voor het wachtwoord **voor de** persoonlijke sleutel is versleuteld.

      (Voorwaardelijk) Sleep voor het **certificaat** het certificaatbestand naar het vak. U kunt ook klikken **[!UICONTROL Browse]** om het bestand te selecteren. Dit veld is niet vereist als het bestand met de persoonlijke sleutel ook het certificaat bevat ( `.cert`, `.cer`, `.crt`, `.pem`).

* Geef voor **Google** de API-sleutel voor de app op.

   Klik **[!UICONTROL Test]** om te controleren of de app en de mobiele services correct zijn geconfigureerd. Deze optie is nuttig voor het zuiveren en het oplossen van problemen.

   Typ de pushtokens van het apparaat die u het bericht wilt verzenden. U kunt het bericht naar meerdere apparaten verzenden door tokens op te geven in een lijst met komma&#39;s als scheidingsteken.

   ![push-testbericht](assets/push_test_list.png)
