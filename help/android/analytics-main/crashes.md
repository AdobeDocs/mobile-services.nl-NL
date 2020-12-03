---
description: Deze informatie helpt u begrijpen hoe de neerstortingen worden gevolgd en de beste praktijken om valse neerstortingen te behandelen.
seo-description: Deze informatie helpt u begrijpen hoe de neerstortingen worden gevolgd en de beste praktijken om valse neerstortingen te behandelen.
seo-title: App vastlopen bijhouden
solution: Experience Cloud,Analytics
title: App vastlopen bijhouden
topic: Developer and implementation
uuid: 3ab98c14-ccdf-4060-ad88-ec07c1c6bf07
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---


# Toepassingscrashes bijhouden {#track-app-crashes}

Deze informatie helpt u begrijpen hoe de neerstortingen worden gevolgd en de beste praktijken om valse neerstortingen te behandelen.

>[!TIP]
>
>App-crashes worden bijgehouden als onderdeel van levenscyclusmetriek. Voordat u vastloopt, voegt u de bibliotheek toe aan uw project en implementeert u de levenscyclus. Voor meer informatie, zie *Voeg het Dossier SDK en Config aan uw IDEA IntelliJ of Project* Eclipse in de implementatie en de levenscyclus [van de](/help/android/getting-started/dev-qs.md)Kern toe.

Wanneer de metriek van de levenscyclus wordt uitgevoerd, wordt een vraag gemaakt aan `Config.collectLifecycleData` in de `OnResume` methode van elke activiteit. In de `onPause` methode, wordt een vraag gemaakt aan `Config.pauseCollectingLifeCycleData`.

In de `pauseCollectingLifeCycleData`sectie wordt een markering ingesteld om een vreedzame uitgang aan te geven. Wanneer de app opnieuw wordt gestart of hervat, `collectLifecycleData` wordt deze markering gecontroleerd. Als de app niet correct is afgesloten, zoals bepaald door de vlagstatus, worden `a.CrashEvent` contextgegevens verzonden bij de volgende oproep en wordt een crash-gebeurtenis gerapporteerd.

Om nauwkeurige neerstorting rapportering te verzekeren, moet u `pauseCollectingLifeCycleData` `onPause` de methode van elke activiteit roepen. Om te begrijpen waarom dit van essentieel belang is, is hier een voorbeeld van de levenscyclus van de Android-activiteit:

![](assets/android-lifecycle.png)

Zie [Activiteiten](https://developer.android.com/guide/components/activities.html)voor meer informatie over de levenscyclus van de Android-activiteit.

*Deze Android-levenscyclusillustratie is gemaakt en [gedeeld door het Android Open Source Project](https://source.android.com/) en wordt gebruikt volgens de voorwaarden in de [Creative Commons 2.5-kenmerklicentie](https://creativecommons.org/licenses/by/2.5/).*

## Wat kan ertoe leiden dat een fout wordt gemeld?

1. Als u foutopsporing uitvoert met behulp van een IDE, zoals Android Studio, en de app opnieuw start vanuit de IDE terwijl de toepassing zich op de voorgrond bevindt, loopt de toepassing vast.

   >[!TIP]
   >
   >U kunt voorkomen dat de toepassing vastloopt door de toepassing te onderbreken voordat u de toepassing opnieuw start vanaf de IDE.

1. Als de laatste voorgrondactiviteit van uw app achtergronds is en niet `Config.pauseCollectingLifecycleData();` binnen roept `onPause`, en uw app manueel gesloten of gedood door OS is, resulteert de volgende lancering in een botsing.

## Hoe moeten Fragments worden behandeld?

Fragmenten hebben toepassingslevenscyclusgebeurtenissen die vergelijkbaar zijn met Activiteiten. Een fragment kan echter niet actief zijn zonder te zijn gekoppeld aan een activiteit.

>[!IMPORTANT]
>
>U moet vertrouwen op de levenscyclusgebeurtenissen waartegen de bevattende activiteiten uw code kunnen in werking stellen. Dit wordt verwerkt door de bovenliggende weergave van het fragment.

## (Optioneel) Activiteitenlevenscycluscallbacks implementeren

Vanaf API Level 14 staat Android wereldwijde callbacks voor activiteiten toe. Zie [Toepassing](https://developer.android.com/reference/android/app/Application)voor meer informatie.

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

Om extra contextgegevens met uw levenscyclusvraag te verzenden door te gebruiken `Config.collectLifecycleData(Activity activity`, `Map<String`, `Object> contextData)`, moet u de `onResume` methode voor die Activiteit met voeten treden en ervoor zorgen dat u `super.onResume()` na manueel het roepen `collectLifecycleData`roept.

```js
@Override 
protected void onResume() { 
    HashMap<String, Object> cdata = new HashMap<>(); 
    cdata.put("someKey", "someValue"); 
    Config.collectLifecycleData(this, cdata); 
  
    super.onResume(); 
}
```

