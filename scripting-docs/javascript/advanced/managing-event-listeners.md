---
title: Verwalten von Ereignislistenern | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 87717f5d-b0c6-4c8d-a293-476002b7bfcf
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a97c579716b9964b8dfb93db419e9a70160d33a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="managing-event-listeners"></a>Verwalten von Ereignislistenern
Wenn das DOM-Element oder -Objekt eine andere Lebensdauer hat als der zugehörige Ereignislistener, müssen Sie möglicherweise die [removeEventListener](http://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx)-Methode verwenden, um Arbeitsspeicherverluste zu vermeiden.  
  
## <a name="event-listeners-and-object-scope"></a>Ereignislistener und Objektgültigkeitsbereich  
 Der Code im folgenden Codebeispiel kann zu einem Arbeitsspeicherverlust führen, wenn die `dataObjFactory()`-Funktion aufgerufen wird. In diesem Code wird bei jeder Erstellung eines neuen Datenobjekts ein Ereignislistener für das jeweilige Datenobjekt erstellt. Um das aktuelle Datenobjekt im `dataReady()`-Ereignishandler verfügbar zu machen, wird [bind-Methode (Funktion)](../../javascript/reference/bind-method-function-javascript.md) in `addEventListener` verwendet.  
  
```JavaScript  
 var data;  
 var dataObj;  
  
 var dataReadyEvent = document.createEvent("Event");  
 dataReadyEvent.initEvent("dataReady", true, false);  
  
 function DataObject() {  
  
     this.name = "Data Object";  
     this.data = function () {  
         return data;  
     }  
     this.onDataCompleted = dataReady;  
     // this.handlerRef = this.onDataCompleted.bind(this);  
  
     // document.addEventListener('dataReady', this.handlerRef);  
     document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
 }  
  
 // Runs when the data is available.  
 function dataReady() {  
     if (console && console.log) {  
         console.log("object value: " + this.name);  
         console.log("object value: " + this.data());  
     }  
 }  
  
setTimeout(function () {  
    // Generate data after a timeout period.  
    data = [0, 1, 2, 3];  
    document.dispatchEvent(dataReadyEvent);  
}, 10000);  
  
function dataObjFactory() {  
     for (var x = 0; x < 100; x++) {  
         if (dataObj) {  
             // The following line of code has no effect.  
             document.removeEventListener('dataReady', dataObj.onDataCompleted);  
             dataObj = null;  
         }  
         dataObj = new DataObject();  
     }  
 }  
  
 dataObjFactory();  
```  
  
 Der Listener für jedes Datenobjekt wird beim `document`-Objekt registriert, das eine andere Lebensdauer hat als die Datenobjekte. Der registrierte Ereignislistener der einzelnen Datenobjekte verhindert, dass eine Garbage Collection für sie durchgeführt wird, solange sich das `document`-Objekt innerhalb des Gültigkeitsbereichs befindet. (In einigen aktuellen JavaScript-Entwurfsmustern bleibt das document-Objekt für die gesamte Lebensdauer der Web-App im Gültigkeitsbereich.) Um einen Arbeitsspeicherverlust zu verhindern, wird `removeEventListener` in der `dataObjFactory`-Funktion aufgerufen. Dieser Code verursacht jedoch einen Fehler, da `removeEventListener` nicht für die gebundene Version des Ereignishandlers aufgerufen wurde, die von der `bind`-Funktion zurückgegeben wird.  
  
 Um den Code zu korrigieren und die Datenobjekte für die Garbage Collection verfügbar zu machen, müssen Sie zunächst einen Verweis auf die gebundene Version des Ereignishandlers speichern, wie in diesem Code gezeigt, und dann den gespeicherten Verweis an `addEventListener` übergeben. Hier sehen Sie den korrigierten Code für `DataObject`:  
  
```JavaScript  
function DataObject() {  
  
    this.name = "Data Object";  
    this.data = function () {  
        return data;  
    }  
    this.onDataCompleted = dataReady;  
    this.handlerRef = this.onDataCompleted.bind(this);  
  
    document.addEventListener('dataReady', this.handlerRef);  
    // document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
}  
  
```  
  
 Schließlich müssen Sie `removeEventListener` für den gespeicherten Verweis (`handlerRef`) der gebundenen Funktion aufrufen. Hier sehen Sie den korrigierten Code für `dataObjFactory`:  
  
```JavaScript  
function dataObjFactory() {  
     for (var x = 0; x < 100; x++) {  
         if (dataObj) {  
             document.removeEventListener('dataReady', dataObj.handlerRef);  
         }  
         dataObj = new DataObject();  
     }  
 }  
  
```  
  
 Jetzt funktioniert der Aufruf von `removeEventListener`, und für die nicht benötigen Datenobjekte kann eine Garbage Collection durchgeführt werden, während das `document`-Objekt im Gültigkeitsbereich bleibt.