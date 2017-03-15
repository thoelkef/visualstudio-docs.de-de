---
title: "Gewusst wie: Debuggen von optimiertem Code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Haltepunkte, In optimiertem Code"
  - "Debugbuilds, Optimieren"
  - "Debuggen [C++], Optimierter Code"
  - "Optimierung, Debugbuilds"
  - "Optimierter Code, Debuggen"
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
caps.latest.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 25
---
# Gewusst wie: Debuggen von optimiertem Code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!NOTE]
>  Die \(in Visual Studio Update 3 eingeführte\)  [\/Zo \(erweitertes optimiertes Debugging\)](/visual-cpp/build/reference/zo-enhance-optimized-debugging)\-Compileroption generiert umfangreichere Debuginformationen für optimierten Code \(d. h. Projekte, die nicht mit der **\/Od**\-Compileroption erstellt wurden.  Siehe [\/O\-Optionen \(Code optimieren\)](/visual-cpp/build/reference/o-options-optimize-code)\).  Dazu gehört verbesserte Unterstützung zum Debuggen von lokalen Variablen und Inlinefunktionen.  
>   
>  [Bearbeiten und Fortfahren](../debugger/edit-and-continue-visual-csharp.md) ist deaktiviert, wenn die **\/Zo**\-Compileroption verwendet wird.  
  
 Wenn der Compiler Code optimiert, werden die Anweisungen neu positioniert und organisiert.  Hierdurch wird die Effizienz des kompilierten Codes erhöht.  Aufgrund dieser Neuanordnung ist der Debugger nicht immer in der Lage, den Quellcode, der einer bestimmten Gruppe von Anweisungen entspricht, zu erkennen.  
  
 Durch die Optimierung können folgende Bereiche beeinflusst werden:  
  
-   Lokale Variablen, die durch den Optimierer entfernt oder an Speicherorte verschoben werden können, die vom Debugger nicht erkannt werden.  
  
-   Positionen in einer Funktion, die geändert werden, wenn Codeblöcke durch den Optimierer zusammenführt werden.  
  
-   Funktionsnamen für Rahmen der Aufrufliste, die möglicherweise falsch sind, wenn der Optimierer zwei Funktionen zusammenführt.  
  
 Die in der Aufrufliste angezeigten Rahmen sind fast immer korrekt, vorausgesetzt, es sind für alle Rahmen Symbole vorhanden.  Die Rahmen der Aufrufliste sind falsch, wenn die Aufrufliste beschädigt ist, wenn Funktionen in der Assemblysprache geschrieben wurden oder wenn es sich um Betriebssystemrahmen ohne entsprechende Symbole in der Aufrufliste handelt.  
  
 Globale und statische Variablen werden immer richtig angezeigt.  Dies trifft auch auf das Strukturlayout zu.  Wenn ein Zeiger auf eine Struktur vorhanden und der Wert des Zeigers richtig ist, zeigt jede Membervariable der Struktur den richtigen Wert an.  
  
 Aufgrund dieser Einschränkungen müssen Debugoperationen, wenn überhaupt möglich, unter Verwendung einer nicht optimierten Version des Programms erfolgen.  In der Debugkonfiguration eines Visual C\+\+\-Programms ist die Optimierung standardmäßig deaktiviert, während sie in der Releasekonfiguration aktiviert ist.  
  
 Ein Fehler ist jedoch nur in einer optimierten Programmversion erkennbar.  In diesem Fall muss der optimierte Code gedebuggt werden.  
  
### So aktivieren Sie die Optimierung in einer Debugbuildkonfiguration  
  
1.  Wählen Sie beim Erstellen eines neuen Projekts `Win32 Debug` als Ziel aus.  Verwenden Sie das `Win32``Debug`\-Ziel, bis das Programm vollständig debuggt und für die Erstellung eines `Win32 Release`\-Ziels bereit ist.  Das `Win32 Debug`\-Ziel wird nicht vom Compiler optimiert.  
  
2.  Wählen Sie das Projekt im Projektmappen\-Explorer aus.  
  
3.  Klicken Sie im Menü **Ansicht** auf die Option **Eigenschaftenseiten**.  
  
4.  Stellen Sie im Dialogfeld **Eigenschaftenseiten** sicher, dass im Dropdown\-Listenfeld **Konfiguration** die Option `Debug` ausgewählt ist.  
  
5.  Wählen Sie in der Ordneransicht auf der linken Seite den Ordner **C\/C\+\+** aus.  
  
6.  Wählen Sie im Ordner **C\+\+** die Option `Optimization` aus.  
  
7.  Suchen Sie die Option `Optimization` in der Eigenschaftenliste auf der rechten Seite.  Die Einstellung links davon lautet wahrscheinlich `Disabled (`[\/Od](/visual-cpp/build/reference/od-disable-debug)`)`.  Wählen Sie eine der anderen Optionen \(`Minimum Size``(`[\/O1](/visual-cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Maximum Speed``(`[\/O2](/visual-cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Full Optimization``(`[\/Ox](/visual-cpp/build/reference/ox-full-optimization)`)` oder `Custom`\) aus.  
  
8.  Wenn Sie für die `Custom` die Option `Optimization` auswählen, können Sie Optionen für alle weiteren Eigenschaften in der Eigenschaftenliste festlegen.  
  
9. Wählen Sie den C\/C\+\+\-Befehlszeilenknoten "Konfigurationseigenschaften" der Eigenschaftenseite des Projekts aus, und fügen Sie dem Textfeld **Zusätzliche Optionen** `)`[\/Zo](/visual-cpp/build/reference/zo-enhance-optimized-debugging)`(` hinzu.  
  
    > [!WARNING]
    >  Für `/Zo` ist Visual Studio 2013 Update 3 oder höher erforderlich.  
    >   
    >  Das Hinzufügen von `/Zo` deaktiviert [Bearbeiten und Fortfahren](../debugger/edit-and-continue-visual-csharp.md).  
  
 Ermitteln Sie beim Debuggen von optimiertem Code im Fenster **Disassembly**, welche Anweisungen tatsächlich generiert und ausgeführt werden.  Beim Festlegen von Haltepunkten sollten Sie beachten, dass der Haltepunkt zusammen mit einer Anweisung verschoben werden kann.  Beachten Sie z. B. folgenden Code:  
  
```  
for (x=0; x<10; x++)  
```  
  
 Angenommen, Sie haben in dieser Zeile einen Haltepunkt festgelegt.  Sie gehen möglicherweise davon aus, dass der Haltepunkt 10 Mal getroffen wird. Wenn der Code optimiert ist, wird er jedoch nur einmal getroffen.  Dies liegt daran, dass die erste Anweisung den Wert von `x` auf 0 festlegt.  Der Compiler erkennt, dass dies nur einmal durchgeführt werden muss und verschiebt es aus der Schleife.  Gleichzeitig wird auch der Haltepunkt verschoben.  Die Anweisungen zum Vergleichen und Heraufsetzen von `x` verbleiben innerhalb der Schleife.  Wenn Sie das Fenster **Disassembly** anzeigen, wird die [Schritteinheit](http://msdn.microsoft.com/de-de/8791dac9-64d1-4bb9-b59e-8d59af1833f9) zur besseren Steuerung automatisch auf "Befehl" festgelegt. Dies ist bei der schrittweisen Ausführung von optimiertem Code von Vorteil.  
  
## Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debuggen von systemeigenem Code](../debugger/debugging-native-code.md)