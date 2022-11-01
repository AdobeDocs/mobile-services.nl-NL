---
description: U kunt marketingkoppelingen maken om nieuwe gebruikers van mobiele apps direct aan te schaffen door de URL-parameters handmatig te configureren.
keywords: mobiel
solution: Experience Cloud Services,Analytics
title: Koppelingen voor overname handmatig maken
topic-fix: Metrics
uuid: d7709203-f793-4982-adaa-9c3c914aca2b
exl-id: aef9fe3e-32dc-4ec0-9eda-f64cc5e486a3
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# Koppelingen voor overname handmatig maken {#create-acquisition-link-manually}

{#eol}

U kunt marketingkoppelingen maken om nieuwe gebruikers van mobiele apps direct aan te schaffen door de URL-parameters handmatig te configureren.

>[!IMPORTANT]
>
>Voor deze functie is SDK-versie 4.6 of hoger vereist. Zie voor meer informatie [Verwervingsvoorwaarden](/help/using/acquisition-main/c-acquisition-prerequisites.md).

Het volgende diagram illustreert de componenten van een manueel gebouwde het volgen verbinding en toont de verschillende parameters URL die u moet behoorlijk vormen wanneer manueel het creëren van verwervingsverbindingen.

![](assets/acquisition_url.png)

Deze koppeling is geconfigureerd om een platformspecifieke omleiding uit te voeren naar de Google Play Store of de Apple App Store voor een mobiele app. Als het doel niet kan worden bepaald, is de standaardopslag geplaatst aan Apple App Store. Nadat de app is geïnstalleerd, wordt de `my.custom.key:test` De aangepaste contextsleutel is gekoppeld aan de Analytics Install Hit.

Gebruik de volgende URL-indeling om handmatig koppelingen te maken:

`http(s)://c00.adobe.com/v3/ {mobile-services-app-hash}/start? {parameters}`

>[!TIP]
>
>De versie van de Android-SDK die u gebruikt, heeft geen invloed op dit proces.

Voor iOS moet u het juiste protocol gebruiken:

* Gebruiken **HTTP** als u de SDK&#39;s van iOS vóór versie 4.7.0 gebruikt, of als u SDK 4.7.0 of hoger van iOS gebruikt, en als **[!UICONTROL Use HTTPS]** is **niet** geselecteerd op de pagina Toepassingsinstellingen beheren.
* Gebruiken **HTTPS** als u iOS SDK 4.7.0 of hoger gebruikt en **[!UICONTROL Use HTTPS]** **is** geselecteerd op de pagina Toepassingsinstellingen beheren.

Wanneer aan de volgende voorwaarden is voldaan:

* `{mobile-services-app-hash}` komt overeen met de toepassings-id in de configuratie `acquisition:appid ` bestand.

   U kunt zoeken `{mobile-services-app-hash}` op de pagina App Settings beheren onder Acquisition SDK Options in het veld Tracking ID.

   ![](assets/tracking-id.png)

* `{parameters}` is een lijst van standaard specifiek genoemde URL vraagparameters.

Hier volgt een lijst met parameters:

* **`a_g_id`**

   Google Play Store App Identifier.

   * Samplewaarde: `com.adobe.beardcons`

* **`a_g_lo`**

   Landinstelling Google Play Store overschrijven.

   * Samplewaarde: `ko`

* **`a_i_id`**

   iTunes App Identifier.

   * Samplewaarde: `835196493`

* **`a_i_lo`**

   Landinstelling iTunes overschrijven.

   * Samplewaarde: `jp`

* **`a_dd`**

   Standaardwinkel voor automatische omleiding.

   * Samplewaarde: `i | g`

* **`a_cid`**

   Aangepaste id overschrijven (doorgaans IDFA voor iOS of ADID voor Android).

   * Samplewaarde: `Any String < 255 characters (UTF-8 encoded)`

* **`ctx*`**

   Toetsen vooraf ingesteld met `ctx` zal in de contextgegevens van de resulterende lanceringshit zijn.

   * Samplewaarde: `ctxmy.custom.key=myValue`

* **`ctxa.referrer.campaign.name`**

   Naam van verwervingscampagne.

   Deze parameter is vereist voor rapportage als u de prestaties van verschillende verwervingskoppelingen wilt vergelijken.

   * Samplewaarde: Conferentie van de Top van 2015

* **`ctxa.referrer.campaign.trackingcode`**

   Trackingcode

   Deze parameter is vereist voor rapportage als u de prestaties van verschillende verwervingskoppelingen wilt vergelijken.

   * Samplewaarde: `lexsxouj`

* **`ctxa.referrer.campaign.source`**

   De bron.

   * Samplewaarde: Advertentienetwerk

* **`ctxa.referrer.campaign.medium`**

   Normaal

   * Samplewaarde: E-mail

* **`ctxa.referrer.campaign.content`**

   Inhoud

   * Samplewaarde: Afbeeldingsnummer 325689

* **`ctxa.referrer.campaign.term`**

   Term

   * Samplewaarde: wandelschoenen


Houd rekening met de volgende informatie wanneer u handmatig verwervingskoppelingen maakt:

* Alle parameters die niet overeenkomen met parameters in de tabel worden doorgegeven als onderdeel van de omleiding van de App Store.
* Alle parameters zijn technisch facultatief, hoewel de verbinding niet functioneel zal zijn, als minstens één opslagidentiteitskaart wordt gespecificeerd.

   Een voorbeeld van een winkel-id is `a_g_id`/ `a_i_id`.

* Als de bestemmingsopslag niet automatisch kan worden bepaald, en geen gebrek wordt verstrekt, is een fout 404 teruggekeerd.
