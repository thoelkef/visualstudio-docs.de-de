---
title: JavaScript in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: d4741ff741b89997bbfe4fea9b0f60bba84e63db
ms.lasthandoff: 02/22/2017

---
# <a name="javascript-in-visual-studio"></a>JavaScript in Visual Studio
JavaScript ist eine der Hauptprogrammiersprachen in Visual Studio. Zum Schreiben von JavaScript-Code in der Visual Studio-IDE können Sie die meisten oder alle Standardbearbeitungshilfen (Codeausschnitte, IntelliSense, usw.) verwenden. Sie können JavaScript-Code für viele Arten von Anwendungen und Dienste schreiben.  
  
 Eine Dokumentation zur JavaScript-Sprachreferenz finden Sie unter [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).  
  
 Unter Umständen sind bestimmte Versionen von Visual Studio oder bestimmte Visual Studio-Erweiterungen erforderlich, um bestimmte Anwendungstypen und Dienste mit HTML und JavaScript zu entwickeln. Die folgende Liste enthält Links für weitere Informationen.  
  
-   Für das Erstellen von plattformübergreifenden Apps mit Apache Cordova [laden Sie die Visual Studio-Tools für Apache Cordova herunter](http://go.microsoft.com/fwlink/p/?LinkId=397606).  
  
-   Um [Windows Store](http://dev.windows.com/develop)-, [Windows Phone](http://dev.windows.com/develop)- und universelle Apps (die beide Plattformen unterstützen) zu erstellen, [laden Sie die Tools herunter](http://dev.windows.com/en-us/develop/downloads).  
  
-   Weitere Informationen zum Erstellen von cloudbasierten Diensten finden Sie auf der [Microsoft Azure-Website](http://azure.microsoft.com/documentation/).  
  
-   Weitere Informationen zum Erstellen von Websites und Web-Apps [finden Sie auf der ASP.NET-Website](http://www.asp.net/get-started/websites).  
  
    > [!NOTE]
    >  Sie können eine leere ASP.NET-Website erstellen und für die HTML-, CSS- und JavaScript-Programmierung verwenden. Die von ASP.NET bereitgestellte Datei "Webconfig" ermöglicht das Debuggen in Visual Studio (Sie können auch die F12-Tools beim Ausführen der App verwenden).  
  
 Der JavaScript-Editor in Visual Studio bietet IntelliSense-Unterstützung. Weitere Informationen finden Sie unter [JavaScript IntelliSense](../ide/javascript-intellisense.md).  
  
## <a name="whats-new-in-javascript"></a>Neues bei JavaScript  
 Die neuen Funktionen für JavaScript werden in der folgenden Tabelle aufgeführt  
  
|Funktion|Beschreibung|  
|-------------|-----------------|  
|Klassen|Neue Syntax unterstützt die Deklaration von [Klassen](http://msdn.microsoft.com/Library/bf45ebad-4678-4062-88df-55d32b603c69).|  
|Promises|[Promises](http://msdn.microsoft.com/Library/358ad98b-f7fa-448c-9ee0-ef1e2a45e9c6) ermöglichen eine leichtere und sauberere asynchrone Codierung. Promise-Konstruktoren werden unterstützt, zusammen mit den Hilfsmethoden `all` und `race`.|  
|Iteratoren|Jetzt können Sie iterierbare Objekte (einschließlich Arrays, arrayähnliche Objekte und Iteratoren) wiederholt durchlaufen und dabei einen benutzerdefinierten Iterationshaken mit Anweisungen aufrufen, die für den Wert jeder einzelnen Eigenschaft ausgeführt werden sollen. Weitere Informationen finden Sie unter [Iteratoren und Generatoren](http://msdn.microsoft.com/Library/68ef5b2f-0349-492b-b557-73ff2a2f90cf). **Hinweis:** Generatoren werden noch nicht unterstützt.|  
|Pfeilfunktionen|Die Pfeilfunktion (= >) bietet eine Kurzsyntax für das Schlüsselwort `function`, dass eine lexikalische `this`-Bindung darstellt.|  
|Neue Methoden für integrierte Objekte|Die integrierten Objekte [Array-Objekt](http://msdn.microsoft.com/Library/08e5f552-0797-4b48-8164-609582fc18c9), [Math-Objekt](http://msdn.microsoft.com/Library/607b94cb-921c-43cd-b514-fdbc13aeced6), [Number-Objekt](http://msdn.microsoft.com/Library/76e87c37-cf6c-46cc-bafa-04be1fe3d78d), [Object-Objekt](http://msdn.microsoft.com/Library/d24ef8fc-217b-4828-94e1-19f72780bae0) und [String-Objekt](http://msdn.microsoft.com/Library/8063ecd5-5778-4e87-b985-b21420171914) umfassen viele neue Hilfsfunktionen und Eigenschaften zum Bearbeiten und Überprüfen von Daten.|  
|Verbesserungen des Objektliterals|Objekte unterstützen nun berechnete Eigenschaften, präzise Methodendefinitionen und eine Kurzsyntax für Eigenschaften, deren Wert für eine gleichnamige Variable initialisiert wird. Weitere Informationen finden Sie unter [Erstellen von Objekten](http://msdn.microsoft.com/Library/58d1baa5-4fe8-4a56-a926-5b11765df704).|  
|Proxys|[Proxys](http://msdn.microsoft.com/Library/2b89abee-04fa-47e6-9676-980016cff5f8) ermöglichen ein benutzerdefiniertes Verhalten für Objekte.|  
|Rest-Parameter|Mit Rest-Parametern können Sie aufeinanderfolgende Argumente in einem Funktionsaufruf in einen Array umwandeln. Weitere Informationen finden Sie unter [Funktionen](http://msdn.microsoft.com/Library/e2a72b5a-3edd-43d8-95e8-91721b38c1c1).|  
|Spread-Operator|Der [Spread-Operator](http://msdn.microsoft.com/Library/10263a4c-bd27-4d87-9917-fb4b6bf373db) (`…`) erweitert iterierbare Ausdrücke in einzelne Argumente. Beispielsweise entspricht `a.b(…array)` ungefähr `a.b.apply(a, array)`.|  
|Symbole|Mit [Symbol](http://msdn.microsoft.com/Library/2ad059f1-4b7f-4758-882a-c74ce1283ab0)-Objekten können Eigenschaften vorhandenen Objekten hinzugefügt werden, ohne dass mögliche Probleme mit den vorhandenen Objekteigenschaften, unerwünschte Sichtbarkeit oder weitere unkoordinierte Hinzufügungen durch anderen Code bestehen.|  
|Vorlagenzeichenfolgen|[Vorlagenzeichenfolgen](http://msdn.microsoft.com/Library/f2e525a5-b0fc-49c3-95a0-641788e5c12a) sind Zeichenfolgenliterale, mit denen Ausdrücke ausgewertet und mit dem Zeichenfolgenliteral verkettet werden können.|  
|Unicode-Verbesserungen|Es wurden Verbesserungen der Unicode-Unterstützung vorgenommen. Beispielsweise unterstützt ein neues Escapesequenzformat astrale Codepunkte (Codepunkte mit mehr als vier Hexadezimalziffern). Weitere Informationen finden Sie unter [Sonderzeichen](http://msdn.microsoft.com/Library/3b38b1bd-1f0f-4748-b13e-55cab36fd126).|  
|WeakSet|Ein [WeakSet](http://msdn.microsoft.com/Library/f97e6e7c-d678-4e32-978e-d949a7cafa3a) ist eine Auflistung von Objekten, für die eine Garbage Collection durchgeführt wird, wenn nicht an anderer Stelle auf sie verwiesen wird.|
