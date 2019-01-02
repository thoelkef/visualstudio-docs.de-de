---
title: JavaScript
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bcd092ca1631f54f758cef95895d8509d14dec96
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802977"
---
# <a name="javascript-in-visual-studio"></a>JavaScript in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript ist eine der Hauptprogrammiersprachen in Visual Studio. Zum Schreiben von JavaScript-Code in der Visual Studio-IDE können Sie die meisten oder alle Standardbearbeitungshilfen (Codeausschnitte, IntelliSense, usw.) verwenden. Sie können JavaScript-Code für viele Arten von Anwendungen und Dienste schreiben.

 Eine Dokumentation zur JavaScript-Sprachreferenz finden Sie unter [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).

 Unter Umständen sind bestimmte Versionen von Visual Studio oder bestimmte Visual Studio-Erweiterungen erforderlich, um bestimmte Anwendungstypen und Dienste mit HTML und JavaScript zu entwickeln. Die folgende Liste enthält Links für weitere Informationen.

- Für das Erstellen von plattformübergreifenden Apps mit Apache Cordova [laden Sie die Visual Studio-Tools für Apache Cordova herunter](http://go.microsoft.com/fwlink/p/?LinkId=397606).

- Um [Windows Store](http://dev.windows.com/develop)-, [Windows Phone](http://dev.windows.com/develop)- und universelle Apps (die beide Plattformen unterstützen) zu erstellen, [laden Sie die Tools herunter](http://dev.windows.com/en-us/develop/downloads).

- Weitere Informationen zum Erstellen von cloudbasierten Diensten finden Sie auf der [Microsoft Azure-Website](http://azure.microsoft.com/documentation/).

- Weitere Informationen zum Erstellen von Websites und Web-Apps [finden Sie auf der ASP.NET-Website](http://www.asp.net/get-started/websites).

  > [!NOTE]
  >  Sie können eine leere ASP.NET-Website erstellen und für die HTML-, CSS- und JavaScript-Programmierung verwenden. Die von ASP.NET bereitgestellte Datei "Webconfig" ermöglicht das Debuggen in Visual Studio (Sie können auch die F12-Tools beim Ausführen der App verwenden).

  Der JavaScript-Editor in Visual Studio bietet IntelliSense-Unterstützung. Weitere Informationen finden Sie unter [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="whats-new-in-javascript"></a>Neues bei JavaScript
 Die neuen Funktionen für JavaScript werden in der folgenden Tabelle aufgeführt

|Feature|Beschreibung|
|-------------|-----------------|
|Klassen|Neue Syntax unterstützt die Deklaration von [Klassen](/visualstudio/scripting-docs/javascript/reference/class-statement-javascript).|
|Promises|[Promises](/visualstudio/scripting-docs/javascript/reference/promise-object-javascript) ermöglichen eine leichtere und sauberere asynchrone Codierung. Promise-Konstruktoren werden unterstützt, zusammen mit den Hilfsmethoden `all` und `race`.|
|Iterators|Jetzt können Sie iterierbare Objekte (einschließlich Arrays, arrayähnliche Objekte und Iteratoren) wiederholt durchlaufen und dabei einen benutzerdefinierten Iterationshaken mit Anweisungen aufrufen, die für den Wert jeder einzelnen Eigenschaft ausgeführt werden sollen. Weitere Informationen finden Sie unter [Iteratoren und Generatoren](/visualstudio/scripting-docs/javascript/advanced/iterators-and-generators-javascript). **Hinweis**:  Generatoren werden noch nicht unterstützt.|
|Pfeilfunktionen|Die Pfeilfunktion (= >) bietet eine Kurzsyntax für das Schlüsselwort `function`, dass eine lexikalische `this`-Bindung darstellt.|
|Neue Methoden für integrierte Objekte|Die integrierten Objekte [Array-Objekt](/visualstudio/scripting-docs/javascript/reference/array-object-javascript), [Math-Objekt](/visualstudio/scripting-docs/javascript/reference/math-object-javascript), [Number-Objekt](/visualstudio/scripting-docs/javascript/reference/number-object-javascript), [Object-Objekt](/visualstudio/scripting-docs/javascript/reference/object-object-javascript) und [String-Objekt](/visualstudio/scripting-docs/javascript/reference/string-object-javascript) umfassen viele neue Hilfsfunktionen und Eigenschaften zum Bearbeiten und Überprüfen von Daten.|
|Verbesserungen des Objektliterals|Objekte unterstützen nun berechnete Eigenschaften, präzise Methodendefinitionen und eine Kurzsyntax für Eigenschaften, deren Wert für eine gleichnamige Variable initialisiert wird. Weitere Informationen finden Sie unter [Erstellen von Objekten](/visualstudio/scripting-docs/javascript/creating-objects-javascript).|
|Proxys|[Proxys](/visualstudio/scripting-docs/javascript/reference/proxy-object-javascript) ermöglichen ein benutzerdefiniertes Verhalten für Objekte.|
|Rest-Parameter|Mit Rest-Parametern können Sie aufeinanderfolgende Argumente in einem Funktionsaufruf in einen Array umwandeln. Weitere Informationen finden Sie unter [Funktionen](/visualstudio/scripting-docs/javascript/functions-javascript).|
|Spread-Operator|Der [Spread-Operator](/visualstudio/scripting-docs/javascript/reference/spread-operator-decrement-dot-dot-dot-javascript) (`…`) erweitert iterierbare Ausdrücke in einzelne Argumente. Beispielsweise entspricht `a.b(…array)` ungefähr `a.b.apply(a, array)`.|
|Symbole|Mit [Symbol](/visualstudio/scripting-docs/javascript/reference/symbol-object-javascript)-Objekten können Eigenschaften vorhandenen Objekten hinzugefügt werden, ohne dass mögliche Probleme mit den vorhandenen Objekteigenschaften, unerwünschte Sichtbarkeit oder weitere unkoordinierte Hinzufügungen durch anderen Code bestehen.|
|Vorlagenzeichenfolgen|[Vorlagenzeichenfolgen](/visualstudio/scripting-docs/javascript/advanced/template-strings-javascript) sind Zeichenfolgenliterale, mit denen Ausdrücke ausgewertet und mit dem Zeichenfolgenliteral verkettet werden können.|
|Unicode-Verbesserungen|Es wurden Verbesserungen der Unicode-Unterstützung vorgenommen. Beispielsweise unterstützt ein neues Escapesequenzformat astrale Codepunkte (Codepunkte mit mehr als vier Hexadezimalziffern). Weitere Informationen finden Sie unter [Sonderzeichen](/visualstudio/scripting-docs/javascript/advanced/special-characters-javascript).|
|WeakSet|Ein [WeakSet](/visualstudio/scripting-docs/javascript/reference/weakset-object-javascript) ist eine Auflistung von Objekten, für die eine Garbage Collection durchgeführt wird, wenn nicht an anderer Stelle auf sie verwiesen wird.|
