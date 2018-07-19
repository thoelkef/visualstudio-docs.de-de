---
title: Debuggen von LINQ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ca92fe5142957faf85ead5f9c9068b062d25a8d
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056694"
---
# <a name="debugging-linq"></a>Debuggen von LINQ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unterstützt das Debuggen von Language Integrated Query (LINQ)-Code, wobei einige Einschränkungen bestehen. Die meisten Debugfunktionen arbeiten mit LINQ-Anweisungen, z. B. für das schrittweise Ausführen, das Festlegen von Haltepunkten und das Anzeigen von Ergebnissen in Debuggerfenstern. Dieses Thema beschreibt die haupteinschränkungen des LINQ-Debuggens.  
  
##  <a name="BKMK_ViewingLINQResults"></a> Anzeigen von LINQ-Ergebnissen  
 Das Ergebnis einer LINQ-Anweisung kann mithilfe von DataTips, über das Überwachungsfenster oder im Dialogfeld Schnellüberwachung angezeigt werden. Bei Verwendung eines Quellcodefensters können Sie den Mauszeiger auf eine Abfrage im Quellcodefenster bewegen, woraufhin ein DataTip eingeblendet wird. Sie können eine LINQ-Variable kopieren und in das Überwachungsfenster oder das Dialogfeld Schnellüberwachung einfügen.  
  
 In LINQ wird eine Abfrage nicht ausgewertet, wenn sie erstellt oder deklariert wird, sondern wenn die Abfrage verwendet wird. Deshalb verfügt die Abfrage erst nach der Auswertung über einen Wert. Eine vollständige Beschreibung der Abfrage erstellen und auswerten, finden Sie unter [Introduction to LINQ Queries (c#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries) oder [Schreiben Ihrer ersten LINQ-Abfrage](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query).  
  
 Um das Ergebnis einer Abfrage anzuzeigen, muss es vom Debugger ausgewertet werden. Diese implizite Auswertung, die beim Anzeigen eines LINQ-Abfrageergebnisses im Debugger erfolgt, hat einige Auswirkungen, die berücksichtigt werden sollten:  
  
-   Jede Auswertung der Abfrage dauert einige Zeit. Das Erweitern des Ergebnisknotens nimmt ebenfalls Zeit in Anspruch. Bei einigen Abfragen kann eine wiederholte Auswertung zu beträchtlichen Leistungseinbußen führen.  
  
-   Die Auswertung einer Abfrage kann dazu führen, dass der Datenwert oder Zustand des Programms geändert wird. Nicht alle Abfragen verfügen über Nebeneffekte. Um festzustellen, ob eine Abfrage ohne Nebeneffekte sicher ausgewertet werden kann, sollten Sie den Code verstehen, durch den die Abfrage implementiert wird.  
  
##  <a name="BKMK_SteppingAndLinq"></a> Stepping und LINQ  
 Wenn Sie LINQ-Code debuggen, weist die schrittweise Ausführung teilweise ein abweichendes Verhalten auf, das Sie beachten sollten.  
  
### <a name="linq-to-sql"></a>LINQ to SQL  
 In LINQ to SQL-Abfragen befindet sich der Prädikatcode außerhalb der Kontrolle des Debuggers. Deshalb können Sie keinen Einzelschritt in den Prädikatcode ausführen. Jede Abfrage, die in eine Ausdrucksbaumstruktur kompiliert wird, generiert Code, der sich außerhalb der Kontrolle des Debuggers befindet.  
  
### <a name="stepping-in-visual-basic"></a>Schrittweise Ausführung in Visual Basic  
 Wenn der Debugger bei der schrittweisen Ausführung eines Visual Basic-Programms auf eine Abfragedeklaration trifft, wird kein Einzelschritt in die Deklaration ausgeführt, sondern die gesamte Deklaration als einzelne Anweisung hervorgehoben. Dieses Verhalten tritt auf, da die Abfrage erst bei ihrem Aufruf ausgewertet wird. Weitere Informationen finden Sie unter [Einführung in LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq).  
  
 Wenn Sie den folgenden Beispielcode schrittweise durchlaufen, hebt der Debugger die Abfragedeklaration bzw. Abfrageerstellung als einzelne Anweisung hervor.  
  
```vb
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
  
 Beim nächsten Schritt hebt der Debugger `For Each cur In x` hervor. Im nächsten Schritt führt der Debugger einen Einzelschritt in die `MyFunction`-Funktion aus. Nach dem schrittweisen Durchlaufen von `MyFunction` führt der Debugger einen Rücksprung zu `Console.WriteLine(cur.ToSting())` aus. Obwohl der Prädikatcode vom Debugger ausgewertet wird, wird zu keinem Zeitpunkt ein Einzelschritt in den Prädikatcode in der Abfragedeklaration ausgeführt.  
  
### <a name="replacing-a-predicate-with-a-function-to-enable-stepping-visual-basic"></a>Ersetzen eines Prädikats durch eine Funktion, um die schrittweise Ausführung zu ermöglichen (Visual Basic)  
 Falls Sie Prädikatcode zu Debugzwecken schrittweise durchlaufen müssen, können Sie das Prädikat durch den Aufruf einer Funktion ersetzen, die den ursprünglichen Prädikatcode enthält. Nehmen Sie z. B. an, Sie hätten folgenden Code:  
  
```vb
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
```  
  
 Sie können den Prädikatcode in eine neue Funktion mit der Bezeichnung `IsEven` verschieben:  
  
```vb
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
  
 Die überarbeitete Abfrage ruft bei jedem Durchlauf von `IsEven` die `items`-Funktion auf. Mithilfe der Debuggerfenster können Sie feststellen, ob die einzelnen Elemente die angegebene Bedingung erfüllen und den Code in `IsEven` schrittweise ausführen. Das Prädikat in diesem Beispiel ist recht einfach gehalten. Falls Ihr zu debuggendes Prädikat jedoch komplizierter ist, kann diese Technik sehr hilfreich sein.  
  
##  <a name="BKMK_EditandContinueNotSupportedforLINQ"></a> Bearbeiten Sie und fortfahren Sie wird für LINQ nicht unterstützt.  
 Bearbeiten und Fortfahren unterstützt LINQ-Abfragen mit Einschränkungen. Weitere Informationen finden Sie unter [EnC unterstützt Änderungen](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von SQL](http://msdn.microsoft.com/en-us/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)    
 [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)   
 [Introduction to LINQ Queries (C#) (Einführung in LINQ-Abfragen (C#))](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)   
 [Einführung in LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
