---
title: Verwenden der bind-Methode (JavaScript) | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bind method [JavaScript]
- this object [JavaScript]
ms.assetid: f608f95b-3b9d-437a-a67a-5a4ef8f6c07f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d185801cc5bba355751147edb79b9c47d21f8eed
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2018
---
# <a name="using-the-bind-method-javascript"></a>Verwenden der bind-Methode (JavaScript)
Die `bind`-JavaScript-Methode kann auf verschiedene Weise genutzt werden. Normalerweise wird sie verwendet, um Ausführungskontext für eine Funktion beizubehalten, die in einem anderen Kontext ausgeführt wird. Mit der `bind`-Methode wird eine neue Funktion erstellt, die den gleichen Text wie die ursprüngliche Funktion hat. Das erste Argument, das an `bind` übergeben wird, gibt den Wert des `this`-Schlüsselworts in der gebundenen Funktion an. Sie können auch die zusätzlichen, optionalen Argumente an die `bind`-Methode übergeben. Beispiele für die zusätzliche Verwendung finden Sie unter [bind-Methode (Funktion)](../../javascript/reference/bind-method-function-javascript.md). Ein Beispiel für die Verwendung der `bind`-Methode zur partiellen Anwendung auf Funktionen finden Sie unter [Muster und Tipps für die asynchrone Programmierung in Hilo (Windows Store-Apps mit JavaScript und HTML)](http://msdn.microsoft.com/library/windows/apps/jj649740.aspx).  
  
## <a name="preserving-the-execution-context-using-bind"></a>Beibehalten des Ausführungskontexts mithilfe der bind-Methode  
 Die `bind`-Funktion wird häufig zum Hinzufügen von Ereignislistenern verwendet. Im folgenden Codebeispiel wird `bind` verwendet, um den Kontext des aktuellen Objekts (`DataObject`) beizubehalten. Das Datenobjekt wird mithilfe des `bind`-Schlüsselworts an `this` übergeben, das Zugriff auf die Datenobjekteigenschaften und Funktionen ermöglicht, wenn der Ereignishandler (`dataReadyHandler`) ausgeführt wird. Um die Funktionsweise der `bind`-Methode zu veranschaulichen, wird mit diesem Code ein benutzerdefiniertes Ereignis erstellt.  
  
```JavaScript  
var data;  
  
var dataReadyEvent = document.createEvent("Event");  
dataReadyEvent.initEvent("dataReady", true, false);  
  
function DataObject() {  
    this.name = "Data Object";  
    this.data = function () {  
        return data;  
    }  
    this.onDataCompleted = dataReadyHandler;  
    document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
    // To see the result of not using bind, comment out the preceding line,   
    // and uncomment the following line of code.  
    // document.addEventListener('dataReady', this.onDataCompleted);  
}  
function dataReadyHandler() {  
    if (console && console.log) {  
        console.log("Data object property value: " + this.name);  
        console.log("Data object property value: " + this.data());  
    }  
}  
  
setTimeout(function () {  
    data = [0, 1, 2, 3];  
    document.dispatchEvent(dataReadyEvent);  
    }, 5000);
  
var dataObj = new DataObject();  
  
// Output:  
// Data Object  
// 0,1,2,3  
  
```  
  
 Wenn Sie die Codezeile auskommentieren, die die `bind`-Methode verwendet, heben Sie die Auskommentierung der Codezeile auf, die `addEventListener` ohne `bind` aufruft. Wenn Sie dann den Code erneut ausführen, schlägt die `dataReadyHandler`-Funktion fehl. Beispielsweise wird `dataReadyHandler` in `this.name` nicht definiert, und `this.data()` führt zu einem Fehler, da das `this`-Objekt nicht mehr auf das Datenobjekt verweist.  
  
## <a name="see-also"></a>Siehe auch  
 [bind-Methode (Funktion)](../../javascript/reference/bind-method-function-javascript.md)
