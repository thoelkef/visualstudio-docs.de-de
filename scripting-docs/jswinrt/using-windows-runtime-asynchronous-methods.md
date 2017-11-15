---
title: Verwenden von asynchronen Methoden von Windows-Runtime | Microsoft-Dokumentationen
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: JavaScript, Windows Runtime asynchronous methods
ms.assetid: 70756833-44f7-4383-827f-2ac781558082
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 215a04a2f3f875743a7fbf910a3a565cf34fb558
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="using-windows-runtime-asynchronous-methods"></a>Verwenden von asynchronen Methoden von Windows-Runtime
Viele Windows-Runtime-Methoden, speziell solche, deren Ausführung viel Zeit in Anspruch nimmt, sind asynchron. Die Methoden geben im Allgemeinen eine asynchrone Aktion oder Operation zurück (z. B. `Windows.Foundation.IAsyncAction`, `Windows.Foundation.IAsyncOperation`, `Windows.Foundation.IAsyncActionWithProgress` oder `Windows.Foundation.IAsyncOperationWithProgress`). Diese Methoden werden in JavaScript mithilfe des Musters [CommonJS/Promises/A](http://go.microsoft.com/fwlink/p/?LinkId=244434) dargestellt. Das heißt, dass sie ein Promise-Objekt mit einer [then](https://msdn.microsoft.com/en-us/library/windows/apps/br229728.aspx)-Funktion zurückgeben, für das Sie eine `completed`-Funktion bereitstellen müssen, die das Ergebnis verarbeitet, wenn der Vorgang erfolgreich ist. Wenn Sie keinen Fehlerhandler bereitstellen möchten, sollten Sie statt der `then`-Funktion die [done](https://msdn.microsoft.com/en-us/library/windows/apps/hh701079.aspx)-Funktion verwenden.  
  
> [!IMPORTANT]
>  Windows-Runtime-Funktionen sind nicht für Apps verfügbar, die in Internet Explorer ausgeführt werden.  
  
## <a name="examples-of-asynchronous-methods"></a>Beispiele für asynchrone Methoden  
 Im folgenden Beispiel verwendet die `then`-Funktion einen Parameter, der den Abschlusswert der Methode `createResourceAsync` darstellt.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
        console.log("New item is: " + newItem.id);  
            });  
```  
  
 Wenn in diesem Falle die Methode `createResourceAsync` fehlschlägt, gibt sie eine Zusage im Fehlerstatus zurück, löst jedoch keine Ausnahme aus. Sie können einen Fehler wie folgt mithilfe der `then`-Funktion verarbeiten.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
              console.log("New item is: " + newItem.id);  
          }  
          function(err) {  
              console.log("Got error: " + err.message);  
          });  
```  
  
 Wenn Sie den Fehler nicht explizit verarbeiten möchten, aber dafür sorgen möchten, dass er eine Ausnahme auflöst, können Sie stattdessen die `done`-Funktion verwenden.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .done(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            });  
```  
  
 Sie können auch den Fortschritt bis zum Abschluss anzeigen, indem Sie eine dritte Funktion verwenden.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .then(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            },  
    // Error.  
            function(error) {   
               alert("Failed to create a resource.");  
            },  
    // Progress.  
            function(progress, resultSoFar) {   
               setProgressBar(progress);  
            });  
```  
  
 Weitere Informationen zum asynchronen Programmieren in JavaScript finden Sie unter [Asynchrones Programmieren in JavaScript](https://msdn.microsoft.com/en-us/library/windows/apps/hh700330.aspx).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Windows-Runtime in JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)