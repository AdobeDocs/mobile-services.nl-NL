---
description: U kunt signalen verzenden en bezoekerssegmenten van publieksbeheer terugwinnen.
keywords: android;library;mobile;sdk
seo-description: U kunt signalen verzenden en bezoekerssegmenten van publieksbeheer terugwinnen.
seo-title: Configuratie van Auditiebeheer
solution: Marketing Cloud,Analytics
title: Configuratie van Auditiebeheer
topic: Developer and implementation
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Configuratie van Auditiebeheer{#audience-manager-configuration}

U kunt signalen verzenden en bezoekerssegmenten van de Manager van het Publiek terugwinnen.

## De toepassingscontext instellen {#section_37CAE496FF894FCA821F7760605574CA}

**(Vereist)** De `setContext()` methode moet eenmaal worden aangeroepen in de `onCreate()` methode van uw hoofdactiviteit.

Hier volgt het codevoorbeeld voor deze methode:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Als u deze methodevraag toevoegde toen u Analytics of Doel uitvoerde, te hoeven u niet het opnieuw toe te voegen.
