---
title: "JavaScript in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# JavaScript in Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

JavaScript ist eine der Hauptprogrammiersprachen in Visual Studio.  Zum Schreiben von JavaScript\-Code in der Visual Studio\-IDE können Sie die meisten oder alle Standardbearbeitungshilfen \(Codeausschnitte, IntelliSense, usw.\) verwenden.  Sie können JavaScript\-Code für viele Arten von Anwendungen und Dienste schreiben.  
  
 Die Referenzdokumentation für JavaScript finden Sie unter [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).  
  
 Unter Umständen sind bestimmte Versionen von Visual Studio oder bestimmte Visual Studio\-Erweiterungen erforderlich, um bestimmte Anwendungstypen und Dienste mit HTML und JavaScript zu entwickeln.  Die folgende Liste enthält Links für weitere Informationen.  
  
-   Für das Erstellen von plattformübergreifenden Apps mit Apache Cordova [laden Sie die Visual Studio\-Tools für Apache Cordova](http://go.microsoft.com/fwlink/p/?LinkId=397606) herunter.  
  
-   Zum Erstellen von [Windows Store\-](http://dev.windows.com/develop), [Windows Phone\-](http://dev.windows.com/develop) und universellen Apps \(mit Unterstützung beider Plattformen\) [laden Sie die entsprechenden Tools herunter](http://dev.windows.com/en-us/develop/downloads).  
  
-   Weitere Informationen zum Erstellen von Cloud\-basierten Diensten finden Sie auf der [Microsoft Azure\-Website](http://azure.microsoft.com/documentation/).  
  
-   Weitere Informationen zum Erstellen von Websites und Webanwendungen [finden Sie auf der ASP .NET\-Website](http://www.asp.net/get-started/websites).  
  
    > [!NOTE]
    >  Sie können eine leere ASP.NET\-Website erstellen und für die HTML\-, CSS\- und JavaScript\-Programmierung verwenden.  Die von ASP.NET bereitgestellte Datei "Webconfig" ermöglicht das Debuggen in Visual Studio \(Sie können auch die F12\-Tools beim Ausführen der App verwenden\).  
  
 Der JavaScript\-Editor in Visual Studio bietet IntelliSense\-Unterstützung.  Weitere Informationen finden Sie unter [JavaScript IntelliSense](../ide/javascript-intellisense.md).  
  
## Neues bei JavaScript  
 Die neuen Funktionen für JavaScript werden in der folgenden Tabelle aufgeführt  
  
|Funktion|Beschreibung|  
|--------------|------------------|  
|Klassen|Neue Syntax unterstützt die Deklaration von [Klassen](../Topic/class%20Statement%20\(JavaScript\).md).|  
|Promises|[Promises](../Topic/Promise%20Object%20\(JavaScript\).md) ermöglichen eine leichtere und sauberere asynchrone Codierung.  Promise\-Konstruktoren werden unterstützt, zusammen mit den Hilfsmethoden `all` und `race`.|  
|Iteratoren|Jetzt können Sie iterierbare Objekte \(einschließlich Arrays, arrayähnliche Objekte und Iteratoren\) wiederholt durchlaufen und dabei einen benutzerdefinierten Iterationshaken mit Anweisungen aufrufen, die für den Wert jeder einzelnen Eigenschaft ausgeführt werden sollen.  Weitere Informationen finden Sie unter [Iteratoren und Generatoren](../Topic/Iterators%20and%20Generators%20\(JavaScript\).md). **Note:**  Generatoren werden noch nicht unterstützt.|  
|Pfeilfunktionen|Die Pfeilfunktion \(\= \>\) bietet eine Kurzsyntax für das Schlüsselwort `function`, dass eine lexikalische `this`\-Bindung darstellt.|  
|Neue Methoden für integrierte Objekte|Die integrierten Objekte [Array\-Objekt](../Topic/Array%20Object%20\(JavaScript\).md), [Math\-Objekt](../Topic/Math%20Object%20\(JavaScript\).md), [Number\-Objekt](../Topic/Number%20Object%20\(JavaScript\).md), [Object\-Objekt](../Topic/Object%20Object%20\(JavaScript\).md) und [String\-Objekt](../Topic/String%20Object%20\(JavaScript\).md) umfassen viele neue Hilfsfunktionen und Eigenschaften zum Bearbeiten und Überprüfen von Daten.|  
|Verbesserungen des Objektliterals|Objekte unterstützen nun berechnete Eigenschaften, präzise Methodendefinitionen und eine Kurzsyntax für Eigenschaften, deren Wert für eine gleichnamige Variable initialisiert wird.  Weitere Informationen finden Sie unter [Erstellen von Objekten](../Topic/Creating%20Objects%20\(JavaScript\).md).|  
|Proxys|[Proxys](../Topic/Proxy%20Object%20\(JavaScript\).md) ermöglichen ein benutzerdefiniertes Verhalten für Objekte.|  
|Rest\-Parameter|Mit Rest\-Parametern können Sie aufeinanderfolgende Argumente in einem Funktionsaufruf in einen Array umwandeln.  Weitere Informationen finden Sie unter [Funktionen](../Topic/Functions%20\(JavaScript\).md).|  
|Spread\-Operator|Der [Spread\-Operator](../Topic/Spread%20Operator%20\(...\)%20\(JavaScript\).md) \(`…`\) erweitert iterierbare Ausdrücke in einzelne Argumente.  Beispielsweise entspricht `a.b(…array)` ungefähr `a.b.apply(a, array)`.|  
|Symbole|Mit [Symbol](../Topic/Symbol%20Object%20\(JavaScript\).md)\-Objekten können Eigenschaften zu vorhandenen Objekten hinzugefügt werden, ohne dass mögliche Probleme mit den vorhandenen Objekteigenschaften, unerwünschte Sichtbarkeit oder weitere unkoordinierte Hinzufügungen durch anderen Code bestehen.|  
|Vorlagenzeichenfolgen|[Vorlagenzeichenfolgen](../Topic/Template%20Strings%20\(JavaScript\).md) sind Zeichenfolgenliterale, mit denen Ausdrücke ausgewertet und mit dem Zeichenfolgenliteral verkettet werden können.|  
|Unicode\-Verbesserungen|Es wurden Verbesserungen der Unicode\-Unterstützung vorgenommen.  Beispielsweise unterstützt ein neues Escapesequenzformat astrale Codepunkte \(Codepunkte mit mehr als vier Hexadezimalziffern\).  Weitere Informationen finden Sie unter [Sonderzeichen](../Topic/Special%20Characters%20\(JavaScript\).md)|  
|WeakSet|Ein [WeakSet](../Topic/WeakSet%20Object%20\(JavaScript\).md) ist eine Auflistung von Objekten, für die eine Garbage Collection durchgeführt wird, wenn nicht an anderer Stelle auf sie verwiesen wird.|