---
title: "Fenster „Auto“ und „Lokal“ | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
f1_keywords: 
  - "vs.debug.autos"
  - "vs.debug.locals"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "Debugger, Variablenfenster"
  - "Debuggen [Visual Studio], Variablenfenster"
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fenster „Auto“ und „Lokal“
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Fenster **Auto** \(beim Debuggen, **STRG \+ ALT \+ V, A** oder **Debuggen \/ Fenster \/ Auto**\) und das Fenster **Lokal** \(beim Debuggen, **STRG \+ ALT \+ V, L**, oder **Debuggen \/ Fenster \/ Lokal**\) sind hilfreich, wenn Sie beim Debuggen Variablenwerte sehen möchten. Im Fenster **Lokal** werden die Variablen angezeigt, die im lokalen Gültigkeitsbereich definiert sind, der in der Regel der Funktion oder Methode entspricht, die derzeit ausgeführt wird. Im Fenster **Auto** werden Variablen angezeigt, die in der Nähe der aktuellen Zeile \(die Stelle, an der der Debugger angehalten wurde\) verwendet werden. Welche Variablen genau angezeigt werden, unterscheidet sich in verschiedenen Sprachen. Weitere Informationen finden Sie unter „Welche Variablen werden im Fenster „Auto“ angezeigt?“ weiter unten.  
  
 Wenn Sie weitere Informationen zu den Grundlagen des Debuggens benötigen, lesen Sie [Erste Schritte mit dem Debugger](../debugger/getting-started-with-the-debugger.md).  
  
## Betrachten von Objekten in den Fenstern „Auto“ und „Lokal“  
 Arrays und Objekte werden in den Fenstern „Auto“ und „Lokal“ als Struktursteuerelemente angezeigt. Klicken Sie auf den Pfeil links neben dem Variablennamen, damit die Ansicht erweitert wird, sodass m die Felder und Eigenschaften angezeigt werden. Dies ist ein Beispiel für ein [FileStream](../Topic/FileStream%20Class.md)\-Objekt im Fenster **Lokal**:  
  
 ![Locals&#45;FileStream](../debugger/media/locals-filestream.png "Locals\-FileStream")  
  
## Welche Variablen werden im Fenster „Auto“ angezeigt?  
 Sie können das Fenster **Auto** für C\#\-, Visual Basic\- und C\+\+\-Code verwenden. Das Fenster **Auto** unterstützt weder JavaScript noch F\#\-.  
  
 In C\# und Visual Basic wird im Fenster **Auto** jede Variable angezeigt, die in der aktuellen oder vorherigen Zeile verwendet wird. Angenommen, Sie deklarieren vier Variablen und legen diese wie folgt fest:  
  
```c#  
public static void Main() { int a, b, c, d; a = 1; b = 2; c = 3; d = 4; }  
```  
  
 Wenn Sie einen Haltepunkt in der Zeile `c = 3` festgelegt haben und den Debugger ausführen, sieht das Fenster **Auto** wie folgt aus, wenn die Ausführung angehalten wird:  
  
 ![Autos&#45;CSharp](../debugger/media/autos-csharp.png "Autos\-CSharp")  
  
 `c` hat den Wert 0, weil die Zeile `c = 3` noch nicht ausgeführt wurde.  
  
 In C\+\+ werden im Fenster **Auto** die Variablen angezeigt, die in den letzten drei Zeilen vor der aktuellen Zeile \(die Zeile, in der die Ausführung angehalten wurde\) verwendet werden. Angenommen, Sie deklarieren sechs Variablen:  
  
```cpp  
void main() { int a, b, c, d, e, f; a = 1; b = 2; c = 3; d = 4; e = 5; f = 6; }  
```  
  
 Wenn Sie einen Haltepunkt in der Zeile `e = 5;` festgelegt haben und den Debugger ausführen, sieht das Fenster **Auto** wie folgt aus, wenn die Ausführung angehalten wird:  
  
 ![Autos&#45;Cplus](../debugger/media/autos-cplus.png "Autos\-Cplus")  
  
 Sie sehen, dass die Variable „e“ nicht initialisiert ist. Dies liegt daran, dass der Code in der Zeile  `e = 5;`  noch nicht ausgeführt wurde.  
  
 In bestimmten Fällen können Sie auch die Rückgabewerte von Funktionen und Methoden sehen. Weitere Informationen finden im folgenden Abschnitt [Anzeigen von Rückgabewerten von Methodenaufrufen](#bkmk_returnValue).  
  
##  <a name="bkmk_returnValue"></a> Anzeigen von Rückgabewerten von Methodenaufrufen  
 In .NET\- und C\+\+\-Code können Sie Rückgabewerte auswerten, wenn Sie einen Methodenaufruf als Prozedurschritt oder bis zum Rücksprung ausführen. Diese Funktion ist nützlich, wenn das Ergebnis eines Methodenaufrufs nicht in einer lokalen Variablen gespeichert wird, etwa wenn eine Methode als Parameter oder Rückgabewert einer anderen Methode verwendet wird.  
  
 Im folgenden C\#\-Code werden die Rückgabewerte von zwei Funktionen hinzugefügt:  
  
```c#  
static void Main(string[] args) { int a, b, c, d; a = 1; b = 2; c = 3; d = 4; int x = sumVars(a, b) + subtractVars(c, d); } private static int sumVars(int i, int j) { return i + j; } private static int subtractVars(int i, int j) { return j - i; }  
  
```  
  
 Legen Sie einen Haltepunkt in der Zeile int `x = sumVars(a, b) + subtractVars(c, d);`  fest.  
  
 Starten Sie das Debuggen, und drücken Sie **F10 \(Prozedurschritt\)**, wenn die Ausführung am ersten Haltepunkt angehalten wird. Daraufhin sollte Folgendes im Fenster **Auto** zu sehen sein:  
  
 ![AutosReturnValueCSharp2](../debugger/media/autosreturnvaluecsharp2.png "AutosReturnValueCSharp2")  
  
## Warum sind Variablenwerte im Fenster „Lokal“ oder „Auto“ manchmal rot?  
 Gelegentlich stellen Sie fest, dass der Wert einer Variablen im Fenster **Lokal** oder **Auto** rot angezeigt wird. Dies ist ein Variablenwert, der seit der letzten Auswertung geändert wurde. Die Änderung kann aus einer vorherigen Debugsitzung stammen oder daran liegen, dass der Wert im Fenster geändert wurde.  
  
## Ändern des numerischen Formats eines Variablenfensters  
 Das standardmäßige numerische Format ist das Dezimalformat, Sie können dies aber in das Hexadezimalformat ändern. Klicken Sie mit der rechten Maustaste im Fenster **Lokal** oder **Auto**, und wählen Sie **Hexadezimale Anzeige** aus. Die Änderung wirkt sich auf alle Debuggerfenster aus.  
  
## Bearbeiten eines Werts in einem Variablenfenster  
 Sie können die Werte der meisten Variablen bearbeiten, die in den Fenstern **Auto**, **Lokal**, **Überwachen** und **Schnellüberwachung** angezeigt werden. Informationen zu den Fenstern **Überwachen** und **Schnellüberwachung** finden Sie unter [Fenster "Überwachen" und "Schnellüberwachung"](../debugger/watch-and-quickwatch-windows.md). Doppelklicken Sie einfach auf den Wert, den Sie ändern möchten, und fügen Sie den neuen Wert hinzu.  
  
 Sie können Sie einen Ausdruck für einen Wert eingeben, etwa `a + b`. Der Debugger akzeptiert im die meisten gültigen Sprachausdrücke.  
  
 In nativem C\+\+\-Code müssen Sie möglicherweise den Kontext eines Variablennamens qualifizieren. Weitere Informationen finden Sie unter [Kontextoperator \(C\+\+\)](../debugger/context-operator-cpp.md).  
  
 Allerdings sollten Sie Vorsicht walten lassen, wenn Sie Werte ändern. Mögliche Probleme:  
  
-   Die Auswertung bestimmter Ausdrücke kann zur Änderung des Werts einer Variablen führen oder sich auf den Programmzustand auswirken. Wird beispielsweise `var1 = ++var2` ausgewertet, wird der Wert von `var1` und `var2` geändert.  
  
     Ausdrücke, die eine Änderung von Daten bewirken, haben [Nebeneffekte](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)), die zu unerwarteten Ergebnissen führen können, wenn Sie sich der Effekte nicht bewusst sind. Vergewissern Sie sich, dass Sie die Folgen einer solchen Änderung kennen, bevor Sie sie vornehmen.  
  
-   Das Bearbeiten von Gleitkommawerten kann aufgrund der Dezimal\-zu\-Binär\-Konvertierung von Nachkommastellen zu geringfügigen Ungenauigkeiten führen. Auch eine scheinbar harmlose Bearbeitung kann Änderungen in einigen der unwichtigsten Bits einer Gleitkommavariable bewirken.  
  
## Symbolleiste „Debugspeicherort“  
 Sie können die Symbolleiste **Debugspeicherort** verwenden, um die gewünschte Funktion, den gewünschten Thread oder den gewünschten Prozess auszuwählen. Legen Sie einen Haltepunkt fest, und starten Sie das Debuggen. \(Wenn diese Symbolleiste nicht angezeigt wird, können Sie sie aktivieren, indem Sie auf einen leeren Bereich der Symbolleiste klicken. Sie sollten die Liste der Symbolleisten sehen. Wählen Sie **Debugspeicherort** aus.\) Wenn der Haltepunkt erreicht ist, wird die Ausführung angehalten, und Sie können die Symbolleiste „Debugspeicherort“ sehen, die die unterste Zeile in der folgenden Grafik ist:  
  
 ![DebugLocationToolbar](~/docs/debugger/media/debuglocationtoolbar.png "DebugLocationToolbar")  
  
 Sie können den Kontext auch zu anderen Funktionsaufrufen, Threads oder Prozessen wechseln, indem Sie im Fenster **Aufrufliste**, **Threads** oder **Prozesse** auf das Element doppelklicken.  
  
## Siehe auch  
 [Debuggerfenster](../debugger/debugger-windows.md)