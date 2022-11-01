---
description: U kunt de opties voor SDK-analyse configureren op de pagina Toepassingsinstellingen beheren terwijl u een nieuwe app maakt of een bestaande app bewerkt.
keywords: mobiel
solution: Experience Cloud Services,Analytics
title: Opties voor SDK-analyse configureren
topic-fix: Metrics
uuid: fd3a21d2-6560-4e96-92fe-b99caac5e834
exl-id: f2c35b65-1052-4bfc-af9d-8778e4ff0522
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Opties voor SDK-analyse configureren {#configure-sdk-analytics-options}

{#eol}

U kunt de opties voor SDK-analyse configureren op de pagina Toepassingsinstellingen beheren terwijl u een nieuwe app maakt of een bestaande app bewerkt.

Typ informatie in de volgende velden onder **[!UICONTROL SDK Analytics Options]**:

* **[!UICONTROL Use HTTPS]**

   HTTPS inschakelen voor extra beveiliging.

* **[!UICONTROL Backdate Session Hits]**

   Schakel de mogelijkheid voor de Adobe-SDK in of uit om sessieinfo-hits te herstellen. Sessieinfo-hits bestaan momenteel uit vastlopen en sessielengte. Als deze optie is ingeschakeld, wordt de sessie-info teruggezet naar 1 seconde na de laatste treffer van de vorige sessie. Dit betekent dat crashes en sessiegegevens correleren met de juiste datum waarop ze zijn gebeurd. Bij elke nieuwe start van de toepassing wordt een hit hersteld. Als deze optie is uitgeschakeld, voegt de Adobe SDK de sessiegegevens toe aan de huidige levenscyclus.

* **[!UICONTROL Privacy]**

   Selecteer een privacyoptie:

   * **[!UICONTROL Send Data Until Opt-Out]**
   * **[!UICONTROL Hold Data Until Opt-In]**

* **[!UICONTROL Session Timeout (Seconds)]**

   Geef de time-outwaarde voor de sessie op.

   De standaardwaarde is 300 seconden. Hiermee geeft u de tijdsduur in seconden op die moet verstrijken tussen het starten van de app voordat de start als een nieuwe sessie wordt beschouwd. Deze time-out is ook van toepassing wanneer uw toepassing naar de achtergrond wordt verzonden en opnieuw wordt geactiveerd. De tijd die uw toepassing op de achtergrond doorbrengt, wordt niet opgenomen in de sessieduur.

* **[!UICONTROL Batch Limit]**

   Geef op hoeveel treffers u in de wachtrij wilt plaatsen voordat u gegevens verzendt.

   Stel dit in op 0 om direct hits te verzenden. De partijgrens vertegenwoordigt de drempel voor aantal treffers die in opeenvolgende vraag moeten worden verzonden. Als deze optie bijvoorbeeld is ingesteld op 10, wordt elke hit vóór de tiende hit opgeslagen in de wachtrij. Wanneer de 10e hit binnenkomt, worden alle 10 hits opeenvolgend verzonden.

* **[!UICONTROL More Details]**

   Klik op de knop **[!UICONTROL More Details]** De verbinding om de identiteitskaart van de rapportreeks en het volgen server te bekijken, laat of maakt off-line het volgen, en bekijkt het karakter het coderen model toe dat (zoals UTF-8) wordt gebruikt.

   Wanneer offline bijhouden is ingeschakeld, worden gegevens die door het apparaat worden gegenereerd terwijl ze offline zijn, voorzien van een tijdstempel en later verzonden. Als deze optie is uitgeschakeld, worden offlinegegevens verwijderd.
