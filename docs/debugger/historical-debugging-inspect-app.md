---
title: Überprüfen Sie Ihre app mit verlaufsbezogenem debugging | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2309a3213344607fa0f5b2f626fc67af2eff8f79
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542337"
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio"></a>Überprüfen Sie Ihre app mit IntelliTrace verlaufsbezogenes Debuggen in Visual Studio
Sie können [verlaufsbezogenes debugging](../debugger/historical-debugging.md) rückwärts und Vorwärts durch die Ausführung Ihrer Anwendung und ihren Status überprüfen.  
  
Sie können IntelliTrace in Visual Studio Enterprise-Edition jedoch nicht den Professional oder Community Editions verwenden.  
  
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
  
 Wir gehen davon aus, die der erwartete Wert des `resultInt` nach dem Aufruf `AddAll()` 20 (das Ergebnis des inkrementierens `testInt` 20-Mal). (Wir außerdem davon aus, dass Sie nicht, dass den Fehler in angezeigt `AddInt()`). Doch das Ergebnis ist jedoch tatsächlich 44. Wie finden wir den Fehler, ohne `AddAll()` schrittweise 10 Mal durchzugehen? Wir können die verlaufsbezogenes debugging verwenden, um den Fehler schneller und einfacher zu finden. Gehen Sie dabei folgendermaßen vor:  
  
1.  In **Tools > Optionen > IntelliTrace > allgemeine**, stellen Sie sicher, dass IntelliTrace aktiviert ist, und wählen **IntelliTrace-Ereignisse und Aufrufinformationen**. Wenn Sie diese Option nicht auswählen, wird Ihnen der Navigationsbundsteg nicht angezeigt (sie Erläuterung weitere unten).  
  
2.  Legen Sie einen Haltepunkt in der Zeile `Console.WriteLine(resultInt);` fest.  
  
3.  Beginnen Sie mit dem Debuggen. Der Code wird bis zum Haltepunkt ausgeführt. In der **"lokal"** Fenster sehen Sie, dass der Wert des `resultInt` 44.  
  
4.  Öffnen der **Diagnosetools** Fenster (**Debuggen > Diagnosetools anzeigen**). Das Code-Fenster sieht wie folgt aus:  
  
     ![Codefenster am Haltepunkt](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5.  Neben dem linken Rand sollte ein doppelter Pfeil angezeigt werden, genau über dem Haltepunkt. Dieser Bereich wird als Navigationsbundsteg bezeichnet und dient zum verlaufsbezogenen Debuggen. Klicken Sie auf den Pfeil.  
  
     Im Codefenster sollte Ihnen die vorangegangene Codezeile (`int resultInt = AddIterative(testInt);`) rosa gefärbt angezeigt werden. Über dem Fenster sollte eine Meldung angezeigt werden, die Sie sich nun im verlaufsbezogenes debugging befinden.  
  
     Das Codefenster sieht nun folgendermaßen aus:  
  
     ![Codefenster im verlaufsbezogenen Debugmodus](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6.  Nachdem Sie in Schritt können die `AddAll()` Methode (**F11**, oder die **Einzelschritt** Schaltfläche auf dem Navigationsbundsteg. Ein Schritt vorwärts (**F10**, oder **zum nächsten Aufruf wechseln** auf dem Navigationsbundsteg. Die rosa Linie befindet sich jetzt in der `j = AddInt(j);`-Zeile. **F10** in diesem Fall nicht in die nächste Zeile des Codes schrittweise. Stattdessen fährt es mit dem nächsten Funktionsaufruf fort. Das verlaufsbezogene Debugging navigiert von Aufruf zu Aufruf, und überspringt Codezeilen, die nicht in einem Funktionsaufruf enthalten sind.  
  
7.  Nun in die `AddInt()`-Methode einsteigen. Der Fehler in diesem Code sollte Ihnen sofort angezeigt werden.  

## <a name="next-steps"></a>Nächste Schritte

Dieses Verfahren oberflächlich nur des verlaufsbezogenen Debugging möglich.

- Zum Anzeigen von Momentaufnahmen während des Debuggens finden Sie unter [überprüfen Sie die vorherigen app-Status, die mithilfe von IntelliTrace](../debugger/view-historical-application-state.md).
- Weitere Informationen zu den verschiedenen Einstellungen und die Auswirkungen der verschiedenen Schaltflächen auf dem Navigationsbundsteg finden Sie unter [IntelliTrace-Funktionen](../debugger/intellitrace-features.md).