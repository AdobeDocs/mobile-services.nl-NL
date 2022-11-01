---
description: Het volgen van de verwerving moet in de configuratie van SDK worden toegelaten alvorens u op de Koppelingen van de Marketing kunt volgen en rapporteren.
keywords: mobiel
solution: Experience Cloud Services,Analytics
title: Verwerving configureren
topic-fix: Metrics
uuid: e996e43e-8a77-47a3-a6fb-53f676f92bef
exl-id: 3a12dfab-70d0-41e6-8d4e-5aba21bb8606
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Verwerving configureren {#configure-acquisition}

{#eol}

Het volgen van de verwerving moet in de configuratie van SDK worden toegelaten alvorens u op de Koppelingen van de Marketing kunt volgen en rapporteren.

1. Blader op de pagina Toepassingsinstellingen beheren voor de app naar de knop **[!UICONTROL SDK Acquisition Options]** sectie.
1. Voer de volgende taken uit:

   * Selecteer de optie **[!UICONTROL Enable]** selectievakje.

      Wanneer u dit selectievakje selecteert, wordt **[!UICONTROL Referrer Timeout]** wordt geactiveerd en de waarde verandert van 0 in 5.

   * Voer een waarde in het dialoogvenster **[!UICONTROL Referrer Timeout (seconds)]** field

      (**Optioneel**) Als u de optie **[!UICONTROL Enable]** selectievakje, is dit veld optioneel. U kunt de time-outwaarde wijzigen, die in seconden wordt opgegeven. Met deze instelling geeft u de periode op waarin moet worden gewacht tot er informatie over de overname is opgehaald voordat de hit First Launch wordt verzonden.
   >[!IMPORTANT]
   >U moet een waarde invoeren die niet gelijk is aan nul. Als u Acquisition inschakelt maar de waarde nul laat, werken Acquisition-koppelingen niet. We raden u aan de standaardwaarde van 5 seconden te gebruiken.

1. Download en gebruik het nieuwe SDK-configuratiebestand in uw app.

   U hebt Opname geconfigureerd op **iOS**.
