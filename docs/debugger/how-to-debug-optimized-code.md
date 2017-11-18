---
title: 'Vorgehensweise: Debuggen von optimiertem Code | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, in optimized code
- debugging [C++], optimized code
- optimization, debug builds
- debug builds, optimizing
- optimized code, debugging
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12f376932a260c556ac2ea2b0f1a2a53c59c752f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-optimized-code"></a>Gewusst wie: Debuggen von optimiertem Code
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
> [!NOTE]
>  Die [/zo (optimiertes Debuggen verbessern)](/cpp/build/reference/zo-enhance-optimized-debugging)(eingeführt in Visual Studio Update 3)-Compileroption generiert umfangreichere Debuginformationen für optimierten Code (Projekte, die nicht erstellt werden, mit der **/Od** Compileroption. Finden Sie unter [/o-Optionen (Code optimieren)](/cpp/build/reference/o-options-optimize-code)). Dazu gehört verbesserte Unterstützung zum Debuggen von lokalen Variablen und Inlinefunktionen.  
>   
>  [Bearbeiten und Fortfahren](../debugger/edit-and-continue-visual-csharp.md) ist deaktiviert, wenn die **/zo** -Compileroption verwendet wird.  
  
 Wenn der Compiler Code optimiert, werden die Anweisungen neu positioniert und organisiert. Hierdurch wird die Effizienz des kompilierten Codes erhöht. Aufgrund dieser Neuanordnung ist der Debugger nicht immer in der Lage, den Quellcode, der einer bestimmten Gruppe von Anweisungen entspricht, zu erkennen.  
  
 Durch die Optimierung können folgende Bereiche beeinflusst werden:  
  
-   Lokale Variablen, die durch den Optimierer entfernt oder an Speicherorte verschoben werden können, die vom Debugger nicht erkannt werden.  
  
-   Positionen in einer Funktion, die geändert werden, wenn Codeblöcke durch den Optimierer zusammenführt werden.  
  
-   Funktionsnamen für Rahmen der Aufrufliste, die möglicherweise falsch sind, wenn der Optimierer zwei Funktionen zusammenführt.  
  
 Die in der Aufrufliste angezeigten Rahmen sind fast immer korrekt, vorausgesetzt, es sind für alle Rahmen Symbole vorhanden. Die Rahmen der Aufrufliste sind falsch, wenn die Aufrufliste beschädigt ist, wenn Funktionen in der Assemblysprache geschrieben wurden oder wenn es sich um Betriebssystemrahmen ohne entsprechende Symbole in der Aufrufliste handelt.  
  
 Globale und statische Variablen werden immer richtig angezeigt. Dies trifft auch auf das Strukturlayout zu. Wenn ein Zeiger auf eine Struktur vorhanden und der Wert des Zeigers richtig ist, zeigt jede Membervariable der Struktur den richtigen Wert an.  
  
 Aufgrund dieser Einschränkungen müssen Debugoperationen, wenn überhaupt möglich, unter Verwendung einer nicht optimierten Version des Programms erfolgen. In der Debugkonfiguration eines Visual C++-Programms ist die Optimierung standardmäßig deaktiviert, während sie in der Releasekonfiguration aktiviert ist.  
  
 Ein Fehler ist jedoch nur in einer optimierten Programmversion erkennbar. In diesem Fall muss der optimierte Code gedebuggt werden.  
  
### <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>So aktivieren Sie die Optimierung in einer Debugbuildkonfiguration  
  
1.  Wählen Sie beim Erstellen eines neuen Projekts `Win32 Debug` als Ziel aus. Verwenden der `Win32``Debug` Ziel, bis das Programm vollständig debuggt wird, und Sie bereit sind, erstellen Sie eine `Win32 Release` Ziel. Das `Win32 Debug`-Ziel wird nicht vom Compiler optimiert.  
  
2.  Wählen Sie das Projekt im Projektmappen-Explorer aus.  
  
3.  Auf der **Ansicht** Menü klicken Sie auf **Eigenschaftenseiten**.  
  
4.  In der **Eigenschaftenseiten** Dialogfeld stellen Sie sicher, dass `Debug` ausgewählt ist, der **Konfiguration** Dropdown-Liste.  
  
5.  Wählen Sie in der Ordneransicht auf der linken Seite, die **C/C++-** Ordner.  
  
6.  Klicken Sie unter der **C++** Ordner wählen `Optimization`.  
  
7.  Suchen Sie die Option `Optimization` in der Eigenschaftenliste auf der rechten Seite. Die Einstellung daneben lautet wahrscheinlich `Disabled (` [/Od](/cpp/build/reference/od-disable-debug)`)`. Wählen Sie eine der anderen Optionen (`Minimum Size``(`[/O1](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Maximum Speed``(` [/O2](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Full Optimization``(` [/Ox](/cpp/build/reference/ox-full-optimization) `)`, oder `Custom`).  
  
8.  Wenn Sie für die `Custom` die Option `Optimization` auswählen, können Sie Optionen für alle weiteren Eigenschaften in der Eigenschaftenliste festlegen.  
  
9. Wählen Sie die Befehlszeilenknoten "Konfigurationseigenschaften" C/C++-Befehlszeile Knoten der Eigenschaftenseite des Projekts und hinzufügen `(` [/zo](/cpp/build/reference/zo-enhance-optimized-debugging) `)` auf die **Zusatzoptionen** Textfeld.  
  
    > [!WARNING]
    >  Für `/Zo` ist Visual Studio 2013 Update 3 oder höher erforderlich.  
    >   
    >  Hinzufügen von `/Zo` deaktiviert [bearbeiten und Fortfahren](../debugger/edit-and-continue-visual-csharp.md).  
  
 Verwenden Sie beim Debuggen von optimiertem Code die **Disassembly** Fenster, um festzustellen, welche Anweisungen tatsächlich erstellt und ausgeführt werden. Beim Festlegen von Haltepunkten sollten Sie beachten, dass der Haltepunkt zusammen mit einer Anweisung verschoben werden kann. Beachten Sie z. B. folgenden Code:  
  
```  
for (x=0; x<10; x++)  
```  
  
 Angenommen, Sie haben in dieser Zeile einen Haltepunkt festgelegt. Sie gehen möglicherweise davon aus, dass der Haltepunkt 10 Mal getroffen wird. Wenn der Code optimiert ist, wird er jedoch nur einmal getroffen. Dies liegt daran, dass die erste Anweisung den Wert von `x` auf 0 festlegt. Der Compiler erkennt, dass dies nur einmal durchgeführt werden muss und verschiebt es aus der Schleife. Gleichzeitig wird auch der Haltepunkt verschoben. Die Anweisungen zum Vergleichen und Heraufsetzen von `x` verbleiben innerhalb der Schleife. Beim Anzeigen der **Disassembly** Fenster die [Schritteinheit](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9) wird automatisch festgelegt, der Anweisung zur besseren Steuerung nützlich, ist Wenn Sie optimierten Code durchlaufen schrittweise.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)