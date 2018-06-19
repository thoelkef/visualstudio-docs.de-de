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
ms.openlocfilehash: e963472ee51f2439b50807a49425dcd7f6d8443a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24571430"
---
# <a name="handling-windows-runtime-events-in-javascript"></a>Behandeln von Windows-Runtime-Ereignissen in JavaScript
Windows-Runtime-Ereignisse werden in JavaScript nicht auf dieselbe Weise dargestellt wie in C++ oder im .NET Framework. Sie sind keine Klasseneigenschaften, sondern werden als Zeichenfolgenbezeichner dargestellt, die an die Methoden `addEventListener` und `removeEventListener` der Klasse übergeben werden. Sie können z.B. dem Ereignis [Geolocator.PositionChanged](http://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) einen Ereignishandler hinzufügen, indem Sie der `Geolocator.addEventListener`-Methode die Zeichenfolge „positionchanged“ übergeben:  
  
```JavaScript  
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
  
 In JavaScript werden Windows-Runtime-Ereignisargumente als einzelnes Ereignisobjekt dargestellt. Im folgenden Beispiel für eine Ereignishandlermethode ist der Parameter `ev` ein Objekt, das sowohl den Sender (die Zieleigenschaft) als auch die anderen Ereignisargumente enthält. Die Ereignisargumente sind diejenigen Argumente, die für jedes Ereignis dokumentiert werden.  
  
```JavaScript  
function (ev) {  
    console.log("Target: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
  
```  
  
> [!IMPORTANT]
>  Windows-Runtime-Funktionen sind nicht für Apps verfügbar, die in Internet Explorer ausgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Windows-Runtime in JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)