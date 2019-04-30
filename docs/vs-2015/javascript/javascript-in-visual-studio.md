---
title: JavaScript
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-javascript
ms.topic: conceptual
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b9005b6cf7f23639481505a4727f8faa08241684
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433484"
---
# <a name="javascript-in-visual-studio"></a>JavaScript in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript ist eine der Hauptprogrammiersprachen in Visual Studio. Zum Schreiben von JavaScript-Code in der Visual Studio-IDE können Sie die meisten oder alle Standardbearbeitungshilfen (Codeausschnitte, IntelliSense, usw.) verwenden. Sie können JavaScript-Code für viele Arten von Anwendungen und Dienste schreiben.

 Eine Dokumentation zur JavaScript-Sprachreferenz finden Sie unter [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).

 Unter Umständen sind bestimmte Versionen von Visual Studio oder bestimmte Visual Studio-Erweiterungen erforderlich, um bestimmte Anwendungstypen und Dienste mit HTML und JavaScript zu entwickeln. Die folgende Liste enthält Links für weitere Informationen.

- Für das Erstellen von plattformübergreifenden Apps mit Apache Cordova [laden Sie die Visual Studio-Tools für Apache Cordova herunter](http://go.microsoft.com/fwlink/p/?LinkId=397606).

- Um [Windows Store](http://dev.windows.com/develop)-, [Windows Phone](http://dev.windows.com/develop)- und universelle Apps (die beide Plattformen unterstützen) zu erstellen, [laden Sie die Tools herunter](https://developer.microsoft.com/windows/downloads).

- Weitere Informationen zum Erstellen von cloudbasierten Diensten finden Sie auf der [Microsoft Azure-Website](http://azure.microsoft.com/documentation/).

- Weitere Informationen zum Erstellen von Websites und Web-Apps [finden Sie auf der ASP.NET-Website](http://www.asp.net/get-started/websites).

  > [!NOTE]
  > Sie können eine leere ASP.NET-Website erstellen und für die HTML-, CSS- und JavaScript-Programmierung verwenden. Die von ASP.NET bereitgestellte Datei "Webconfig" ermöglicht das Debuggen in Visual Studio (Sie können auch die F12-Tools beim Ausführen der App verwenden).

  Der JavaScript-Editor in Visual Studio bietet IntelliSense-Unterstützung. Weitere Informationen finden Sie unter [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="whats-new-in-javascript"></a>Neues bei JavaScript
 Die neuen Funktionen für JavaScript werden in der folgenden Tabelle aufgeführt

|Feature|Beschreibung|
|-------------|-----------------|
|Klassen|Neue Syntax unterstützt die Deklaration von [Klassen](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/class).|
|Promises|[Promises](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) ermöglichen eine leichtere und sauberere asynchrone Codierung. Promise-Konstruktoren werden unterstützt, zusammen mit den Hilfsmethoden `all` und `race`.|
|Iterators|Jetzt können Sie iterierbare Objekte (einschließlich Arrays, arrayähnliche Objekte und Iteratoren) wiederholt durchlaufen und dabei einen benutzerdefinierten Iterationshaken mit Anweisungen aufrufen, die für den Wert jeder einzelnen Eigenschaft ausgeführt werden sollen. Weitere Informationen finden Sie unter [Iteratoren und Generatoren](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Iterators_and_Generators). **Hinweis**:  Generatoren werden noch nicht unterstützt.|
|Pfeilfunktionen|Die Pfeilfunktion (= >) bietet eine Kurzsyntax für das Schlüsselwort `function`, dass eine lexikalische `this`-Bindung darstellt.|
|Neue Methoden für integrierte Objekte|Die integrierten Objekte [Array-Objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array), [Math-Objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Math), [Number-Objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number), [Object-Objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object) und [String-Objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String) umfassen viele neue Hilfsfunktionen und Eigenschaften zum Bearbeiten und Überprüfen von Daten.|
|Verbesserungen des Objektliterals|Objekte unterstützen nun berechnete Eigenschaften, präzise Methodendefinitionen und eine Kurzsyntax für Eigenschaften, deren Wert für eine gleichnamige Variable initialisiert wird. Weitere Informationen finden Sie unter [Erstellen von Objekten](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object).|
|Proxys|[Proxys](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Proxy) ermöglichen ein benutzerdefiniertes Verhalten für Objekte.|
|Rest-Parameter|Mit Rest-Parametern können Sie aufeinanderfolgende Argumente in einem Funktionsaufruf in einen Array umwandeln. Weitere Informationen finden Sie unter [Funktionen](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function).|
|Spread-Operator|Der [Spread-Operator](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Spread_operator) (`…`) erweitert iterierbare Ausdrücke in einzelne Argumente. Beispielsweise entspricht `a.b(…array)` ungefähr `a.b.apply(a, array)`.|
|Symbole|Mit [Symbol](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Symbol)-Objekten können Eigenschaften vorhandenen Objekten hinzugefügt werden, ohne dass mögliche Probleme mit den vorhandenen Objekteigenschaften, unerwünschte Sichtbarkeit oder weitere unkoordinierte Hinzufügungen durch anderen Code bestehen.|
|Vorlagenzeichenfolgen|[Vorlagenzeichenfolgen](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Template_literals) sind Zeichenfolgenliterale, mit denen Ausdrücke ausgewertet und mit dem Zeichenfolgenliteral verkettet werden können.|
|Unicode-Verbesserungen|Es wurden Verbesserungen der Unicode-Unterstützung vorgenommen. Beispielsweise unterstützt ein neues Escapesequenzformat astrale Codepunkte (Codepunkte mit mehr als vier Hexadezimalziffern). Weitere Informationen finden Sie unter [Sonderzeichen](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Regular_Expressions#Types_of_special_characters).|
|WeakSet|Ein [WeakSet](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/WeakSet) ist eine Auflistung von Objekten, für die eine Garbage Collection durchgeführt wird, wenn nicht an anderer Stelle auf sie verwiesen wird.|
