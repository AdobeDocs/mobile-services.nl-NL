---
description: Een virtuele rapportreeks (VRS) is een rapportreeks die door één of meerdere segmentdefinitie op een rapportreeks wordt gecreeerd toe te passen. Dit staat gebruikers toe om hun gegevens in één rapportreeks te handhaven maar de gegevens te beheren alsof het in afzonderlijke rapportseries was.
seo-description: Een virtuele rapportreeks (VRS) is een rapportreeks die door één of meerdere segmentdefinitie op een rapportreeks wordt gecreeerd toe te passen. Dit staat gebruikers toe om hun gegevens in één rapportreeks te handhaven maar de gegevens te beheren alsof het in afzonderlijke rapportseries was.
seo-title: Virtuele rapportsets
title: Virtuele rapportsets
uuid: 3f467cad-43e7-4cd0-889b-89f8c61febbd
translation-type: tm+mt
source-git-commit: 814c99695f538160ae28484ca8e2a92f5b24bb1a

---


# Virtuele rapportsuites {#virtual-report-suites}

Een virtuele rapportreeks (VRS) is een rapportreeks die door één of meerdere segmentdefinitie op een rapportreeks wordt gecreeerd toe te passen. Dit staat gebruikers toe om hun gegevens in één rapportreeks te handhaven, maar beheert de gegevens alsof het in afzonderlijke rapportseries was.

Toepassingen die VRS&#39;s gebruiken, doen hetzelfde als apps die een reguliere rapportsuite gebruiken, behalve voor het beheer van de volgende functies:

* Verwerkingsregels
* gebeurtenissen/props/listeners/gebeurtenissen
* Met tijdstempel ingeschakeld, optie
* Afmetingsmarkeringen (levenscyclus, locatie, enzovoort)
* Classificaties

Deze waarden worden beheerd in de ouderrapportreeks en met VRSs gedeeld die tot de zelfde ouderrapportreeks behoren.

De volgende gebieden zijn toegankelijk in de gebruikersinterface van Adobe Mobile Services, onafhankelijk van de bovenliggende rapportsuite:

* Het configuratiebestand
* Belangenpunten beheren
* Koppelingsdoelen beheren
* Postbacks beheren
* Berichtenkoppelingen
* Verwerving

Een VRS kan u helpen de volgende taken uitvoeren:

* Toegang tot gegevens beperken

   Een multinationaal bedrijf heeft een app die gegevens naar een rapportsuite voor alle geografische locaties verzendt. Nochtans, wil het bedrijf de bedrijfsgebruiker in één gebied beperken van het bekijken van de gegevens in een andere regio. De beheerder van het bedrijf kan een VRS tot stand brengen om gebruikers door gebied te segmenteren en toestemmingen aan VRS slechts aan de bedrijfsgebruiker te geven die het gebied beheert.

   Hierdoor wordt voorkomen dat zakelijke gebruikers gegevens weergeven die niet gerelateerd zijn aan hun regio. Zo hoeft een zakelijke gebruiker in het EMEA geen gegevens voor de APAC-regio te bekijken.

* Toestaan dat u controle hebt over berichten in de app/push, POI&#39;s voor locaties, aankopen en postbacks met alle gegevens die naar één rapportsuite worden verzonden.

   Een multinationaal bedrijf wil dat alle gegevens naar dezelfde rapportsuite voor alle geografische locaties worden verzonden. Nochtans, wil het bedrijf het marketing team van elke regio om hun eigen in-app/duw overseinen te behandelen. De beheerder van het bedrijf kan regionale VRSs tot stand brengen, en elk team kan hun eigen app leiden die op dat VRS wordt gebaseerd.

   Het regionale team bouwt hun app door het configuratiedossier van VRS te gebruiken. De gegevens worden naar de bovenliggende rapportsuite verzonden, maar in-app/push-berichten, locatie-POI&#39;s, acquisitie en postbacks worden beheerd in de toepassing die is gemaakt op basis van de VRS.

## Een virtuele rapportsuite maken in Adobe Analytics {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>Alleen Adobe Analytics-beheerders kunnen virtuele rapportsuites maken en wijzigen in Adobe Analytics. Zie Virtuele [rapportsuites](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html)maken als u een virtuele-rapportsuite wilt maken.

Elk VRS heeft een unieke id. Als u de id van de bovenliggende rapportsuite wilt weergeven in de gebruikersinterface van Adobe Mobile Services, klikt u in de **[!UICONTROL App Information]** sectie op de pagina Toepassingsinstellingen beheren op **[!UICONTROL More Details]**.

In de gebruikersinterface van Adobe Mobile Services kunt u een VRS gebruiken om een app te maken en gegevens te segmenteren naar een specifieke groep in uw organisatie. Op die manier kan een zakelijke gebruiker in Spanje bijvoorbeeld de gegevens die relevant zijn voor een zakelijke gebruiker in Japan niet zien.

>[!TIP]
>
>U kunt niet de waarden wijzigen die van de ouderrapportreeks worden geërft.

Een VRS is een server-side segmentdefinitie die aan een reeks van het ouderrapport in bijlage is. Dientengevolge, kunt u geen gegevensinzameling aan VRS uitvoeren, omdat SDK klusjes slechts naar de reeks van het ouderrapport verzendt, die beurtelings de klappen registreert.

## Virtuele rapportsuite in Adobe Mobile Services en gegevensverzameling {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

In Adobe Mobile Services kunt u een app maken op basis van een bovenliggende rapportsuite of een virtuele rapportsuite. Wanneer u een app maakt op basis van een virtuele rapportsuite, raden we u aan het VRS-segment uit te lijnen met de definitie van de app.

>[!TIP]
>
>Push-certificeringen worden gekoppeld op toepassingsniveau in de gebruikersinterface voor mobiele services.

Om ervoor te zorgen dat uw pushberichten correct worden verzonden, moet het publiekssegment correct zijn gedefinieerd. Zie [Publiek voor meer informatie: Bepaal en vorm de Segmenten van het Publiek voor de Duw Berichten](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## Tijdzones {#section_498E1EED22D741C3BDED44F01FACA72A}

De eigenschap tijdzone op de pagina Toepassingsinstellingen beheren wijkt af van de eigenschap tijdzone die u gebruikt om de vrijwillige VRS te maken in Adobe Analytics. De eigenschap op de pagina Toepassingsinstellingen beheren wordt overgenomen van de bovenliggende rapportsuite die wordt gebruikt om gegevens naar Adobe Analytics te verzenden. De eigenschap die u opgeeft wanneer u de VRS maakt in Adobe Analytics, wordt gebruikt om de rapporten weer te geven in de gebruikersinterface voor mobiele services. Deze eigenschap kan anders zijn dan de bovenliggende rapportsuite.

## Selecteer een virtuele rapportsuite in de gebruikersinterface voor mobiele services {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

Als u een VRS wilt gebruiken wanneer u een app maakt, selecteert u de VRS in de **[!UICONTROL Report Suite]** vervolgkeuzelijst op de pagina App Information. Deze lijst bevat bovenliggende en virtuele rapporteringssuites.

>[!IMPORTANT]
>
>Als u een VRS in de lijst wilt selecteren, zoekt u een optie met de blauwe stip en de `vrs_`*`<company_name>`* `_` *`<unique name>`* naamgevingsconventie.

## Eigenschappen van Virtual Report Suite {#section_20ECE6243F664C4FB4347ADB4FF0458A}

Hier volgen de eigenschappen voor VRS&#39;s:

>[!TIP]
>
>De alleen-lezen eigenschappen worden overgenomen van de bovenliggende rapportsuite.

| Eigenschap | Overgenomen van de bovenliggende rapporteringssuite | Bewerkbaar? | Notities |
|--- |--- |--- |--- |
| `target.clientCode` | Nee | Ja |  |
| `target.timeout` | Nee | Ja |  |
| `audienceManager.server` | Nee | Ja |  |
| `audienceManager.analyticsForwardingEnabled` | Ja | Ja |  |
| `audienceManager.timeout` | Nee | Ja |  |
| `acquisition.server` | Nee | Nee |  |
| `acquisition.appid` | Nee | Nee |  |
| `analytics.rsids` | Ja | Nee |  |
| `analytics.server` | Nee | Nee |  |
| `analytics.ssl` | Nee | Ja |  |
| `analytics.offlineEnabled` | Ja |  |  |
| `analytics.charset` | Ja | Nee |  |
| `analytics.lifecycleTimeout` | Nee | Ja | Dit moet de bovenliggende rapporteringssuite zijn als gebruikers niet willen dat hun gegevens inconsistent zijn. |
| `analytics.privacyDefault` | Nee | Ja |  |
| `analytics.batchLimit` | Nee | Ja |  |
| `analytics.timezone` | Ja | Ja, wanneer u de app voor het eerst maakt. | Deze tijdzone-eigenschap wordt gebruikt om gegevens naar Adobe Analytics te verzenden en is anders dan de tijdzone-eigenschap die is ingesteld wanneer een VRS wordt gemaakt. |
| `analytics.timezoneOffset` | Ja | Nee |  |
| `analytics.referrerTimeout` | Nee | Ja |  |
| `analytics.backdateSessionInfo` | Ja | Ja |  |

## Aanvullende informatie {#section_4C4446F1FBE64F659BC0A2362C9F3E59}

Hier is wat extra informatie over virtuele rapportseries:

* Voor meer informatie over VRSs, zie [Virtuele Reeksen](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-about.html)van het Rapport.
* Voor meer informatie over de planning van een implementatie van VRS, zie het [Virtuele werkschema](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html)van de rapportreeks.