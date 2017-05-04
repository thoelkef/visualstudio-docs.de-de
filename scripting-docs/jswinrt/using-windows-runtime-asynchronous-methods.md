---
title: "Verwenden von asynchronen Windows-Runtime-Methoden | Microsoft Docs"
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
  - "JavaScript, asynchrone Windows-Runtime-Methoden"
ms.assetid: 70756833-44f7-4383-827f-2ac781558082
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Verwenden von asynchronen Windows-Runtime-Methoden
Viele Windows\-Runtime\-Methoden, speziell solche, deren Ausführung viel Zeit in Anspruch nimmt, sind asynchron.  Die Methoden geben im Allgemeinen eine asynchrone Aktion oder Operation zurück \(z. B. `Windows.Foundation.IAsyncAction`, `Windows.Foundation.IAsyncOperation`, `Windows.Foundation.IAsyncActionWithProgress` oder `Windows.Foundation.IAsyncOperationWithProgress`\).  Diese Methoden werden in JavaScript mithilfe des Musters [CommonJS\/Promises\/A](http://go.microsoft.com/fwlink/p/?LinkId=244434) dargestellt.  Das heißt, dass sie ein Zusageobjekt mit einer [then](http://msdn.microsoft.com/de-de/c63904fc-465b-4fd5-a1d6-e4fb200248e7)\-Funktion zurückgeben, für das Sie eine `completed`\-Funktion bereitstellen müssen, die das Ergebnis verarbeitet, wenn die Operation erfolgreich verläuft.  Wenn Sie keinen Fehlerhandler bereitstellen möchten, sollten Sie statt der [then](http://msdn.microsoft.com/de-de/c63904fc-465b-4fd5-a1d6-e4fb200248e7)\-Funktion die [done](http://msdn.microsoft.com/de-de/9a5e6877-a2cf-421f-a91e-37d84ccb40da)\-Funktion verwenden.  
  
> [!IMPORTANT]
>  Windows\-Runtime\-Funktionen sind nicht für Apps verfügbar, die in Internet Explorer ausgeführt werden.  
  
## Beispiele für asynchrone Methoden  
 Im folgenden Beispiel verwendet die [then](http://msdn.microsoft.com/de-de/c63904fc-465b-4fd5-a1d6-e4fb200248e7)\-Funktion einen Parameter, der den Abschlusswert der Methode `createResourceAsync` darstellt.  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
        console.log("New item is: " + newItem.id);  
            });  
```  
  
 Wenn in diesem Falle die Methode `createResourceAsync` fehlschlägt, gibt sie eine Zusage im Fehlerstatus zurück, löst jedoch keine Ausnahme aus.  Sie können einen Fehler wie folgt mithilfe der [then](http://msdn.microsoft.com/de-de/c63904fc-465b-4fd5-a1d6-e4fb200248e7)\-Funktion verarbeiten.  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
              console.log("New item is: " + newItem.id);  
          }  
          function(err) {  
              console.log("Got error: " + err.message);  
          });  
```  
  
 Wenn Sie den Fehler nicht explizit verarbeiten möchten, aber dafür sorgen möchten, dass er eine Ausnahme auflöst, können Sie stattdessen die [done](http://msdn.microsoft.com/de-de/9a5e6877-a2cf-421f-a91e-37d84ccb40da)\-Funktion verwenden.  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .done(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            });  
```  
  
 Sie können auch den Fortschritt bis zum Abschluss anzeigen, indem Sie eine dritte Funktion verwenden.  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .then(function(newItem) {   
               console.log("New item is: " + newItem.id);  
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
  
 Weitere Informationen zur asynchronen Programmierung finden Sie unter [Asynchronous programming](http://msdn.microsoft.com/de-de/904ff97c-bb36-4ac5-9eda-a961e3639415).  
  
## Siehe auch  
 [Verwenden von Windows\-Runtime in JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)