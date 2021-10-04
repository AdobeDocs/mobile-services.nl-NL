---
description: Het volgen van de verwerving moet in de configuratie van SDK worden toegelaten alvorens u op de Koppelingen van de Marketing kunt volgen en rapporteren.
keywords: mobiel
solution: Experience Cloud,Analytics
title: Verwerving configureren
topic-fix: Metrics
uuid: e996e43e-8a77-47a3-a6fb-53f676f92bef
exl-id: 3a12dfab-70d0-41e6-8d4e-5aba21bb8606
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Verwerving configureren {#configure-acquisition}

Het volgen van de verwerving moet in de configuratie van SDK worden toegelaten alvorens u op de Koppelingen van de Marketing kunt volgen en rapporteren.

1. Schuif op de pagina Toepassingsinstellingen beheren voor de app naar de sectie **[!UICONTROL SDK Acquisition Options]**.
1. Voer de volgende taken uit:

   * Schakel het selectievakje **[!UICONTROL Enable]** in om de overname in te schakelen.

      Als u dit selectievakje inschakelt, wordt het veld **[!UICONTROL Referrer Timeout]** geactiveerd en verandert de waarde van 0 in 5.

   * Geef een waarde op in het veld **[!UICONTROL Referrer Timeout (seconds)]**

      (**Optioneel**) Als u het selectievakje **[!UICONTROL Enable]** hebt ingeschakeld, is dit veld optioneel. U kunt de time-outwaarde wijzigen, die in seconden wordt opgegeven. Met deze instelling geeft u de periode op waarin moet worden gewacht tot er informatie over de overname is opgehaald voordat de hit First Launch wordt verzonden.
   >[!IMPORTANT]
   >U moet een waarde invoeren die niet gelijk is aan nul. Als u Acquisition inschakelt maar de waarde nul laat, werken Acquisition-koppelingen niet. We raden u aan de standaardwaarde van 5 seconden te gebruiken.

1. Download en gebruik het nieuwe SDK-configuratiebestand in uw app.

   U hebt Opname geconfigureerd op **iOS**.
Als u overnames wilt inschakelen op **Android**, voert u de stappen in [Mobiele overnames bijhouden](/help/android/acquisition-main/acquisition.md) uit.
