---
title: Navigieren durch Code mit dem Debugger | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f79ece781db19f2483ef1dd6cb0a81ff7cf78e06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "88608939"
---
# <a name="navigating-through-code-with-the-debugger"></a>Navigieren im Code mit dem Debugger
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Machen Sie sich mit Befehlen und Verknüpfungen vertraut, um im Debugger im Code zu navigieren. Dadurch wird es schneller und einfacher, Probleme in Ihrer APP zu finden und zu beheben. Während Sie im Debugger im Code navigieren, können Sie [den Status Ihrer APP überprüfen](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables) oder mehr über den Ausführungs Fluss erfahren.  
  
## <a name="start-debugging"></a>Starten des Debugvorgangs  
 Häufig starten Sie eine Debugsitzung mithilfe **F5** von F5 **(**  /  **Debuggen Debuggen starten**). Mit diesem Befehl wird die APP mit dem angefügten Debugger gestartet.  
  
 Der grüne Pfeil startet auch den Debugger (identisch mit **F5**).  
  
 ![Dbg&#95;Grundlagen&#95;starten&#95;Debuggen](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 Ein paar weitere Möglichkeiten, wie Sie die APP mit dem angefügten Debugger starten können, sind **F11** (Einzel[Schritt in Code](#BKMK_Step_into__over__or_out_of_the_code)),  **F10** (Prozedur[Schritt](#BKMK_Step_over_Step_out)) oder **Ausführen bis Cursor**.  Weitere Informationen zu den Funktionen dieser Optionen finden Sie in den anderen Abschnitten in diesem Thema.  
  
 Beim Debuggen zeigt die gelbe Linie den Code an, der als nächstes ausgeführt wird.  
  
 ![Dbg&#95;Grundlagen&#95;Abbrechen&#95;Modus](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 Beim Debuggen können Sie zwischen Befehlen wie **F5**und **F11** wechseln und die anderen in diesem Thema beschriebenen Funktionen (z. b. Breakpoints) verwenden, um schnell zu dem Code zu gelangen, den Sie untersuchen möchten.  
  
 Die meisten Debuggerfunktionen, z. b. das Anzeigen von Variablen Werten im Fenster "lokal" oder das Auswerten von Ausdrücken in der Überwachungsfenster, sind nur verfügbar, wenn der Debugger angehalten wird (auch als *break-Modus*bezeichnet). Wenn der Debugger angehalten wird, wird der APP-Status angehalten, während Funktionen, Variablen und Objekte im Arbeitsspeicher verbleiben. Im Break-Modus können Sie die Positionen und Zustände der Elemente überprüfen, um nach Verstößen oder Fehlern zu suchen. Bei manchen Projekttypen können Sie im Unterbrechungsmodus auch Anpassungen der App vornehmen.  
  
## <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a> Schrittweises Ausführen von Code, Zeile für Zeile  
 Um beim Debuggen für jede Codezeile (jede-Anweisung) anzuhalten, verwenden Sie die Tastenkombination **F11** (oder **Debuggen**Sie  /  **Schritt** Weise im Menü).  
  
> [!TIP]
> Wenn Sie jede Codezeile ausführen, können Sie mit dem Mauszeiger auf Variablen zeigen, um deren Werte anzuzeigen, oder Sie können [mit den Fenstern](../debugger/autos-and-locals-windows.md) "lokal" und "über [Wachen](../debugger/autos-and-locals-windows.md) " die Werte ändern.  
  
 Im folgenden finden Sie einige Details zum Verhalten von Einzel **Schritten**:  
  
- Bei einem geschachtelten Funktionsaufruf führt **Einzelschritt** die am tiefsten geschachtelte Funktion in Einzelschritten aus. Wenn Sie **Einzelschritt** für einen Aufruf wie `Func1(Func2())`verwenden, führt der Debugger die Funktion `Func2`in Einzelschritten aus.  
  
- Der Debugger durchläuft tatsächlich durch Codeanweisungen anstatt durch physische Zeilen. Beispielsweise kann eine `if` -Klausel in eine Zeile geschrieben werden:  
  
  ```csharp  
  int x = 42;  
  string s = "Not answered";  
  if( int x == 42) s = "Answered!";  
  ```  
  
  ```vb  
  Dim x As Integer = 42  
  Dim s As String = "Not answered"  
  If x = 42 Then s = "Answered!"  
  ```  
  
   Wenn Sie einen Einzelschritt in diese Zeile ausführen, behandelt der Debugger die Bedingung als einen Schritt und das Ergebnis als anderen Schritt (in diesem Beispiel lautet die Bedingung "true").  
  
  Wenn Sie die-aufrufsliste beim schrittweisen Ausführen von Funktionen visuell nachverfolgen möchten, finden Sie weitere Informationen unter [map-Methoden in der](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)  
  
## <a name="step-through-code-skipping-functions"></a><a name="BKMK_Step_over_Step_out"></a> Schrittweises Durchlaufen von Code, Überspringen von Funktionen  
 Wenn Sie Code im Debugger ausführen, werden Sie häufig feststellen, dass Sie nicht sehen müssen, was in einer bestimmten Funktion geschieht (Sie sind nicht für Sie wichtig, oder Sie wissen, dass Sie funktioniert, wie gut getesteter Bibliotheks Code). Verwenden Sie diese Befehle, um den Code zu überspringen (die Funktionen werden natürlich weiterhin ausgeführt, aber der Debugger überspringt Sie).  
  
|Tastenkombination|Menübefehl|Beschreibung|  
|----------------------|------------------|-----------------|  
|**F10**|**Prozedurschritt**|Wenn die aktuelle Zeile einen Funktionsaufruf enthält, führt "Prozedur **Schritt** " den Code aus und hält die Ausführung in der ersten Codezeile an, nachdem die aufgerufene Funktion zurückgegeben hat.|  
|**UMSCHALT+F11**|**Rücksprung**|**Step out** setzt das Ausführen von Code fort und hält die Ausführung an, wenn die aktuelle Funktion zurückgibt (der Debugger überspringt die aktuelle Funktion).|  
  
> [!TIP]
> Wenn Sie den Einstiegspunkt in Ihrer APP suchen müssen, beginnen Sie mit **F10** oder **F11**. Diese Befehle sind häufig hilfreich, wenn Sie den App-Status überprüfen oder versuchen, mehr über den Ausführungs Fluss zu erfahren.  
  
## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Ausführen bis zu einer bestimmten Position oder Funktion  
 Diese Methoden sind häufig die bevorzugte Methode zum Debuggen von Code, wenn Sie genau wissen, welchen Code Sie überprüfen möchten, oder zumindest wissen, wo Sie mit dem Debuggen beginnen möchten.  
  
- **Festlegen von Haltepunkten im Code**  
  
     Um einen einfachen Haltepunkt im Code festzulegen, öffnen Sie die Quellcodedatei im Visual Studio-Editor. Legen Sie den Cursor in der Codezeile fest, in der die Ausführung angehalten werden soll, und klicken Sie dann mit der rechten Maustaste in das Code Fenster, um das Kontextmenü anzuzeigen, und wählen Sie halte **Punkt/Haltepunkt einfügen** aus (oder drücken Sie **F9**). Der Debugger unterbricht die Ausführung direkt vor der Ausführung der Zeile.  
  
     ![Festlegen eines Breakpoints](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Haltepunkte in Visual Studio bieten einen umfangreichen Satz von zusätzlichen Funktionen, wie z. B. bedingte Haltepunkte und Ablaufverfolgungspunkte. Siehe [Verwenden von Breakpoints](../debugger/using-breakpoints.md).  
  
- **Ausführen bis zur Cursorplatzierung**  
  
     Um den Code bis zur Cursorposition auszuführen, platzieren Sie den Cursor in einem Quellcodefenster auf eine ausführbare Codezeile. Klicken Sie im Kontextmenü des Editors (Klicken Sie mit der rechten Maustaste in den Editor), und wählen Sie **Ausführen bis Cursor**aus. Dies entspricht dem Festlegen eines temporären Breakpoints.  
  
- **Manuelles Unterbrechen im Code**  
  
     Um die Ausführung einer Anwendung in der nächsten verfügbaren Codezeile zu unterbrechen, wählen Sie **Debuggen**, **Alle unterbrechen** (Tastatur: **Ctrl+Alt+Break**).  
  
     Wenn Sie die Ausführung von Code ohne zugehörige Quell- oder Symboldateien (PDB-Dateien) unterbrechen, wird im Debugger die Seite **Die Quelldatei wurde nicht gefunden** oder **Symbol nicht gefunden** geöffnet, auf der Sie die entsprechenden Dateien suchen können. Weitere Informationen finden Sie unter [Angeben von Symbol-(PDB-) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Wenn Sie nicht auf die zugehörigen Hilfsdateien zugreifen können, können Sie dennoch die Assemblyanweisungen im Disassemblyfenster debuggen.  
  
- **Ausführen bis zu einer Funktion in der Aufrufliste**  
  
     Wählen Sie im Fenster " **Aufrufe** " (verfügbar beim Debuggen) die Funktion aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Ausführen bis Cursor**aus. Weitere Informationen zur visuellen Nachverfolgung der Aufrufliste finden Sie unter [Erstellen einer visuellen Zuordnung der Aufrufliste beim Debuggen (C#, Visual Basic, C++, JavaScript)](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
- **Ausführen bis zu einer Funktion anhand des Namens**  
  
     Sie können den Debugger anweisen, die Anwendung auszuführen, bis eine angegebene Funktion erreicht ist. Sie können die Funktion anhand ihres Namens angeben oder in der Aufrufliste auswählen.  
  
     Um eine Funktion anhand des Namens anzugeben, wählen Sie **Debuggen**, **Neuer Haltepunkt**, **Halten bei Funktion**aus, und geben Sie dann den Namen der Funktion und andere Identifikationsinformationen ein.  
  
     ![Dialogfeld "Neuer Haltepunkt"](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     Wenn die Funktion überladen ist oder sich in mehreren Namespaces befindet, können Sie die gewünschten Funktionen im Dialogfeld **Haltepunkte wählen** auswählen.  
  
     ![Dialogfeld "Breakpoints auswählen"](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a> Bewegen des Zeigers zum Ändern des Ausführungsablaufs  
 Während der Debugger angehalten wird, können Sie den Anweisungs Zeiger verschieben, um die nächste auszuführende Code Anweisung festzulegen. Die Position der nächsten auszuführenden Anweisung wird durch eine gelbe Pfeilspitze am Rand eines Quellcodefensters oder Disassemblierungsfensters markiert. Durch das Verschieben dieser Pfeilspitze können Sie einen Teil des Codes überspringen oder zu einer bereits ausgeführten Zeile zurückkehren. Dies ist zum Beispiel sinnvoll, um einen Codeabschnitt zu überspringen, von dem bereits bekannt ist, dass er einen Fehler enthält.  
  
 ![Example2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 Zum Festlegen der nächsten auszuführenden Anweisung verwenden Sie eines der folgenden Verfahren:  
  
- Ziehen Sie die gelbe Pfeilspitze in einem Quellcodefenster in derselben Quelldatei an die Position, an der Sie die nächste Anweisung festlegen möchten.  
  
- Legen Sie in einem Quell Code Fenster den Cursor in der Zeile fest, die Sie als nächstes ausführen möchten, klicken Sie mit der rechten Maustaste, und wählen Sie **nächste Anweisung festlegen**aus.  
  
- Legen Sie im Fenster Disassembly den Cursor für die Assemblyanweisung fest, die Sie als nächstes ausführen möchten, klicken Sie mit der rechten Maustaste auf einen, und wählen Sie **nächste Anweisung festlegen**aus.  
  
> [!CAUTION]
> Das Festlegen der nächsten Anweisung bewirkt, dass der Programmzähler direkt zur neuen Position springt. Seien Sie daher vorsichtig, wenn Sie diesen Befehl verwenden.  
> 
> - Anweisungen zwischen den alten und neuen Ausführungspunkten werden nicht ausgeführt.  
>   - Wenn Sie den Ausführungspunkt rückwärts verschieben, werden dazwischenliegende Anweisungen nicht rückgängig gemacht.  
>   - Wenn Sie die nächste Anweisung in eine andere Funktion oder in einen anderen Gültigkeitsbereich verschieben, wird i. d. R. die Aufrufliste beeinträchtigt, wodurch ein Laufzeitfehler oder eine Ausnahme ausgelöst wird. Wenn Sie versuchen, die nächste Anweisung in einen anderen Gültigkeitsbereich zu verschieben, wird ein Dialogfenster mit einer Warnung geöffnet, in dem Sie den Vorgang abbrechen können. In Visual Basic können Sie die nächste Anweisung nicht in einen anderen Bereich oder in eine andere Funktion verlegen.  
>   - In systemeigenem C++-Code kann das Festlegen der nächsten Anweisung bei aktivierter Laufzeitprüfung dazu führen, dass am Ende der Methode eine Ausnahme ausgelöst wird.  
>   - Wenn die Funktion "Bearbeiten und Fortfahren" aktiviert ist, schlägt das Ausführen der Option **Nächste Anweisung festlegen** fehl, wenn Sie Änderungen vorgenommen haben, die von "Bearbeiten und Fortfahren" nicht sofort neu zugeordnet werden können. Dies kann auftreten, wenn Sie z. B. Code in einem catch-Block bearbeitet haben. Dann wird die Fehlermeldung angezeigt, dass der Vorgang nicht unterstützt wird.  
> 
> [!NOTE]
> In verwaltetem Code können Sie die nächste Anweisung unter den folgenden Bedingungen nicht verschieben:  
> 
> - Die nächste Anweisung und die aktuelle Anweisung befinden sich in verschiedenen Methoden.  
>   - Das Debuggen wurde über Just-In-Time-Debuggen gestartet.  
>   - Die Aufrufliste wird gerade entladen.  
>   - Eine System.StackOverflowException oder eine System.Threading.ThreadAbortException wurden ausgelöst.  
  
 Während die Anwendung aktiv ausgeführt wird, ist es nicht möglich, die nächste Anweisung festzulegen. Zum Festlegen der nächsten Anweisung muss sich der Debugger im Unterbrechungsmodus befinden.  
  
## <a name="step-into-non-user-code"></a>Einzelschritt in Nichtbenutzer Code  
 Standardmäßig versucht der Debugger beim Debuggen nur den App-Code anzuzeigen, der durch eine Debuggereinstellung namens " *nur eigenen Code*" bestimmt wird. (Informationen hierzu finden Sie unter [nur eigenen Code](../debugger/just-my-code.md) , wie dies für verschiedene Projekttypen und Sprachen funktioniert und wie Sie das Verhalten anpassen können.) Manchmal können Sie jedoch beim Debuggen auch Frameworkcode, Bibliotheks Code von Drittanbietern oder Aufrufe des Betriebssystems (Systemaufrufe) betrachten.  
  
 Sie können nur eigenen Code **deaktivieren, indem Sie zu**Extras  /  **Optionen**  /  **Debuggen** wechseln und das Kontrollkästchen **nur eigenen Code aktivieren** deaktivieren.  
  
 Wenn nur eigenen Code deaktiviert ist, kann der Debugger den Nichtbenutzer Code schrittweise ausführen, und Nichtbenutzer Code wird in den Debuggerfenstern angezeigt.  
  
> [!NOTE]
> Nur mein Code wird in Geräteprojekten nicht unterstützt.  
  
 **Schrittweise Ausführung von Systemaufrufen**  
  
 Wenn Sie Debugsymbole für den Systemcode geladen haben und nur eigenen Code nicht aktiviert ist, können Sie wie bei jedem anderen-Aufrufvorgang einen System Aufrufvorgang ausführen.  
  
 Informationen zum Zugriff auf Microsoft-Symbol Dateien finden Sie unter [Verwenden von Symbol Servern zum Suchen von Symbol Dateien, die sich nicht auf dem lokalen Computer befinden](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) im Thema [Angeben von Symbol Dateien (PDB) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) .  
  
 So laden Sie Symbole für eine bestimmte Systemkomponente während des Debuggings:  
  
1. Öffnen Sie das Fenster "Module" (Tastatur: **Ctrl+Alt+U**).  
  
2. Wählen Sie das Modul aus, für das Sie Symbole laden möchten.  
  
     Sie können in der Spalte **Symbolstatus** feststellen, für welche Module Symbole geladen sind.  
  
3. Wählen Sie im Kontextmenü die Option **Symbole laden** aus.  
  
## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Schrittweise Ausführung von Eigenschaften und Operatoren in verwaltetem Code  
 Standardmäßig überspringt der Debugger die Eigenschaften und Operatoren in verwaltetem Code. In den meisten Fällen sorgt dies für einen besseren Debugvorgang. Klicken Sie auf **Debuggen** / **Optionen**, um das schrittweise Ausführen von Eigenschaften oder Operatoren zu aktivieren. Deaktivieren Sie auf der Seite **Debuggen**auf  /  der Seite**Allgemein** das Kontrollkästchen **Eigenschaften und Operatoren überspringen (nur verwaltet)** .
