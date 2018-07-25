---
title: Behandeln von Windows-Runtime-Ereignissen in JavaScript | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime events
- Windows Runtime events [JavaScript]
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7e5780a2462e8980c22c474ae6236c87aee599b
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2018
ms.locfileid: "36302809"
---
# <a name="handling-windows-runtime-events-in-javascript"></a>Behandeln von Windows-Runtime-Ereignissen in JavaScript
Windows-Runtime-Ereignisse werden in JavaScript nicht auf dieselbe Weise dargestellt wie in C++ oder im .NET Framework. Sie sind keine Klasseneigenschaften, sondern werden als Zeichenfolgenbezeichner (in Kleinbuchstaben) dargestellt, die an die Methoden `addEventListener` und `removeEventListener` der Klasse übergeben werden. Sie können z.B. dem Ereignis [Geolocator.PositionChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) einen Ereignishandler hinzufügen, indem Sie der `Geolocator.addEventListener`-Methode die Zeichenfolge „positionchanged“ übergeben:  
  
```JavaScript  
var locator = new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 Außerdem können Sie die Eigenschaft `locator.onpositionchanged` festlegen:  
  
```JavaScript  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
Ein weiterer Unterschied zwischen .NET/C++ und JavaScript ist die Anzahl der Parameter, die von einem Ereignishandler verwendet werden. In .NET/C++ verwendet ein Handler zwei Parameter: den Ereignissender und die Ereignisdaten. In JavaScript sind diese als einzelnes `Event`-Objekt gebündelt. Im folgenden Beispiel enthält der `ev`-Parameter sowohl den Ereignissender (die `target`-Eigenschaft) und die Eigenschaften der Ereignisdaten (in diesem Fall nur `position`). Die Eigenschaften der Ereignisdaten entsprechen den Eigenschaften, die für jedes Ereignis dokumentiert werden.
  
```JavaScript  
function (ev) {  
    console.log("Sender: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
```  
  
> [!IMPORTANT]
>  Windows-Runtime-Funktionen sind nicht für Apps verfügbar, die in Internet Explorer ausgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Windows-Runtime in JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)
