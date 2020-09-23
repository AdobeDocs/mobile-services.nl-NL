---
description: U kunt gerichte inhoud leveren in Android-toepassingen.
keywords: android;library;mobile;sdk
seo-description: U kunt gerichte inhoud leveren in Android-toepassingen.
seo-title: Doelconfiguratie
solution: Experience Cloud,Analytics
title: Doelconfiguratie
topic: Developer and implementation
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 2%

---


# Doelconfiguratie {#target-configuration}

U kunt gerichte inhoud leveren in Android-toepassingen.

## De toepassingscontext instellen {#section_37CAE496FF894FCA821F7760605574CA}

**(Vereist)** De `setContext()` methode moet eenmaal worden aangeroepen in de `onCreate()` methode van uw hoofdactiviteit.

Bijvoorbeeld:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Als u deze methodevraag reeds toevoegde toen u Analytics of het Beheer van de Publiek uitvoerde, te hoeven u niet het opnieuw toe te voegen.
