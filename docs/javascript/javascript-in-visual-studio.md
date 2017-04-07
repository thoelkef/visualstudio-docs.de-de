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
ms.sourcegitcommit: 77e7ce26df70e41e2328442454fe78c7a663f1f3
ms.openlocfilehash: de00ef86413571739446b61427c3a8e6c4680c06
ms.lasthandoff: 03/08/2017

---
# <a name="javascript-in-visual-studio"></a>JavaScript in Visual Studio
JavaScript ist eine der Hauptprogrammiersprachen in Visual Studio. Zum Schreiben von JavaScript-Code in der Visual Studio-IDE können Sie die meisten oder alle Standardbearbeitungshilfen (Codeausschnitte, IntelliSense, usw.) verwenden. Sie können JavaScript-Code für viele Arten von Anwendungen und Dienste schreiben.  
  
 Eine Dokumentation zur JavaScript-Sprachreferenz finden Sie unter [JavaScript](https://docs.microsoft.com/scripting/javascript/javascript-language-reference).
  
 Unter Umständen sind bestimmte Versionen von Visual Studio oder bestimmte Visual Studio-Erweiterungen erforderlich, um bestimmte Anwendungstypen und Dienste mit HTML und JavaScript zu entwickeln. Die folgende Liste enthält Links für weitere Informationen.  
  
-   Informationen zum Erstellen von plattformübergreifenden Apps mit Apache Cordova finden Sie unter [Visual Studio-Tools für Apache Cordova](https://docs.microsoft.com/visualstudio/cross-platform/tools-for-cordova/).  
  
-   Links zu JavaScript-Technologien, die Sie in Visual Studio verwenden können, finden Sie auf den Seiten [JavaScript](https://docs.microsoft.com/scripting/javascript/) und [Scripting Technologies](https://docs.microsoft.com/scripting/) (Skripterstellungstechnologien).
  
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
