---
title: Verwenden von Windows-Runtime in JavaScript | Microsoft-Dokumentation
ms.custom: 
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime
ms.assetid: 90658546-f746-4e34-a7d1-71cf9ee322a2
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6fbf89668d47d55d1d77a1d7f11765567fc73405
ms.openlocfilehash: c81f5d83056ceb87987e263f09c0d5e5017dbb6f
ms.contentlocale: de-de
ms.lasthandoff: 08/11/2017

---
# <a name="using-the-windows-runtime-in-javascript"></a>Verwenden von Windows-Runtime in JavaScript
Wenn Sie eine UWP-App (Universelle Windows-Plattform) mithilfe von JavaScript schreiben, können Sie Windows-Runtime-Klassen, -Methoden und -Eigenschaften fast genauso nutzen wie native JavaScript-Objekte, -Methoden und -Eigenschaften. Dieses Thema bietet einführende Informationen und Links zu Themen, die die grundlegenden Konzepte der Verwendung von Windows-Runtime-APIs in JavaScript erklären, darunter eine Erklärung, wie Windows-Runtime-Typen dargestellt werden, wie asynchrone Windows-Runtime-Verfahren verwendet werden und wie Windows-Runtime-Ereignisse wahrgenommen und verarbeitet werden.  
  
 Die JavaScript-Referenzdokumentation finden Sie unter [JavaScript Language Reference (JavaScript-Referenzdokumentation)](../javascript/javascript-language-reference.md).  
  
> [!IMPORTANT]
>  Windows-Runtime-Funktionen sind nicht für Apps verfügbar, die in Internet Explorer ausgeführt werden.  
  
## <a name="windows-runtime-reference-documentation"></a>Windows-Runtime-Referenzdokumentation  
 Die Referenzdokumentation finden Sie unter [Windows-Runtime-Referenzdokumentation](https://msdn.microsoft.com/en-us/library/windows/apps/br211377.aspx). Codebeispiele sind in JavaScript sowie in C++, C# und Visual Basic verfügbar.  
  
## <a name="writing-windows-runtime-components-in-c-c-or-visual-basic"></a>Schreiben von Windows-Runtime-Komponenten in C++, C# oder Visual Basic  
 Anweisungen und Richtlinien zum Erstellen von Windows-Runtime-Komponenten, die in JavaScript genutzt werden können, finden Sie unter [Erstellen von Windows-Runtime-Komponenten in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp) und [Erstellen von Windows-Runtime-Komponenten in C# und Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).  
  
## <a name="casing-conventions-with-windows-runtime-features"></a>Groß-/Kleinschreibungskonventionen in Windows-Runtime-Funktionen  
 Groß-/Kleinschreibungskonventionen für Windows-Runtime-Funktionen in JavaScript unterscheiden sich ein wenig von denen in anderen Sprachen:  
  
-   Namespaces und Klassen stehen in Pascal-Case-Schreibweise (Binnenversalien, erstes Wort großgeschrieben):  
  
    ```JavaScript  
    Windows.Deployment.PackageInfo;  
    ```  
  
-   Member von Klassen, darunter auch Methoden und Eigenschaften, sowie Member von Strukturen und Aufzählungen stehen in Camel-Case-Schreibweise (Binnenversalien, erstes Wort kleingeschrieben):  
  
    ```JavaScript  
    Deployment.PackageInfo.createPackage();  
    ```  
  
-   Ereignisnamen stehen in Kleinbuchstaben:  
  
    ```JavaScript  
    dataTransferManager.ontargetapplicationchosen;  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Überlegungen zur Verwendung der Windows-Runtime-API](../jswinrt/considerations-when-using-the-windows-runtime-api.md)   
 [Verwenden von asynchronen Methoden von Windows-Runtime](../jswinrt/using-windows-runtime-asynchronous-methods.md)   
 [Behandeln von Windows-Runtime-Ereignissen in JavaScript](../jswinrt/handling-windows-runtime-events-in-javascript.md)   
 [JavaScript-Darstellung von Windows-Runtime-Typen](../jswinrt/javascript-representation-of-windows-runtime-types.md)   
 [JavaScript-Projektion von Windows-Runtime-DateTime und -TimeSpan](../jswinrt/windows-runtime-datetime-and-timespan-representations.md)
