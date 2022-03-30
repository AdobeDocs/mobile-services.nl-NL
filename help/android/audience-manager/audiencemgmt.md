---
description: U kunt signalen verzenden en bezoekerssegmenten van publieksbeheer terugwinnen.
keywords: android;bibliotheek;mobile;sdk
solution: Experience Cloud Services,Analytics
title: Configuratie van Audience Manager
topic-fix: Developer and implementation
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
exl-id: 05033748-5461-482f-a01d-1ba73f64616a
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 10%

---

# Configuratie van Audience Manager{#audience-manager-configuration}

U kunt signalen verzenden en bezoekerssegmenten van Audience Manager terugwinnen.

## De toepassingscontext instellen {#section_37CAE496FF894FCA821F7760605574CA}

**(Vereist)** De `setContext()` Deze methode moet in het dialoogvenster `onCreate()` methode van uw hoofdactiviteit.

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
