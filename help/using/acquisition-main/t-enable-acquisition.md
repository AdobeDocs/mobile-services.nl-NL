---
description: Het volgen van de verwerving moet in de configuratie van SDK worden toegelaten alvorens u op de Koppelingen van de Marketing kunt volgen en rapporteren.
keywords: mobile
seo-description: Het volgen van de verwerving moet in de configuratie van SDK worden toegelaten alvorens u op de Koppelingen van de Marketing kunt volgen en rapporteren.
seo-title: Verwerving configureren
solution: Experience Cloud,Analytics
title: Verwerving configureren
topic: Metrics
uuid: e996e43e-8a77-47a3-a6fb-53f676f92bef
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---


# Verwerving configureren {#configure-acquisition}

Het volgen van de verwerving moet in de configuratie van SDK worden toegelaten alvorens u op de Koppelingen van de Marketing kunt volgen en rapporteren.

1. Blader op de pagina Toepassingsinstellingen beheren voor de app naar de **[!UICONTROL SDK Acquisition Options]** sectie.
1. Voer de volgende taken uit:

   * Schakel het **[!UICONTROL Enable]** selectievakje in om de optie Verwerving in te schakelen.

      Wanneer u dit selectievakje inschakelt, wordt het **[!UICONTROL Referrer Timeout]** veld geactiveerd en verandert de waarde van 0 in 5.

   * Voer een waarde in het **[!UICONTROL Referrer Timeout (seconds)]** veld in

      (**Optioneel**) Als u het **[!UICONTROL Enable]** selectievakje hebt ingeschakeld, is dit veld optioneel. U kunt de time-outwaarde wijzigen, die in seconden wordt opgegeven. Met deze instelling geeft u de periode op waarin moet worden gewacht tot er informatie over de overname is opgehaald voordat de hit First Launch wordt verzonden.
   >[!IMPORTANT]
   >U moet een waarde invoeren die niet gelijk is aan nul. Als u Acquisition inschakelt maar de waarde nul laat, werken Acquisition-koppelingen niet. We raden u aan de standaardwaarde van 5 seconden te gebruiken.

1. Download en gebruik het nieuwe SDK-configuratiebestand in uw app.

   U hebt Opname geconfigureerd op **iOS**.
Voer de stappen voor het **bijhouden van mobiele overname** uit om overname op [Android](/help/android/acquisition-main/acquisition.md)in te schakelen.
