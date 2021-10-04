---
description: U kunt Adobe Target in uw TVML/TVJS-apps gebruiken door uw .xml-bestanden rechtstreeks te vervangen. Wijs gebieden van uw pagina aan die door de inhoud van het Doel moeten worden vervangen door het douaneADBTtarget element van XML te gebruiken.
title: Adobe Target voor TVML/TVJS
uuid: afd5a583-5266-43f2-8cb0-0ace89c53a57
exl-id: 9348d49c-2a5a-4ea0-b90d-99d446bd336a
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Adobe Target voor TVML/TVJS{#adobe-target-for-tvml-tvjs}

U kunt Adobe Target in uw TVML/TVJS-apps gebruiken door uw .xml-bestanden rechtstreeks te vervangen. Wijs gebieden van uw pagina aan die door de inhoud van het Doel moeten worden vervangen door het douaneADBTtarget element van XML te gebruiken.

>[!IMPORTANT]
>
>Voordat u het element `ADBTarget` in uw TVML-pagina&#39;s gebruikt, moet u de TVML/TVJS-app configureren voor gebruik van de tvOS SDK. Zie [Apple TV-implementatie met tvOS](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md) voor meer informatie.

## Aan de slag {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. Identificeer het `.xml` dossier waarin u uw plaats van het Doel wilt gebruiken.
1. Voeg een `ADBTarget` element aan het dossier als kind van `<document>` element toe.
1. Als het Doel er niet in slaagt om uw plaats te vinden Mbox, of het tijden uit, wordt de waarde tussen uw `<ADBTarget>` en `</ADBTarget>` markeringen gebruikt als standaardinhoud.

## Uw mbox in Doel configureren {#section_F2DA140C34B0421D976046F825B23123}

De geretourneerde inhoud van Target vervangt alle inhoud tussen `<ADBTarget>` en `</ADBTarget>`, inclusief beide `ADBTarget`-tags.

>[!TIP]
>
>U moet plannen wat u dienovereenkomstig wilt vervangen.

Het gebruik van hoofdletters en kleine letters kan eenvoudig zijn, zoals het vervangen van een tekenreekswaarde in een label of complex, zoals het vervangen van een hele pagina.

## Uw ADBTarget-element configureren {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

In het `ADBTarget` element, moet u de naam Mbox in het `mbox` bezit verstrekken. U kunt naar keuze douaneeigenschappen aan uw verzoek in het `customParameterName="customParameterValue"` formaat toevoegen.

* **`mbox`**

   Naam van uw locatie Mbox.

   * Type eigenschap: String
   * Deze eigenschap is vereist.

* **`id`**

   De bestellings-id.

   * Type eigenschap: String
   * Deze eigenschap is **niet** vereist.

* **`total`**

   Het totaal van de bestelling.

   * Type eigenschap: String
   * Deze eigenschap is **niet** vereist.

* **`purchasedProductIds`**

   Een door komma&#39;s gescheiden lijst met aangeschafte product-id&#39;s voor deze bestelling.

   * Hier volgt het codevoorbeeld voor deze eigenschap:


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * Type eigenschap: String
   * Deze eigenschap is **niet** vereist.

* **`mboxParameters`**

   Een lijst met sleutel-waardeparen voor `mboxParameters`. Elk item in deze tekenreeks wordt gescheiden door een puntkomma en sleutelwaarden worden gescheiden door een dubbele punt.

   * Hier volgt het codevoorbeeld voor deze eigenschap:

      ```objective-c
      mboxParameters="mboxparameterKey:mboxParameterValue;mboxParameterKey1:mboxParameterValue1;mboxParameterKey2:mboxParameterValue2"
      ```

   * Type eigenschap: String
   * Deze eigenschap is **niet** vereist.

* **`customParameterName`**

   De waarde van deze eigenschap is `customParameterValue`.

   * Type eigenschap: String
   * Deze eigenschap is **niet** vereist.


## Voorbeelden {#section_6D6D6E8C7FE147168FC30D83CBC06985}

### Voorbeeld 1

In het volgende voorbeeld wordt een `ADBTarget`-element op de pagina `LandingPage.xml.js` gebruikt om de inhoud van een waarschuwing te vervangen:

#### Doel configureren

Veronderstel dat u een plaats Mbox genoemd `landingPage` hebt en de aanbiedingsinhoud wordt geplaatst om het volgende te zijn:

```objective-c
<title>My cool landing page</title> 
<description>Thanks for coming to my page</description> 
```

#### LandingPage.xml.js configureren

* Hier volgt de configuratie voor landingPage.xml.js:

   ```js
   <alertTemplate> 
       <ADBTarget mbox="landingPage">  
           <title>TargetTestPage</title> 
           <description>Load fail or timeout (defaultContent)</description> 
       </ADBTarget>  
   </alertTemplate> 
   ```

* Als het verzoek aan Target succesvol is en uw aanbiedingsinhoud wordt teruggegeven, zal uw pagina met resulteren:

   ```objective-c
   <alertTemplate> 
       <title>My cool landing page</title> 
       <description>Thanks for coming to my page</description> 
   </alertTemplate>
   ```

* Als de doelserver niet kan worden bereikt of de aanvraagtijden zijn verstreken, resulteert de pagina in:

   ```objective-c
   <alertTemplate> 
       <title>TargetTestPage</title> 
       <description>Load fail or timeout (defaultContent)</description> 
   </alertTemplate>
   ```

### Voorbeeld 2

In het volgende voorbeeld wordt getoond hoe u aangepaste gegevens aan uw `ADBTarget`-element kunt toevoegen. Met deze methode kunt u voorwaardelijke ervaringen maken en inhoud aanbieden voor deze Mbox-locatie in Doel:

```objective-c
<alertTemplate> 
    <ADBTarget mbox="landingPage" customData="custom data" moreCustomData="more custom data"> 
        <title>TargetTestPage</title> 
        <description>Load fail or timeout (defaultContent)</description> 
    </ADBTarget>  
</alertTemplate>
```
