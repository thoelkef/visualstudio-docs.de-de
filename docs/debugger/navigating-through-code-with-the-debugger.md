---
title: Navigieren von Code mit dem Debugger | Microsoft Docs
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301092"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Navigieren durch Code mit dem Visual Studio-Debugger

Der Visual Studio-Debugger kann Ihnen beim Navigieren durch Code helfen, um den Status einer App zu überprüfen und ihren Ausführungsfluss anzuzeigen. Sie können Tastenkombinationen, Debugbefehle, Haltepunkte und andere Features verwenden, um schnell zu dem Code zu gelangen, den Sie untersuchen möchten. Die Vertrautheit mit Debugger-Navigationsbefehlen und Verknüpfungen macht es schneller und einfacher, App-Probleme zu finden und zu beheben.  Wenn Sie zum ersten Mal versucht haben, Code zu debuggen, sollten Sie [Debugging für absolute Anfänger](../debugger/debugging-absolute-beginners.md) und [Debugging-Techniken und -Tools](../debugger/write-better-code-with-visual-studio.md) lesen, bevor Sie diesen Artikel durchgehen.

## <a name="get-into-break-mode"></a>In den "Break-Modus"

Im *Unterbrechungsmodus*wird die App-Ausführung angehalten, während Funktionen, Variablen und Objekte im Arbeitsspeicher verbleiben. Sobald sich der Debugger im Unterbrechungsmodus befindet, können Sie durch ihren Code navigieren. Die häufigste Möglichkeit, schnell in den Pausenmodus zu gelangen, ist entweder:

- Beginnen Sie das Schrittschritt-Code, indem Sie **F10** oder **F11**drücken. Auf diese Weise können Sie schnell den Einstiegspunkt Ihrer App finden, dann können Sie weiter Schrittbefehle drücken, um code zu navigieren.

- [Führen Sie an einem bestimmten Speicherort oder einer bestimmten Funktion](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All)aus, z. B. indem Sie einen [Haltepunkt festlegen](using-breakpoints.md) und Ihre App starten.

   Beispielsweise können Sie im Code-Editor in Visual Studio den Befehl **"Auf Cursor ausführen"** verwenden, um die App zu starten, den Debugger anzuhängen und in den Unterbrechungsmodus zu wechseln, und dann **F11,** um code zu navigieren.

   ![Führen Sie den Cursor aus und treten Sie in den Code ein](../debugger/media/navigate-code-code-stepping.gif "Führen Sie den Cursor aus und treten Sie in den Code ein")

Einmal im Unterbrechungsmodus, können Sie eine Vielzahl von Befehlen verwenden, um durch Ihren Code zu navigieren. Im Unterbrechungsmodus können Sie die Werte von Variablen untersuchen, um nach Verletzungen oder Fehlern zu suchen. Bei einigen Projekttypen können Sie auch Anpassungen an der App vornehmen, während Sie sich im Unterbrechungsmodus befinden.

Die meisten Debuggerfenster, wie die **Modules** und **Watch-Fenster,** sind nur verfügbar, wenn der Debugger an Ihre App angefügt ist. Einige Debugger-Features, z. B. das Anzeigen von Variablenwerten im **Fenster Locals** oder das Auswerten von Ausdrücken im **Überwachungsfenster,** sind nur verfügbar, während der Debugger angehalten wird (d. h. im Unterbrechungsmodus).

> [!NOTE]
> Wenn Sie in Code aufbrechen, bei dem keine Quell- oder Symboldateien (*.pdb*) geladen sind, zeigt der Debugger eine Seite **"Quelldateien nicht gefunden"** oder **"Symbole nicht gefunden"** an, die Ihnen helfen kann, die Dateien zu finden und zu laden. Weitere Informationen finden Sie unter [Angeben von Symbol- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Wenn Sie die Symbol- oder Quelldateien nicht laden können, können Sie die Baugruppenanweisungen weiterhin im **Fenster Demontage** debuggen.

## <a name="step-through-code"></a>Schritt-für-Schritt-Ausführung des Codes

Die Debuggerschrittbefehle helfen Ihnen, den App-Status zu überprüfen oder mehr über den Ausführungsfluss zu erfahren.

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a>Schritt in Codezeile für Zeile

Um jede Anweisung während des Debuggens zu beenden, verwenden Sie **Debug** > **Step Into**, oder drücken Sie **F11**.

Der Debugger führt Codeanweisungen durch, nicht physische Zeilen. Beispielsweise kann eine `if`-Klausel in eine Zeile geschrieben werden:

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

Wenn Sie jedoch in diese Zeile einsteigen, behandelt der Debugger die Bedingung als einen Schritt und die Folge als einen anderen. Im vorherigen Beispiel ist die Bedingung wahr.

Bei einem geschachtelten Funktionsaufruf führt **Einzelschritt** die am tiefsten geschachtelte Funktion in Einzelschritten aus. Wenn Sie z. B. **Step** `Func1(Func2())`Into für einen Aufruf `Func2`wie verwenden, wird der Debugger in die Funktion einschritten.

>[!TIP]
>Wenn Sie jede Codezeile ausführen, können Sie mit der Maus auf Variablen zeigen, um deren Werte anzuzeigen, oder die [Fenster Locals](autos-and-locals-windows.md) und [Watch](watch-and-quickwatch-windows.md) verwenden, um zu beobachten, wie sich die Werte ändern. Sie können die [Aufrufliste](how-to-use-the-call-stack-window.md) auch visuell verfolgen, während Sie in Funktionen eintreten. (Nur für Visual Studio Enterprise siehe [Zuordnungsmethoden auf der Aufrufliste beim Debuggen](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)).

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a>Schritt durch Code und Überspringen einiger Funktionen

Möglicherweise ist eine Funktion beim Debuggen nicht wichtig, oder Sie wissen, dass sie funktioniert, wie gut getesteter Bibliothekscode. Sie können die folgenden Befehle verwenden, um Code während des Codeschritts zu überspringen. Die Funktionen werden weiterhin ausgeführt, aber der Debugger überspringt sie.

|Tastaturbefehl|Menübefehle für das Debuggen|Beschreibung|
|----------------------|------------------|-----------------|
|**F10**|**Prozedurschritt**|Wenn die aktuelle Zeile einen Funktionsaufruf enthält, führt **Step Over** den Code aus und setzt die Ausführung in der ersten Codezeile aus, nachdem die aufgerufene Funktion zurückgegeben wurde.|
|**Shift**+**F11**|**Step Out**|**Step Out** führt weiterhin Code aus und setzt die Ausführung aus, wenn die aktuelle Funktion zurückkehrt. Der Debugger überspringt die aktuelle Funktion.|

## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>Ausführen an einem bestimmten Ort oder einer bestimmten Funktion

Sie können es vorziehen, direkt an einem bestimmten Speicherort oder einer bestimmten Funktion auszuführen, wenn Sie genau wissen, welchen Code Sie überprüfen möchten, oder wenn Sie wissen, wo Sie mit dem Debuggen beginnen möchten.

### <a name="run-to-a-breakpoint-in-code"></a>Ausführen zu einem Haltepunkt im Code

Um einen einfachen Haltepunkt im Code festzulegen, klicken Sie auf den linken Rand neben der Codezeile, an der Sie die Ausführung anhalten möchten. Sie können auch die Zeile auswählen und **F9**drücken,**Breakpoint** **debugen** > auswählen oder mit der rechten Maustaste klicken und **Haltepunkt** > **einfügen Breakpoint**auswählen. Der Haltepunkt wird als roter Punkt am linken Rand neben der Codezeile angezeigt. Der Debugger unterbricht die Ausführung kurz vor der Ausführung der Zeile.

![Festlegen eines Haltepunkts](../debugger/media/dbg_basics_setbreakpoint.png "Haltepunkt festlegen")

Haltepunkte in Visual Studio bieten einen umfangreichen Satz von zusätzlichen Funktionen, wie z. B. bedingte Haltepunkte und Ablaufverfolgungspunkte. Weitere Informationen finden Sie unter [Verwenden von Haltepunkten](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>Ausführen zu einem Funktionshaltepunkt

Sie können den Debugger anweisen, ausgeführt zu werden, bis er eine angegebene Funktion erreicht. Sie können die Funktion anhand ihres Namens angeben oder in der Aufrufliste auswählen.

**So geben Sie einen Funktionshaltepunkt nach Namen an**

1. **Wählen Sie Debug** > **New Breakpoint** > **Function Breakpoint**

1. Geben Sie im Dialogfeld **"Neuer Funktionshaltepunkt"** den Namen der Funktion ein, und wählen Sie deren Sprache aus.

   ![Neues Dialogfeld "Funktionshaltepunkt"](../debugger/media/dbg_execution_newbreakpoint.png "Neuer Funktions-Breakpoint")

1. Wählen Sie **OK** aus.

Wenn die Funktion überladen ist oder in mehr als einem Namespace ist, können Sie im Fenster **Haltepunkte** den gewünschten auswählen.

![Überladene Funktionshaltepunkte](../debugger/media/dbg_execution_overloadedbreakpoints.png "Überladene Funktionshaltepunkte")

**So wählen Sie einen Funktionshaltepunkt aus der Aufrufliste aus**

1. Öffnen Sie während des Debuggens das **Fenster Aufrufliste,** indem Sie**Windows** > **Call Stack** **debuggen** > auswählen.

1. Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf eine Funktion, und wählen Sie **Auf Cursor ausführen**aus, oder drücken Sie **Strg**+**F10**.

Informationen zum visuellen Nachverfolgen der Aufrufliste finden Sie [unter Zuordnen von Methoden in der Aufrufliste während des Debuggens](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Ausführen zu einer Cursorposition

Um zur Cursorposition, im Quellcode oder im **Fenster Aufrufliste** auszuführen, wählen Sie die Zeile aus, an der Sie mit der rechten Maustaste klicken möchten, und wählen Sie **Auf Cursor ausführen**aus, oder drücken Sie **Strg**+**F10**. Die Auswahl **von Run To Cursor** ist wie das Festlegen eines temporären Haltepunkts.

### <a name="run-to-click"></a>Ausführung bis Klick

Während Sie im Debugger angehalten haben, können Sie mit der Maus auf eine Anweisung im Quellcode oder im **Disassemblierungsfenster** zeigen und das Symbol Ausführung ausführen auswählen, um hier ein grünes Pfeilsymbol **anzuzeigen.** Wenn Sie **Run to Click** verwenden, müssen Sie keinen temporären Haltepunkt festlegen.

![Run to Click](../debugger/media/dbg-run-to-click.png "Ausführung bis Klick") (Ausführen bis Klick)

> [!NOTE]
> **Run to Click** ist [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]ab verfügbar.

### <a name="manually-break-into-code"></a>Manuelles Unterbrechen im Code

Um die nächste verfügbare Codezeile in einer laufenden App zu unterbrechen, wählen Sie Alle > **debuggen**aus , oder drücken Sie **Strg**+ **Debug****Alt-Pause****Alt**+.

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a>Bewegen Sie den Zeiger, um den Ausführungsfluss zu ändern

Während der Debugger angehalten wird, markiert eine gelbe Pfeilspitze am Rand des Quellcodes oder des **Disassemblierungsfensters** den Speicherort der nächsten auszuführenden Anweisung. Sie können die nächste auszuführende Anweisung ändern, indem Sie diese Pfeilspitze verschieben. Sie können einen Teil des Codes überspringen oder zu einer vorherigen Zeile zurückkehren. Das Verschieben des Zeigers ist nützlich für Situationen wie das Überspringen eines Codeabschnitts, der einen bekannten Fehler enthält.

 ![Bewegen Sie den Zeiger](../debugger/media/dbg_basics_example3.gif "Bewegen Sie den Zeiger")

Um die nächste auszuführende Anweisung zu ändern, muss sich der Debugger im Unterbrechungsmodus befinden. Ziehen Sie im Quellcode- oder **Demontagefenster** die gelbe Pfeilspitze in eine andere Zeile, oder klicken Sie mit der rechten Maustaste auf die Zeile, die Sie als nächstes ausführen möchten, und wählen Sie **Nächste Anweisung festlegen**aus.

Der Programmzähler springt direkt an die neue Position, und Anweisungen zwischen den alten und neuen Ausführungspunkten werden nicht ausgeführt. Wenn Sie jedoch den Ausführungspunkt nach hinten verschieben, werden die dazwischen liegenden Anweisungen nicht rückgängig gemacht.

>[!CAUTION]
>- Wenn Sie die nächste Anweisung in eine andere Funktion oder in einen anderen Gültigkeitsbereich verschieben, wird i. d. R. die Aufrufliste beeinträchtigt, wodurch ein Laufzeitfehler oder eine Ausnahme ausgelöst wird. Wenn Sie versuchen, die nächste Anweisung in einen anderen Gültigkeitsbereich zu verschieben, wird ein Dialogfenster mit einer Warnung geöffnet, in dem Sie den Vorgang abbrechen können.
>- In Visual Basic können Sie die nächste Anweisung nicht in einen anderen Bereich oder in eine andere Funktion verlegen.
>- In systemeigenem C++-Code kann das Festlegen der nächsten Anweisung bei aktivierter Laufzeitprüfung dazu führen, dass am Ende der Methode eine Ausnahme ausgelöst wird.
>- Wenn die Funktion "Bearbeiten und Fortfahren" aktiviert ist, schlägt das Ausführen der Option **Nächste Anweisung festlegen** fehl, wenn Sie Änderungen vorgenommen haben, die von "Bearbeiten und Fortfahren" nicht sofort neu zugeordnet werden können. Dies kann auftreten, wenn Sie z. B. Code in einem catch-Block bearbeitet haben. In diesem Fall wird eine Fehlermeldung angezeigt, dass der Vorgang nicht unterstützt wird.
>- Im verwalteten Code können Sie die nächste Anweisung nicht verschieben, wenn:
>   - Die nächste Anweisung und die aktuelle Anweisung befinden sich in verschiedenen Methoden.
>   - Das Debuggen wurde durch Just-In-Time-Debugging gestartet.
>   - Eine Aufrufliste wird abwickeln.
>   - Eine System.StackOverflowException oder eine System.Threading.ThreadAbortException wurden ausgelöst.

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Debuggen von Nicht-Benutzercode

Standardmäßig versucht der Debugger, nur Ihren App-Code zu debuggen, indem er eine Einstellung namens *Just My Code*aktiviert. Weitere Informationen dazu, wie diese Funktion für verschiedene Projekttypen und Sprachen funktioniert und wie Sie sie anpassen können, finden Sie unter [Nur mein Code](../debugger/just-my-code.md).

Um frameworkcode, bibliothekscode oder Systemaufrufe während des Debuggens zu betrachten, können Sie Just My Code deaktivieren. Deaktivieren **Sie** unter Tools (oder **Debug)**> **Options** > **Debugging**das Kontrollkästchen **Nur meinen Code aktivieren.** Wenn Nur mein Code deaktiviert ist, wird nicht benutzergebundener Code in den Debuggerfenstern angezeigt, und der Debugger kann in den Nichtbenutzercode eindringen.

> [!NOTE]
> Nur mein Code wird in Geräteprojekten nicht unterstützt.

### <a name="debug-system-code"></a>Debugsystemcode

Wenn Sie Debugsymbole für Microsoft-Systemcode geladen und Just My Code deaktiviert haben, können Sie wie bei jedem anderen Aufruf in einen Systemaufruf einsteigen.

Informationen zum Laden von Microsoft-Symbolen finden Sie unter Konfigurieren von [Symbolpositionen und Ladeoptionen](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**So laden Sie Symbole für eine bestimmte Systemkomponente:**

1. Öffnen Sie während des Debuggens das Fenster **Module,** indem Sie > **Windows** > **Windows-Module** **debuggen**auswählen oder **Strg**+**Alt**+**U**drücken.

1. Im Fenster **Module** können Sie feststellen, welche Module Symbole in der Spalte **Symbolstatus** geladen haben. Klicken Sie mit der rechten Maustaste auf das Modul, für das Sie Symbole laden möchten, und wählen Sie **Symbole laden**aus.

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Schrittweise Ausführung von Eigenschaften und Operatoren in verwaltetem Code
 Standardmäßig überspringt der Debugger die Eigenschaften und Operatoren in verwaltetem Code. In den meisten Fällen sorgt dies für einen besseren Debugvorgang. Um das Eintreten in Eigenschaften oder Operatoren zu aktivieren, wählen Sie > **Debugoptionen**aus. **Debug** Deaktivieren Sie auf der Seite > **"Allgemeines** **Debuggen"** das Kontrollkästchen **Schritt über Eigenschaften und Operatoren (nur verwaltet).**

## <a name="see-also"></a>Weitere Informationen
- [Was bedeutet „Debuggen“?](../debugger/what-is-debugging.md)
- [Debugverfahren und -tools](../debugger/write-better-code-with-visual-studio.md)
- [Erster Blick auf das Debuggen](../debugger/debugger-feature-tour.md)
