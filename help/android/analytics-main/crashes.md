---
description: Deze informatie helpt u begrijpen hoe de neerstortingen worden gevolgd en de beste praktijken om valse neerstortingen te behandelen.
solution: Experience Cloud Services,Analytics
title: App vastlopen bijhouden
topic-fix: Developer and implementation
uuid: 3ab98c14-ccdf-4060-ad88-ec07c1c6bf07
exl-id: d8d59b4e-0231-446d-9ba1-8a9809be9c61
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Toepassingscrashes bijhouden {#track-app-crashes}

Deze informatie helpt u begrijpen hoe de neerstortingen worden gevolgd en de beste praktijken om valse neerstortingen te behandelen.

>[!TIP]
>
>App-crashes worden bijgehouden als onderdeel van levenscyclusmetriek. Voordat u vastloopt, voegt u de bibliotheek toe aan uw project en implementeert u de levenscyclus. Zie voor meer informatie *Voeg de SDK en het Dossier Config aan uw IDEA van IntelliJ of Project toe Eclipse* in [Kernimplementatie en levenscyclus](/help/android/getting-started/dev-qs.md).

Wanneer de metriek van de levenscyclus wordt uitgevoerd, wordt een vraag gemaakt aan `Config.collectLifecycleData` in de `OnResume` methode van elke activiteit. In de `onPause` methode, wordt een vraag gemaakt aan `Config.pauseCollectingLifeCycleData`.

In de `pauseCollectingLifeCycleData`, wordt een vlag geplaatst om op een graceful uitgang te wijzen. Wanneer de app opnieuw wordt gestart of hervat, `collectLifecycleData` controleert deze vlag. Als de app niet is afgesloten, zoals bepaald door de vlagstatus, kunt u `a.CrashEvent` contextgegevens worden verzonden met de volgende vraag en een botsingsgebeurtenis wordt gemeld.

Om nauwkeurige neerstortingsrapportering te verzekeren, moet u roepen `pauseCollectingLifeCycleData` in de `onPause` methode van elke activiteit. Om te begrijpen waarom dit van essentieel belang is, is hier een voorbeeld van de levenscyclus van de Android-activiteit:

![](assets/android-lifecycle.png)

Voor meer informatie over de levenscyclus van de Android-activiteit raadpleegt u [Activiteiten](https://developer.android.com/guide/components/activities.html).

*Deze Android-levenscyclusillustratie is gemaakt en [gedeeld door het Android Open Source Project](https://source.android.com/) en worden gebruikt overeenkomstig de termen in de [Kenmerklicentie voor Creative Commons 2.5](https://creativecommons.org/licenses/by/2.5/).*

## Wat kan ertoe leiden dat een fout wordt gemeld?

1. Als u foutopsporing uitvoert met behulp van een IDE, zoals Android Studio, en de app opnieuw start vanuit de IDE terwijl de toepassing zich op de voorgrond bevindt, loopt de toepassing vast.

   >[!TIP]
   >
   >U kunt voorkomen dat de toepassing vastloopt door de toepassing te onderbreken voordat u de toepassing opnieuw start vanaf de IDE.

1. Als de laatste voorgrondactiviteit van uw app achtergronden heeft en niet roept `Config.pauseCollectingLifecycleData();` in `onPause`En uw app wordt handmatig gesloten of gedood door het besturingssysteem, de volgende keer dat de toepassing wordt gestart, loopt vast.

## Hoe moeten Fragments worden behandeld?

Fragmenten hebben toepassingslevenscyclusgebeurtenissen die vergelijkbaar zijn met Activiteiten. Een fragment kan echter niet actief zijn zonder te zijn gekoppeld aan een activiteit.

>[!IMPORTANT]
>
>U moet vertrouwen op de levenscyclusgebeurtenissen waartegen de bevattende activiteiten uw code kunnen in werking stellen. Dit wordt verwerkt door de bovenliggende weergave van het fragment.

## (Optioneel) Activiteitenlevenscycluscallbacks implementeren

Vanaf API Level 14 staat Android wereldwijde callbacks voor activiteiten toe. Zie voor meer informatie [Toepassing](https://developer.android.com/reference/android/app/Application).

U kunt deze callbacks gebruiken om ervoor te zorgen dat al uw Activiteiten correct roepen `collectLifecycleData()` en `pauseCollectingLifecycleData()`. U hoeft deze code alleen toe te voegen aan uw hoofdactiviteit en aan elke andere activiteit waarin uw app kan worden gestart:

```js
import com.adobe.mobile.Config; 
  
public class MainActivity extends Activity { 
... 
    @Override 
    protected void onCreate(Bundle savedInstanceState) { 
        super.onCreate(savedInstanceState); 
        setContentView(R.layout.activity_main); 
  
        getApplication().registerActivityLifecycleCallbacks(new Application.ActivityLifecycleCallbacks() { 
            @Override 
            public void onActivityResumed(Activity activity) { 
                Config.setContext(activity.getApplicationContext()); 
                Config.collectLifecycleData(activity); 
            } 
  
            @Override 
            public void onActivityPaused(Activity activity) {     
                Config.pauseCollectingLifecycleData(); 
            } 
    
            // the following methods aren't needed for our lifecycle purposes, but are required to be implemented 
            // by the ActivityLifecycleCallbacks object 
            @Override 
            public void onActivityCreated(Activity activity, Bundle savedInstanceState) {} 
            @Override 
            public void onActivityStarted(Activity activity) {} 
            @Override 
            public void onActivityStopped(Activity activity) {} 
            @Override 
            public void onActivitySaveInstanceState(Activity activity, Bundle outState) {} 
            @Override 
            public void onActivityDestroyed(Activity activity) {} 
        }); 
    } 
... 
}
```

Om extra contextgegevens met uw levenscyclusvraag te verzenden door te gebruiken `Config.collectLifecycleData(Activity activity`, `Map<String`, `Object> contextData)`, moet u de `onResume` methode voor die Activiteit en zorg ervoor dat u roept `super.onResume()` na het handmatig aanroepen `collectLifecycleData`.

```js
@Override 
protected void onResume() { 
    HashMap<String, Object> cdata = new HashMap<>(); 
    cdata.put("someKey", "someValue"); 
    Config.collectLifecycleData(this, cdata); 
  
    super.onResume(); 
}
```
