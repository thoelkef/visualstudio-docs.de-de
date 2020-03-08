---
title: Navigieren durch den Code mit dem Debugger | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/12/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6dfffdf0c12ea2a8f14769f26bb40a3943579248
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409314"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Navigieren durch Code mit dem Visual Studio-Debugger

Mit dem Visual Studio-Debugger können Sie durch den Code navigieren, um den Zustand einer APP zu überprüfen und den Ausführungs Fluss anzuzeigen. Sie können Tastenkombinationen, Debug-Befehle, Breakpoints und andere Features verwenden, um schnell zu dem Code zu gelangen, den Sie untersuchen möchten. Vertrautheit mit Debugger-Navigations Befehlen und-Verknüpfungen ermöglicht es, App-Probleme schneller und leichter zu finden und zu beheben.  Wenn Sie den Code zum ersten Mal debuggen möchten, sollten Sie vor dem Durcharbeiten dieses Artikels das [Debuggen für absolute Einsteiger](../debugger/debugging-absolute-beginners.md) und [Debuggingtechniken und-Tools](../debugger/write-better-code-with-visual-studio.md) lesen.

## <a name="get-into-break-mode"></a>Wechseln Sie in den "Break-Modus".

Im *unterschreibmodus*wird die Ausführung der APP angehalten, während Funktionen, Variablen und Objekte im Arbeitsspeicher verbleiben. Sobald sich der Debugger im Break-Modus befindet, können Sie durch den Code navigieren. Die gängigsten Möglichkeiten, sich schnell in den Unterbrechung zu bewegen, sind folgende:

- Beginnen Sie den Code schrittweise, indem Sie **F10** oder **F11**drücken. Auf diese Weise können Sie schnell den Einstiegspunkt ihrer App finden. Sie können dann mit dem Drücken von Schritt Befehlen fortfahren, um den Code zu navigieren.

- [Führen Sie an einem bestimmten Speicherort oder einer bestimmten Funktion](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All)aus, indem Sie beispielsweise [einen Haltepunkt festlegen](using-breakpoints.md) und die app starten.

   Beispielsweise können Sie im Code-Editor in Visual Studio den Befehl **Ausführen bis Cursor** verwenden, um die APP, den Debugger anzufügen und in den Break-Modus zu starten, und **F11** , um den Code zu navigieren.

   ![Ausführen bis Cursor und Ausführen von Code in Einzelschritten](../debugger/media/navigate-code-code-stepping.gif "Ausführen bis Cursor und Ausführen von Code in Einzelschritten")

Im Break-Modus können Sie eine Vielzahl von Befehlen verwenden, um durch den Code zu navigieren. Im Break-Modus können Sie die Werte von Variablen überprüfen, um nach Verstößen oder Fehlern zu suchen. Bei einigen Projekttypen können Sie auch Anpassungen an der APP vornehmen, während Sie sich im Break-Modus befinden.

Die meisten Debuggerfenster, wie z. b. die **Module** und die **Überwachungs** Fenster, sind nur verfügbar, wenn der Debugger an Ihre APP angefügt ist. Einige Debuggerfunktionen, z. b. das Anzeigen von Variablen Werten **im Fenster "** lokal" oder das Auswerten von Ausdrücken im Fenster "über **Wachen** ", sind nur verfügbar, wenn der Debugger angehalten ist (d. h. im Break-Modus).

> [!NOTE]
> Wenn Sie in Code unterbrechen, der keine Quell-oder Symbol Dateien (*PDB*-Dateien) geladen hat, zeigt der Debugger die Seite **Quelldateien nicht gefunden** oder Symbol **nicht gefunden** an, mit der Sie die Dateien suchen und laden können. Weitere Informationen finden Sie unter [Angeben von Symbol- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Wenn Sie die Symbol-oder Quelldateien nicht laden können, können Sie dennoch die Assemblyanweisungen im Disassemblyfenster Debuggen.

## <a name="step-through-code"></a>Schritt-für-Schritt-Ausführung des Codes

Mithilfe der Befehle zum Debuggerschritt untersuchen Sie den App-Status, oder erfahren Sie mehr über den Ausführungs Fluss.

### <a name="BKMK_Step_into__over__or_out_of_the_code"></a>Schrittweises Ausführen von Code in Einzelschritten

Um beim Debuggen für jede Anweisung anzuhalten, verwenden Sie **Debug** > Einzel **Schritt**, oder drücken Sie **F11**.

Der Debugger schrittweise durch Code Anweisungen, nicht durch physische Zeilen. Beispielsweise kann eine `if`-Klausel in eine Zeile geschrieben werden:

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

Wenn Sie jedoch in diese Zeile eintreten, behandelt der Debugger die Bedingung als einen Schritt und die Folge als eine andere. Im vorherigen Beispiel lautet die Bedingung "true".

Bei einem geschachtelten Funktionsaufruf führt **Einzelschritt** die am tiefsten geschachtelte Funktion in Einzelschritten aus. Wenn Sie z. b. Einzel **Schritt** für einen-Befehl wie `Func1(Func2())`verwenden, führt der Debugger die Funktion `Func2`aus.

>[!TIP]
>Wenn Sie jede Codezeile ausführen, können Sie mit dem Mauszeiger auf Variablen zeigen, um deren Werte anzuzeigen, oder Sie können mit den Fenstern "lokal [" und "](autos-and-locals-windows.md) über [Wachen](watch-and-quickwatch-windows.md) " die Werte ändern. Sie können die- [aufrufsstapel](how-to-use-the-call-stack-window.md) auch während der Schritt-für-Schritt-Funktion in (Informationen zu Visual Studio Enterprise finden Sie unter [map-Methoden in der aufrufsstapel beim Debuggen](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)).

### <a name="BKMK_Step_over_Step_out"></a>Schrittweises Durchlaufen von Code und überspringen einiger Funktionen

Beim Debuggen ist es möglicherweise nicht wichtig, dass eine Funktion funktioniert, oder Sie wissen, wie gut getesteter Bibliotheks Code funktioniert. Sie können die folgenden Befehle verwenden, um Code zu überspringen, während die Code überschrittes Die Funktionen werden weiterhin ausgeführt, aber der Debugger überspringt Sie.

|Tastatur Befehl|Menübefehle für das Debuggen|BESCHREIBUNG|
|----------------------|------------------|-----------------|
|**F10**|**Überspringen**|Wenn die aktuelle Zeile einen Funktionsaufruf enthält, führt "Prozedur **Schritt** " den Code aus und hält dann die Ausführung in der ersten Codezeile an, nachdem die aufgerufene Funktion zurückgegeben hat.|
|**UMSCHALT**+**F11**|**Rücksprung**|**Step out** setzt das Ausführen von Code fort und hält die Ausführung an, wenn die aktuelle Funktion zurückgibt. Der Debugger überspringt die aktuelle Funktion.|

## <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>An einem bestimmten Speicherort oder einer bestimmten Funktion ausführen

Wenn Sie genau wissen, welchen Code Sie überprüfen möchten, können Sie es vorziehen, direkt an einem bestimmten Speicherort oder einer bestimmten Funktion auszuführen, oder Sie wissen, wo Sie mit dem Debuggen beginnen möchten.

### <a name="run-to-a-breakpoint-in-code"></a>Ausführen bis zu einem Breakpoint im Code

Um einen einfachen Haltepunkt im Code festzulegen, klicken Sie auf den äußersten linken Rand neben der Codezeile, in der Sie die Ausführung unterbrechen möchten. Sie können auch die Zeile auswählen und **F9**drücken, **Debuggen** > halte **Punkt umschalten**auswählen oder mit der rechten Maustaste klicken und halte **Punkt** > halte **Punkt einfügen**auswählen. Der Haltepunkt wird als roter Punkt im linken Rand neben der Codezeile angezeigt. Der Debugger hält die Ausführung an, kurz bevor die Zeile ausgeführt wird.

![Festlegen eines Breakpoints](../debugger/media/dbg_basics_setbreakpoint.png "Haltepunkt festlegen")

Haltepunkte in Visual Studio bieten einen umfangreichen Satz von zusätzlichen Funktionen, wie z. B. bedingte Haltepunkte und Ablaufverfolgungspunkte. Weitere Informationen finden [Sie unter Verwenden von Breakpoints](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>Ausführen bis zu einem Funktions Breakpoint

Sie können den Debugger so anweisen, dass er ausgeführt wird, bis er eine angegebene Funktion erreicht. Sie können die Funktion anhand ihres Namens angeben oder in der Aufrufliste auswählen.

**So geben Sie einen Funktions Haltepunkt anhand des Namens an**

1. Wählen Sie **Debuggen** > **Neuer Haltepunkt** > **Funktions Breakpoint** aus.

1. Geben Sie im Dialogfeld **neuer Funktions Breakpunkt** den Namen der Funktion ein, und wählen Sie die zugehörige Sprache aus.

   ![Dialogfeld "neuer Funktions Haltepunkt"](../debugger/media/dbg_execution_newbreakpoint.png "Neuer Funktions Breakpoint")

1. Klicken Sie auf **OK**.

Wenn die Funktion überladen ist oder sich in mehreren Namespaces befindet, können Sie im Fenster **Breakpoints** den gewünschten Wert auswählen.

![Überladene Funktions Breakpoints](../debugger/media/dbg_execution_overloadedbreakpoints.png "Überladene Funktions Breakpoints")

**So wählen Sie einen Funktions Haltepunkt aus der aufrufsstapel aus**

1. Öffnen Sie beim Debuggen das Fenster " **aufrufsstapel** ", indem Sie auf **Debuggen** > **Windows** > 

1. Klicken Sie im Fenster " **CallStack** " mit der rechten Maustaste auf eine Funktion, und wählen Sie **Ausführen bis Cursor**aus, oder drücken Sie **STRG**+**F10**.

Informationen zur visuellen Ablauf Verfolgung der-aufrufsliste finden Sie unter [map Methods in the callstack while Debugging](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Ausführen bis zu einer Cursorposition

Zum Ausführen bis zur Cursorposition wählen Sie im Quellcode oder im **Fenster "Fenster" die Zeile** aus, bei der Sie unterbrechen möchten, klicken Sie mit der rechten Maustaste, und wählen Sie **Ausführen bis Cursor**aus, oder drücken Sie **STRG**+**F10**. **Die Auswahl von "Ausführen bis Cursor** " ähnelt dem Festlegen eines temporären halte Punkts.

### <a name="run-to-click"></a>Ausführung bis Klick

Während Sie im Debugger angehalten wurde, können Sie auf eine-Anweisung im Quellcode oder im Fenster **Disassembly** zeigen und dann auf das Symbol **Ausführung bis zu** diesem grünen Pfeil ausführen klicken. Wenn **Sie auf Ausführen klicken,** entfällt die Notwendigkeit, einen temporären Haltepunkt festzulegen.

![Run to Click](../debugger/media/dbg-run-to-click.png "Ausführung bis Klick") (Ausführen bis Klick)

> [!NOTE]
> Das **Ausführen bis Klick** ist ab [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]verfügbar.

### <a name="manually-break-into-code"></a>Manuelles Unterbrechen im Code

Wenn Sie in der nächsten verfügbaren Codezeile in einer ausgelaufenden APP **unterbrechen möchten**, wählen Sie **Debuggen** aus, > alle unter **brechen**, oder drücken Sie **STRG**+**alt** ,+

## <a name="BKMK_Set_the_next_statement_to_execute"></a>Bewegen Sie den Zeiger, um den Ausführungs Fluss zu ändern.

Während der Debugger angehalten wird, kennzeichnet eine gelbe Pfeilspitze am Rand des Quellcodes oder Disassemblyfensters den Speicherort der nächsten auszuführenden Anweisung. Sie können die nächste auszuführende Anweisung ändern, indem Sie diese Pfeilspitze verschieben. Sie können einen Teil des Codes überspringen oder zu einer vorherigen Zeile zurückkehren. Das Verschieben des Zeigers ist hilfreich für Situationen wie das Überspringen eines Code Abschnitts, der einen bekannten Fehler enthält.

 ![Zeiger verschieben](../debugger/media/dbg_basics_example3.gif "Zeiger verschieben")

Um die nächste auszuführende Anweisung zu ändern, muss sich der Debugger im unterbrechen Modus befinden. Ziehen Sie im Quellcode oder Disassemblierungsfenster die gelbe Pfeilspitze in eine andere Zeile, oder klicken Sie mit der rechten Maustaste auf die Zeile, die Sie als nächstes ausführen möchten, und wählen Sie **nächste Anweisung festlegen**aus.

Der Programm-Counter springt direkt zum neuen Speicherort, und die Anweisungen zwischen den alten und neuen Ausführungs Punkten werden nicht ausgeführt. Wenn Sie jedoch den Ausführungs Punkt rückwärts verschieben, werden die dazwischenliegenden Anweisungen nicht rückgängig gemacht.

>[!CAUTION]
>- Wenn Sie die nächste Anweisung in eine andere Funktion oder in einen anderen Gültigkeitsbereich verschieben, wird i. d. R. die Aufrufliste beeinträchtigt, wodurch ein Laufzeitfehler oder eine Ausnahme ausgelöst wird. Wenn Sie versuchen, die nächste Anweisung in einen anderen Gültigkeitsbereich zu verschieben, wird ein Dialogfenster mit einer Warnung geöffnet, in dem Sie den Vorgang abbrechen können.
>- In Visual Basic können Sie die nächste Anweisung nicht in einen anderen Bereich oder in eine andere Funktion verlegen.
>- In systemeigenem C++-Code kann das Festlegen der nächsten Anweisung bei aktivierter Laufzeitprüfung dazu führen, dass am Ende der Methode eine Ausnahme ausgelöst wird.
>- Wenn die Funktion "Bearbeiten und Fortfahren" aktiviert ist, schlägt das Ausführen der Option **Nächste Anweisung festlegen** fehl, wenn Sie Änderungen vorgenommen haben, die von "Bearbeiten und Fortfahren" nicht sofort neu zugeordnet werden können. Dies kann auftreten, wenn Sie z. B. Code in einem catch-Block bearbeitet haben. In diesem Fall werden Sie in einer Fehlermeldung darauf hingewiesen, dass der Vorgang nicht unterstützt wird.
>- In verwaltetem Code können Sie die nächste Anweisung nicht verschieben, wenn Folgendes der folgenden ist:
>   - Die nächste Anweisung und die aktuelle Anweisung befinden sich in verschiedenen Methoden.
>   - Das Debuggen wurde durch Just-in-Time-Debugging gestartet.
>   - Eine aufrureleasestapel Entladung wird ausgeführt.
>   - Eine System.StackOverflowException oder eine System.Threading.ThreadAbortException wurden ausgelöst.

## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Debuggen von Nichtbenutzer Code

Standardmäßig versucht der Debugger, nur Ihren app-Code zu debuggen, indem er eine Einstellung namens " *nur eigenen Code*" aktiviert. Weitere Informationen über die Funktionsweise dieses Features für verschiedene Projekttypen und Sprachen und deren Anpassung finden Sie unter [nur eigenen Code](../debugger/just-my-code.md).

Zum Überprüfen von Frameworkcode, Bibliotheks Code von Drittanbietern oder Systemaufrufen während des Debuggens können Sie nur eigenen Code deaktivieren. Deaktivieren **Sie unter Extras (oder** **Debuggen**) > **Optionen** > **Debuggen**das Kontrollkästchen **nur eigenen Code aktivieren** . Wenn nur eigenen Code deaktiviert ist, wird Nichtbenutzer Code in den Debuggerfenstern angezeigt, und der Debugger kann den Nichtbenutzer Code schrittweise ausführen.

> [!NOTE]
> Nur mein Code wird in Geräteprojekten nicht unterstützt.

### <a name="debug-system-code"></a>Systemcode Debuggen

Wenn Sie Debugsymbole für den Microsoft-Systemcode geladen und nur eigenen Code deaktiviert haben, können Sie wie bei jedem anderen-Vorgang einen System Aufrufvorgang ausführen.

Informationen zum Laden von Microsoft-Symbolen finden Sie unter [Konfigurieren von Symbol Positionen und Laden von Optionen](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**So laden Sie Symbole für eine bestimmte Systemkomponente:**

1. Wenn Sie Debuggen, öffnen Sie das Fenster " **Module** ", indem Sie **Debuggen** > **Windows** > **Module**auswählen oder **STRG**+**alt**+**U**drücken.

1. Im Fenster **Module** können Sie feststellen, in welchen Modulen Symbole in der Spalte **Symbol Status** geladen sind. Klicken Sie mit der rechten Maustaste auf das Modul, für das Sie Symbole laden möchten, und wählen Sie **Symbole laden**aus.

## <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Schrittweise Ausführung von Eigenschaften und Operatoren in verwaltetem Code
 Standardmäßig überspringt der Debugger die Eigenschaften und Operatoren in verwaltetem Code. In den meisten Fällen sorgt dies für einen besseren Debugvorgang. Wählen Sie > **Optionen** **Debuggen** . Deaktivieren Sie auf der Seite **Debuggen** > **Allgemein** das Kontrollkästchen **Eigenschaften und Operatoren überspringen (nur verwaltet)** .

## <a name="see-also"></a>Weitere Informationen
- [What is debugging? (Was bedeutet „Debuggen“?)](../debugger/what-is-debugging.md)
- [Debugging techniques and tools (Debugverfahren und -tools)](../debugger/write-better-code-with-visual-studio.md)
- [Erster Einblick in das Debuggen](../debugger/debugger-feature-tour.md)
