---
title: "Verwenden von Windows-Runtime in JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Windows-Runtime"
ms.assetid: 90658546-f746-4e34-a7d1-71cf9ee322a2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Verwenden von Windows-Runtime in JavaScript
Wenn Sie eine [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)]\- oder eine Windows Phone Store\-App mithilfe von JavaScript schreiben, können Sie Windows Runtime\-Klassen, \-Methoden und \-Eigenschaften praktisch in derselben Weise nutzen, als wenn sie native JavaScript\-Objekte, \-Methoden und \-Eigenschaften verwenden würden.  Dieses Thema bietet einführende Informationen und Links zu Themen, die die grundlegenden Konzepte der Verwendung von Windows\-Runtime\-APIs in JavaScript erklären, darunter eine Erklärung, wie Windows\-Runtime\-Typen dargestellt werden, wie asynchrone Windows\-Runtime\-Verfahren verwendet werden und wie Windows\-Runtime\-Ereignisse wahrgenommen und verarbeitet werden.  
  
 Die JavaScript\-Referenzdokumentation finden Sie unter [JavaScript\-Sprachreferenz](../javascript/javascript-language-reference.md).  
  
> [!IMPORTANT]
>  Windows\-Runtime\-Funktionen sind nicht für Apps verfügbar, die in Internet Explorer ausgeführt werden.  
  
## Windows\-Runtime\-Referenzdokumentation  
 Die Referenzdokumentation finden Sie unter [Windows Runtime reference](http://msdn.microsoft.com/de-de/8fe97dbf-8cd4-435f-b481-9e83d0519f9e).  Codebeispiele sind in JavaScript sowie in C\+\+, C\# und Visual Basic verfügbar.  
  
## Schreiben von Windows\-Runtime\-Komponenten in C\+\+, C\# oder Visual Basic  
 Informationen über Anweisungen und Richtlinien zum Schreiben von Windows\-Runtime\-Komponenten, die in JavaScript verwendet werden können, finden Sie unter [Erstellen von Windows\-Runtime\-Komponenten](../Topic/Creating%20Windows%20Runtime%20Components.md).  
  
## Groß\-\/Kleinschreibungskonventionen in Windows\-Runtime\-Funktionen  
 Groß\-\/Kleinschreibungskonventionen für Windows\-Runtime\-Funktionen in JavaScript unterscheiden sich ein wenig von denen in anderen Sprachen:  
  
-   Namespaces und Klassen stehen in Pascal\-Case\-Schreibweise \(Binnenversalien, erstes Wort großgeschrieben\):  
  
    ```javascript  
    Windows.Deployment.PackageInfo;  
    ```  
  
-   Member von Klassen, darunter auch Methoden und Eigenschaften, sowie Member von Strukturen und Aufzählungen stehen in Camel\-Case\-Schreibweise \(Binnenversalien, erstes Wort kleingeschrieben\):  
  
    ```javascript  
    Deployment.PackageInfo.createPackage();  
    ```  
  
-   Ereignisnamen stehen in Kleinbuchstaben:  
  
    ```javascript  
    dataTransferManager.ontargetapplicationchosen;  
    ```  
  
## Siehe auch  
 [Überlegungen zur Verwendung der Windows\-Runtime\-API](../jswinrt/considerations-when-using-the-windows-runtime-api.md)   
 [Verwenden von asynchronen Windows\-Runtime\-Methoden](../jswinrt/using-windows-runtime-asynchronous-methods.md)   
 [Behandeln von Windows\-Runtime\-Ereignissen in JavaScript](../jswinrt/handling-windows-runtime-events-in-javascript.md)   
 [JavaScript\-Darstellung von Windows\-Runtime\-Typen](../jswinrt/javascript-representation-of-windows-runtime-types.md)   
 [JavaScript\-Projektion von Windows\-Runtime\-DateTime und \-TimeSpan](../jswinrt/windows-runtime-datetime-and-timespan-representations.md)