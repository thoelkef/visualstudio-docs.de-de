---
title: "Debuggen von LINQ | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen, LINQ"
  - "LINQ, Debuggen"
  - "LINQ, Bearbeiten und Fortfahren"
  - "LINQ, Ausführen in Einzelschritten"
  - "LINQ, Anzeigen von Ergebnissen im Debugger"
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debuggen von LINQ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unterstützt das Debuggen von Language Integrated Query \(LINQ\)\-Code, wobei einige Einschränkungen bestehen. Die meisten Debugfunktionen arbeiten mit LINQ\-Anweisungen, z. B. für das schrittweise Ausführen, das Festlegen von Haltepunkten und das Anzeigen von Ergebnissen in Debuggerfenstern.  In diesem Thema werden die Haupteinschränkungen des LINQ\-Debuggens beschrieben.  
  
## In diesem Thema  
 [Anzeigen von LINQ-Ergebnissen](../debugger/debugging-linq.md#BKMK_ViewingLINQResults)  
  
 [Stepping und LINQ](../debugger/debugging-linq.md#BKMK_SteppingAndLinq)  
  
 [Bearbeiten und Fortfahren wird für LINQ nicht unterstützt](../debugger/debugging-linq.md#BKMK_EditandContinueNotSupportedforLINQ)  
  
##  <a name="BKMK_ViewingLINQResults"></a> Anzeigen von LINQ\-Ergebnissen  
 Das Ergebnis einer LINQ\-Anweisung kann mithilfe von DataTips, über das Überwachungsfenster oder im Dialogfeld Schnellüberwachung angezeigt werden.  Bei Verwendung eines Quellcodefensters können Sie den Mauszeiger auf eine Abfrage im Quellcodefenster bewegen, woraufhin ein DataTip eingeblendet wird.  Sie können eine LINQ\-Variable kopieren und in das Überwachungsfenster oder das Dialogfeld Schnellüberwachung einfügen.  
  
 In LINQ wird eine Abfrage nicht ausgewertet, wenn sie erstellt oder deklariert wird, sondern wenn die Abfrage verwendet wird.  Deshalb verfügt die Abfrage erst nach der Auswertung über einen Wert.  Eine vollständige Beschreibung zum Erstellen und Auswerten von Abfragen finden Sie unter [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries) oder [Schreiben der ersten LINQ\-Abfrage](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query).  
  
 Um das Ergebnis einer Abfrage anzuzeigen, muss es vom Debugger ausgewertet werden.  Diese implizite Auswertung, die beim Anzeigen eines LINQ\-Abfrageergebnisses im Debugger erfolgt, hat einige Auswirkungen, die berücksichtigt werden sollten:  
  
-   Jede Auswertung der Abfrage dauert einige Zeit.  Das Erweitern des Ergebnisknotens nimmt ebenfalls Zeit in Anspruch.  Bei einigen Abfragen kann eine wiederholte Auswertung zu beträchtlichen Leistungseinbußen führen.  
  
-   Die Auswertung einer Abfrage kann dazu führen, dass der Datenwert oder Zustand des Programms geändert wird.  Nicht alle Abfragen verfügen über Nebeneffekte.  Um festzustellen, ob eine Abfrage ohne Nebeneffekte sicher ausgewertet werden kann, sollten Sie den Code verstehen, durch den die Abfrage implementiert wird.  
  
##  <a name="BKMK_SteppingAndLinq"></a> Stepping und LINQ  
 Wenn Sie LINQ\-Code debuggen, weist die schrittweise Ausführung teilweise ein abweichendes Verhalten auf, das Sie beachten sollten.  
  
### LINQ to SQL  
 In LINQ to SQL\-Abfragen befindet sich der Prädikatcode außerhalb der Kontrolle des Debuggers.  Deshalb können Sie keinen Einzelschritt in den Prädikatcode ausführen.  Jede Abfrage, die in eine Ausdrucksbaumstruktur kompiliert wird, generiert Code, der sich außerhalb der Kontrolle des Debuggers befindet.  
  
### Schrittweise Ausführung in Visual Basic  
 Wenn der Debugger bei der schrittweisen Ausführung eines Visual Basic\-Programms auf eine Abfragedeklaration trifft, wird kein Einzelschritt in die Deklaration ausgeführt, sondern die gesamte Deklaration als einzelne Anweisung hervorgehoben.  Dieses Verhalten tritt auf, da die Abfrage erst bei ihrem Aufruf ausgewertet wird.  Weitere Informationen finden Sie unter [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq).  
  
 Wenn Sie den folgenden Beispielcode schrittweise durchlaufen, hebt der Debugger die Abfragedeklaration bzw. Abfrageerstellung als einzelne Anweisung hervor.  
  
```  
Function MyFunction(ByVal x As Char)  
    Return True  
End Function  
  
Sub Main()  
    'Query creation  
    Dim x = From it In "faoaoeua" _  
            Where MyFunction(it) _  
            Select New With {.a = it}  
  
    ' Query execution  
    For Each cur In x  
        Console.WriteLine(cur.ToString())  
    Next  
End Sub  
```  
  
 Beim nächsten Schritt hebt der Debugger `For Each cur In x` hervor.  Im nächsten Schritt führt der Debugger einen Einzelschritt in die `MyFunction`\-Funktion aus.  Nach dem schrittweisen Durchlaufen von `MyFunction` führt der Debugger einen Rücksprung zu `Console.WriteLine(cur.ToSting())` aus.  Obwohl der Prädikatcode vom Debugger ausgewertet wird, wird zu keinem Zeitpunkt ein Einzelschritt in den Prädikatcode in der Abfragedeklaration ausgeführt.  
  
### Ersetzen eines Prädikats durch eine Funktion, um die schrittweise Ausführung zu ermöglichen \(Visual Basic\)  
 Falls Sie Prädikatcode zu Debugzwecken schrittweise durchlaufen müssen, können Sie das Prädikat durch den Aufruf einer Funktion ersetzen, die den ursprünglichen Prädikatcode enthält.  Nehmen Sie z. B. an, Sie hätten folgenden Code:  
  
```  
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
```  
  
 Sie können den Prädikatcode in eine neue Funktion mit der Bezeichnung `IsEven` verschieben:  
  
```  
Dim items () as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where IsEven(nextInt) Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
...   
Function IsEven(item As =Integer) as Boolean  
      Return item Mod 2 = 0  
End Function  
```  
  
 Die überarbeitete Abfrage ruft bei jedem Durchlauf von `items` die `IsEven`\-Funktion auf.  Mithilfe der Debuggerfenster können Sie feststellen, ob die einzelnen Elemente die angegebene Bedingung erfüllen und den Code in `IsEven` schrittweise ausführen.  Das Prädikat in diesem Beispiel ist recht einfach gehalten.  Falls Ihr zu debuggendes Prädikat jedoch komplizierter ist, kann diese Technik sehr hilfreich sein.  
  
##  <a name="BKMK_EditandContinueNotSupportedforLINQ"></a> Bearbeiten und Fortfahren wird für LINQ nicht unterstützt  
 Bearbeiten und Fortfahren unterstützt keine Änderungen an LINQ\-Abfragen.  Wenn Sie eine LINQ\-Anweisung während einer Debugsitzung hinzufügen, entfernen oder ändern, wird ein Dialogfeld mit dem Hinweis eingeblendet, dass die Änderung von Bearbeiten und Fortfahren nicht unterstützt wird.  An diesem Punkt können Sie entweder die Änderungen rückgängig machen oder die Debugsitzung beenden und eine neue Sitzung mit dem bearbeiteten Code starten.  
  
 Außerdem wird das Ändern des Typs oder Wertes einer in einer LINQ\-Anweisung verwendeten Variablen von Bearbeiten und Fortfahren nicht unterstützt.  Auch hier können Sie entweder die Änderungen rückgängig machen oder die Debugsitzung beenden und neu starten.  
  
 In C\# kann Bearbeiten und Fortfahren nicht für Code in einer Methode verwendet werden, die eine LINQ\-Abfrage enthält.  
  
 In Visual Basic kann Bearbeiten und Fortfahren für Nicht\-LINQ\-Code verwendet werden, und zwar selbst in einer Methode, die eine LINQ\-Abfrage enthält.  Sie können Code vor der LINQ\-Anweisung sogar dann hinzufügen oder entfernen, wenn sich die Änderungen auf die Zeilennummer der LINQ\-Abfrage auswirken.  Das Debugverhalten in Visual Basic für Nicht\-LINQ\-Code bleibt dasselbe wie vor der Einführung von LINQ.  Es ist nicht möglich, eine LINQ\-Abfrage zu ändern, hinzuzufügen oder zu entfernen, es sei denn, Sie beenden den Debugvorgang, um die Änderungen zu übernehmen.  
  
## Siehe auch  
 [Debugging SQL](http://msdn.microsoft.com/de-de/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)   
 [Nebeneffekte und Ausdrücke](../Topic/Side%20Effects%20and%20Expressions.md)   
 [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)   
 [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)