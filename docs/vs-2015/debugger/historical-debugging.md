---
title: Verlaufsbezogenes Debugging | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7db175535e0eebdcf1974f0f85123959ba5a3ed
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961872"
---
# <a name="historical-debugging"></a>Verlaufsbezogenes Debugging
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das verlaufsbezogene Debuggen ist ein Debug-Modus, der von den durch IntelliTrace erfassten Informationen abhängig ist. Dadurch können Sie die Ausführung Ihrer Anwendung rückwärts und vorwärts durchlaufen und ihren Status überprüfen.  
  
 Sie können IntelliTrace in der Visual Studio Enterprise Edition verwenden(jedoch nicht in der Professional oder Community Edition).  
  
## <a name="why-use-historical-debugging"></a>Warum verlaufsbezogenes Debugging?  
 Das Festlegen von Haltepunkten zum Auffinden von Fehlern ist eher eine unsichere Angelegenheit. Sie legen einen Haltepunkt in der Nähe der Stelle im Code fest, an der Sie einen Fehler vermuten, führen dann die Anwendung im Debugger aus, hoffen, dass der Haltepunkt erreicht wird, und dass die Stelle, an der die Ausführung unterbrochen wurde, die Ursache des Fehlers aufdeckt. Wenn dies nicht der Fall ist, müssen Sie versuchen, einen Haltepunkt an anderer Stelle im Code festzulegen und den Debugger erneut auszuführen. Diese Testschritte müssen Sie so oft wiederholen, bis Sie das Problem gefunden haben.  
  
 ![Festlegen eines Haltepunkts](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Mit IntelliTrace und dem verlaufsbezogenen Debugging können Sie Ihre Anwendung durchgehen und den Status überprüfen (Aufrufliste und lokale Variablen), ohne Haltepunkte festzulegen, den Debugvorgang neu zu starten und  die Testschritte zu wiederholen. Dadurch sparen Sie viel Zeit, besonders wenn der Fehler sich tief in einem Testszenario verbirgt, das azum Ausführen viel Zeit erfordert.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>Wie beginne ich mit dem verlaufsbezogenen Debuggen?  
 IntelliTrace ist standardmäßig aktiviert. Sie müssen lediglich entscheiden, welche Ereignisse und Funktionsaufrufe für Sie von Interesse sind. Weitere Informationen zum Definieren von Elementen, die Sie suchen möchten, finden Sie unter [IntelliTrace-Funktionen](../debugger/intellitrace-features.md). Eine schrittweise Anleitung für das Debuggen mit IntelliTrace finden Sie unter [Exemplarische Vorgehensweise: Verwenden von IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
## <a name="navigating-your-code-with-historical-debugging"></a>Navigieren durch Ihren Code mit verlaufsbezogenem Debugging  
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
  
 Wir gehen davon aus, dass der erwartete Wert des `resultInt` nach dem Aufruf von `AddAll()` 20 beträgt (das Ergebnis des Inkrementierens von `testInt` x 20). (Gehen wir außerdem davon aus, dass Ihnen der Fehler in `AddInt()`) nicht angezeigt wird, das Ergebnis jedoch tatsächlich 44 beträgt. Wie finden wir den Fehler, ohne `AddAll()` schrittweise 10 Mal durchzugehen? Wir können das verlaufsbezogene Debugging verwenden, um Fehler schneller und leichter zu finden. Gehen Sie folgendermaßen vor:  
  
1. Stellen Sie unter Extras / Optionen / IntelliTrace / Allgemein sicher, dass IntelliTrace aktiviert ist, wählen Sie die IntelliTrace-Ereignisse aus und rufen Sie die Informationsoption auf. Wenn Sie diese Option nicht auswählen, wird Ihnen der Navigationsbundsteg nicht angezeigt (sie Erläuterung weitere unten).  
  
2. Legen Sie einen Haltepunkt in der Zeile `Console.WriteLine(resultInt);` fest.  
  
3. Beginnen Sie mit dem Debuggen. Der Code wird bis zum Haltepunkt ausgeführt. Im Fenster **Lokal** wird Ihnen für `resultInt` der Wert 44 angezeigt.  
  
4. Öffnen der **Diagnosetools** Fenster (**Debuggen / anzeigen Diagnosetools**). Das Code-Fenster sieht wie folgt aus:  
  
    ![Codefenster am Haltepunkt](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5. Neben dem linken Rand sollte ein doppelter Pfeil angezeigt werden, genau über dem Haltepunkt. Dieser Bereich wird als Navigationsbundsteg bezeichnet und dient zum verlaufsbezogenen Debuggen. Klicken Sie auf den Pfeil.  
  
    Im Codefenster sollte Ihnen die vorangegangene Codezeile (`int resultInt = AddIterative(testInt);`) rosa gefärbt angezeigt werden. Über dem Fenster sollte eine Meldung angezeigt werden, dass Sie sich nun im verlaufsbezogenes Debugging befinden.  
  
    Das Codefenster sieht nun folgendermaßen aus:  
  
    ![Codefenster im verlaufsbezogenen Debugmodus](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6. Jetzt können Sie per Einzelschritt auf die `AddAll()`-Methode zugreifen (**F11** oder die **Einzelschritt**-Schaltfläche auf dem Navigationsbundsteg). Gehen Sie mit **F10** oder mit **Zum nächsten Aufruf wechseln** im Navigationsbundsteg schrittweise vorwärts. Die rosa Linie befindet sich jetzt in der `j = AddInt(j);`-Zeile. Durch Drücken von **F10** gelangen Sie in diesem Fall nicht in die nächste Codezeile. Stattdessen fährt es mit dem nächsten Funktionsaufruf fort. Das verlaufsbezogene Debugging navigiert von Aufruf zu Aufruf, und überspringt Codezeilen, die nicht in einem Funktionsaufruf enthalten sind.  
  
7. Nun in die `AddInt()`-Methode einsteigen. Der Fehler in diesem Code sollte Ihnen sofort angezeigt werden.  
  
   Dieses Verfahren behandelt die Möglichkeiten des verlaufsbezogenen Debugging nur oberflächlich. Weitere Informationen über die unterschiedlichen Einstellungen und Auswirkungen der verschiedenen Schaltflächen auf dem Navigationsbundsteg finden Sie unter [IntelliTrace-Funktionen](../debugger/intellitrace-features.md).
