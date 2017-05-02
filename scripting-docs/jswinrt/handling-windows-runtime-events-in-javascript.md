---
title: "Behandeln von Windows-Runtime-Ereignissen in JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Windows-Runtime-Ereignisse"
  - "Windows-Runtime-Ereignisse [JavaScript]"
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Behandeln von Windows-Runtime-Ereignissen in JavaScript
Windows\-Runtime\-Ereignisse werden in JavaScript nicht auf dieselbe Weise dargestellt wie in C\+\+ oder im .NET Framework.  Sie sind keine Klasseneigenschaften, sondern werden als Zeichenfolgenbezeichner dargestellt, die an die Methoden `addEventListener` und `removeEventListener` der Klasse übergeben werden.  Sie können z. B. einen Ereignishandler für das Ereignis [Geolocator.PositionChanged](http://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) hinzufügen, indem Sie die Zeichenfolge "positionchanged" an die Methode `Geolocator.addEventListener` übergeben:  
  
```javascript  
var locator =  new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 Außerdem können Sie die Eigenschaft `locator.onpositionchanged` verwenden.  
  
```  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
 In JavaScript werden Windows\-Runtime\-Ereignisargumente als einzelnes Ereignisobjekt dargestellt.  Im folgenden Beispiel für eine Ereignishandlermethode ist der Parameter `ev` ein Objekt, das sowohl den Sender \(die Zieleigenschaft\) als auch die anderen Ereignisargumente enthält.  Die Ereignisargumente sind diejenigen Argumente, die für jedes Ereignis dokumentiert werden.  
  
```javascript  
function (ev) {  
    console.log("Target: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
  
```  
  
> [!IMPORTANT]
>  Windows\-Runtime\-Funktionen sind nicht für Apps verfügbar, die in Internet Explorer ausgeführt werden.  
  
## Siehe auch  
 [Verwenden von Windows\-Runtime in JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)