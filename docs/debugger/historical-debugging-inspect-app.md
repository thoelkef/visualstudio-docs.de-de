---
title: Überprüfen Sie Ihre app mit verlaufsbezogenem debugging | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0022d94d8bb786340dba5d2d412bbbd46585e35e
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227706"
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio-c-visual-basic-c"></a>Überprüfen Sie Ihre app mit IntelliTrace verlaufsbezogenes Debuggen in Visual Studio (C#, Visual Basic, C++)

Sie können [verlaufsbezogenes debugging](../debugger/historical-debugging.md) rückwärts und Vorwärts durch die Ausführung Ihrer Anwendung und ihren Status überprüfen.  
  
Sie können IntelliTrace in der Visual Studio Enterprise Edition verwenden, jedoch nicht in der Professional oder Community Edition.  
  
## <a name="navigate-your-code-with-historical-debugging"></a>Navigieren Sie in Ihrem Code mit verlaufsbezogenem debugging

 Beginnen wir mit einem einfachen Programm, das einen Fehler aufweist. Fügen Sie in einer C#-Konsolenanwendung folgenden Code hinzu:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    int resultInt = AddAll(testInt);  
    Console.WriteLine(resultInt);  
}  
private static int AddAll(int j)  
{  
    for (int i = 0; i < 20; i++)  
    {  
        j = AddInt(j);  
    }  
    return j;  
}  
  
private static int AddInt(int add)  
{  
    if (add == 10)  
    {  
        return add += 25;  
    }  
    return ++add;  
}  
```  
  
 Wir gehen davon aus, dass der erwartete Wert des `resultInt` nach dem Aufruf von `AddAll()` 20 beträgt (das Ergebnis des Inkrementierens von `testInt` × 20). (Wir außerdem davon aus, dass Sie nicht, dass den Fehler in angezeigt `AddInt()`). Doch das Ergebnis ist jedoch tatsächlich 44. Wie finden wir den Fehler, ohne `AddAll()` schrittweise 10 Mal durchzugehen? Wir können das verlaufsbezogene Debugging verwenden, um Fehler schneller und leichter zu finden. Gehen Sie dabei folgendermaßen vor:  
  
1.  In **Tools > Optionen > IntelliTrace > allgemeine**, stellen Sie sicher, dass IntelliTrace aktiviert ist, und wählen **IntelliTrace-Ereignisse und Aufrufinformationen**. Wenn Sie diese Option nicht auswählen, wird Ihnen der Navigationsbundsteg nicht angezeigt (sie Erläuterung weitere unten).  
  
2.  Legen Sie einen Haltepunkt in der Zeile `Console.WriteLine(resultInt);` fest.  
  
3.  Beginnen Sie mit dem Debuggen. Der Code wird bis zum Haltepunkt ausgeführt. Im Fenster **Lokal** wird Ihnen für `resultInt` der Wert 44 angezeigt.  
  
4.  Öffnen Sie das Fenster **Diagnosetools** (**Debuggen > Diagnosetools anzeigen**). Das Code-Fenster sieht wie folgt aus:  
  
     ![Codefenster am Haltepunkt](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5.  Neben dem linken Rand sollte ein doppelter Pfeil angezeigt werden, genau über dem Haltepunkt. Dieser Bereich wird als Navigationsbundsteg bezeichnet und dient zum verlaufsbezogenen Debuggen. Klicken Sie auf den Pfeil.  
  
     Im Codefenster sollte Ihnen die vorangegangene Codezeile (`int resultInt = AddIterative(testInt);`) rosa gefärbt angezeigt werden. Über dem Fenster sollte eine Meldung angezeigt werden, dass Sie sich nun im verlaufsbezogenes Debugging befinden.  
  
     Das Codefenster sieht nun folgendermaßen aus:  
  
     ![Codefenster im verlaufsbezogenen Debugmodus](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6.  Jetzt können Sie per Einzelschritt auf die `AddAll()`-Methode zugreifen (**F11** oder die **Einzelschritt**-Schaltfläche auf dem Navigationsbundsteg). Gehen Sie mit **F10** oder mit **Zum nächsten Aufruf wechseln** im Navigationsbundsteg schrittweise vorwärts. Die rosa Linie befindet sich jetzt in der `j = AddInt(j);`-Zeile. Durch Drücken von **F10** gelangen Sie in diesem Fall nicht in die nächste Codezeile. Stattdessen fährt es mit dem nächsten Funktionsaufruf fort. Das verlaufsbezogene Debugging navigiert von Aufruf zu Aufruf, und überspringt Codezeilen, die nicht in einem Funktionsaufruf enthalten sind.  
  
7.  Nun in die `AddInt()`-Methode einsteigen. Der Fehler in diesem Code sollte Ihnen sofort angezeigt werden.  

## <a name="next-steps"></a>Nächste Schritte

Dieses Verfahren behandelt die Möglichkeiten des verlaufsbezogenen Debugging nur oberflächlich.

- Zum Anzeigen von Momentaufnahmen während des Debuggens finden Sie unter [überprüfen Sie die vorherigen app-Status, die mithilfe von IntelliTrace](../debugger/view-historical-application-state.md).
- Weitere Informationen über die unterschiedlichen Einstellungen und Auswirkungen der verschiedenen Schaltflächen auf dem Navigationsbundsteg finden Sie unter [IntelliTrace-Funktionen](../debugger/intellitrace-features.md).