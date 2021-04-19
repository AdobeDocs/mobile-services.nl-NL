---
description: U kunt gerichte inhoud leveren in Android-toepassingen.
keywords: android;bibliotheek;mobile;sdk
seo-description: U kunt gerichte inhoud leveren in Android-toepassingen.
seo-title: Doelconfiguratie
solution: Experience Cloud,Analytics
title: Doelconfiguratie
topic-fix: Developer and implementation
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
exl-id: dbcc3114-e76b-4b18-a418-ac46a21a593e
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '76'
ht-degree: 2%

---

# Doelconfiguratie {#target-configuration}

U kunt gerichte inhoud leveren in Android-toepassingen.

## De toepassingscontext instellen {#section_37CAE496FF894FCA821F7760605574CA}

**(Vereist)** De  `setContext()` methode moet eenmaal worden aangeroepen in de  `onCreate()` methode van uw hoofdactiviteit.

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
