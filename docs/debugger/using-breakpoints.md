---
title: Verwenden von Breakpoints im Debugger | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/28/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.location.address
- vs.debug.breakpt.constraints
- vs.debug.breakpoints.delete
- vs.debug.breakpt.location.data
- vc.breakpoints
- vs.debug.breakpt.condition
- vs.debug.breakpt.location.function
- vs.debug.breakpoints
- vs.debug.menu.insert
- vs.debug.filenames
- vs.debug.breakpt.action
- vs.debug.sourcewin.insert
- vs.debug.address
- vs.debug.data
- vs.debug.func
- vs.debug.breakpt.location.file
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6a8ee96834fc20186ba6719a7c4f377fea45d6b
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187320"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Verwenden von Breakpoints im Visual Studio-Debugger

Breakpoints sind eine der wichtigsten Debuggingtechniken in der Toolbox Ihres Entwicklers. Haltepunkte legen Sie fest, wo Sie die Debugger-Ausführung anhalten möchten. Beispielsweise möchten Sie möglicherweise den Status der Code Variablen anzeigen oder die aufrufsstapel an einem bestimmten Haltepunkt sehen.  Wenn Sie versuchen, eine Warnung oder ein Problem zu beheben, während Sie Breakpoints verwenden, finden Sie weitere Informationen unter Problembehandlung [bei Breakpoints im Visual Studio-Debugger](../debugger/troubleshooting-breakpoints.md).

> [!NOTE]
> Wenn Sie die Aufgabe oder das Problem kennen, die Sie lösen möchten, aber wissen müssen, welche Art von Haltepunkt Sie verwenden möchten, [finden Sie untersuchen der debugaufgabe Weitere Informationen](../debugger/find-your-debugging-task.md#pause-running-code).

## <a name="BKMK_Overview"></a>Festlegen von Breakpoints im Quellcode

Sie können einen Haltepunkt für jede beliebige Zeile mit ausführbarem Code festlegen. Im folgenden C# Code können Sie z. b. einen Haltepunkt für die Variablen Deklaration, die`for`-Schleife oder einen beliebigen Code in der`for`-Schleife festlegen. Es ist nicht möglich, einen Haltepunkt in den Namespace-oder Klassen Deklarationen oder in der Methoden Signatur festzulegen.

Um einen Haltepunkt im Quellcode festzulegen, klicken Sie auf den äußersten linken Rand neben einer Codezeile. Sie können auch die Zeile auswählen und **F9**drücken, **Debuggen** > halte **Punkt umschalten**auswählen oder mit der rechten Maustaste klicken und halte **Punkt** > halte **Punkt einfügen**auswählen. Der Haltepunkt wird als roter Punkt am linken Rand angezeigt.

Für die meisten Sprachen C#, einschließlich, werden Breakpoint und Current Execution Lines automatisch hervorgehoben. Für C++ Code können Sie die Hervorhebung von Haltepunkt-und aktuellen Zeilen aktivieren, indem Sie **Extras (oder** **Debuggen**) > **Optionen** > **Debuggen** auswählen >  **gesamte Quellzeile für Haltepunkte und aktuell markieren. -AnweisungC++ (nur)** .

![Festlegen eines Breakpoints](../debugger/media/basicbreakpoint.png "Grundlegender Haltepunkt")

Beim Debuggen wird die Ausführung am Haltepunkt angehalten, bevor der Code in dieser Zeile ausgeführt wird. Das breakpointsymbol zeigt einen gelben Pfeil.

Am Haltepunkt im folgenden Beispiel ist der Wert von `testInt` immer noch 1. Daher wurde der Wert nicht geändert, da die Variable initialisiert (auf den Wert 1 festgelegt wurde), da die Anweisung in gelb noch nicht ausgeführt wurde.

![Breakpoint-Ausführung beendet](../debugger/media/breakpointexecution.png "Breakpoint-Ausführung")

Wenn der Debugger am Haltepunkt angehalten wird, können Sie den aktuellen Status der APP, einschließlich der [Variablen Werte](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) und der- [aufrufsstapel](../debugger/how-to-use-the-call-stack-window.md), überprüfen.

Im folgenden finden Sie einige allgemeine Anweisungen zum Arbeiten mit Breakpoints.

- Der Breakpoint ist eine UMSCHALT Fläche. Sie können darauf klicken, **F9**drücken oder den halte **Punkt** mit **Debuggen** > ein-und ausschalten, um ihn zu löschen oder erneut einzufügen.

- Um einen Haltepunkt zu deaktivieren, ohne ihn zu löschen, zeigen Sie mit der Maus darauf, oder klicken Sie mit der rechten Maustaste darauf und wählen halte **Punkt deaktivieren** Deaktivierte Breakpoints werden im linken Rand oder im Fenster **Breakpoints** als leere Punkte angezeigt. Um einen Haltepunkt wieder zu aktivieren, zeigen Sie mit der Maus darauf, oder klicken Sie mit der rechten Maustaste, und wählen Sie halte **Punkt aktivieren**.

- Legen Sie Bedingungen und Aktionen fest, fügen Sie Bezeichnungen hinzu, und bearbeiten Sie Sie, oder exportieren Sie einen Haltepunkt, indem Sie mit der rechten Maustaste darauf klicken und den entsprechenden Befehl auswählen oder darauf zeigen und das **Einstellungs** Symbol auswählen.

## <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Haltepunktaktionen und Ablaufverfolgungspunkte

Beim *Ablaufverfolgungspunkt* handelt es sich um einen Haltepunkt, der eine Meldung im Fenster **Ausgabe** ausgibt. Ein Ablauf Verfolgungs Punkt kann wie eine temporäre Ablauf Verfolgungs Anweisung in der Programmiersprache agieren und hält die Ausführung von Code nicht an. Sie erstellen einen Ablauf Verfolgungs Punkt, indem Sie im Fenster "halte **Punkt Einstellungen** " eine spezielle Aktion festlegen. Ausführliche Anweisungen finden Sie unter Verwenden von Ablauf Verfolgungs [Punkten im Visual Studio-Debugger](../debugger/using-tracepoints.md).

## <a name="breakpoint-conditions"></a>Haltepunktbedingungen

Sie können steuern, wann und wo ein Haltepunkt ausgeführt wird, indem Sie Bedingungen festlegen. Die Bedingung kann ein beliebiger gültiger Ausdruck sein, der vom Debugger erkannt wird. Weitere Informationen zu gültigen Ausdrücken finden Sie unter [Expressions in the Debugger (Ausdrücke im Debugger)](../debugger/expressions-in-the-debugger.md).

**So legen Sie eine Haltepunkt Bedingung fest:**

1. Klicken Sie mit der rechten Maustaste auf das Haltepunkt Symbol, und wählen Sie **Bedingungen** Oder zeigen Sie auf das Haltepunkt Symbol, wählen Sie das Symbol " **Einstellungen** " aus, und wählen Sie dann im Fenster "halte **Punkt Einstellungen** " **Bedingungen** aus.

   Sie können auch Bedingungen im Fenster **Breakpoints** festlegen, indem Sie mit der rechten Maustaste auf einen Haltepunkt klicken und **Einstellungen**auswählen und dann **Bedingungen**auswählen.

   ![Haltepunkt Einstellungen](../debugger/media/breakpointsettings.png "Breakpointsettings")

2. Wählen Sie in der Dropdown Liste **bedingter Ausdruck**, **Treffer Anzahl**oder **Filter**aus, und legen Sie den Wert entsprechend fest.

3. Wählen Sie **Schließen** aus, oder drücken Sie **STRG**+**Eingabe** Taste, um das Fenster halte **Punkt Einstellungen** zu schließen. Oder wählen Sie im Fenster **Breakpoints** die Option **OK** aus, um das Dialogfeld zu schließen.

Haltepunkte mit festgelegten Bedingungen werden in den Fenstern Quellcode und **Breakpoints** mit einem **+** Symbol angezeigt.

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Erstellen eines Bedingungs Ausdrucks

Wenn Sie **Bedingungs Ausdruck**auswählen, können Sie zwischen zwei Bedingungen wählen: **ist true** oder **bei Änderung**. Wählen Sie **true** aus, um die Unterbrechung zu unterbrechen, wenn der Ausdruck erfüllt ist, oder, **Wenn** der Wert des Ausdrucks geändert wurde.

Im folgenden Beispiel wird der Breakpoint nur dann getroffen, wenn der Wert von `testInt` **4**ist:

![Haltepunkt Bedingung ist "true"](../debugger/media/breakpointconditionistrue.png "Haltepunkt ist "true"")

Im folgenden Beispiel wird der Breakpoint nur dann getroffen, wenn sich der Wert `testInt` ändert:

![Haltepunkt bei Änderung](../debugger/media/breakpointwhenchanged.png "Haltepunkt bei Änderung")

Wenn Sie eine Haltepunktbedingung mit ungültiger Syntax festlegen, wird sofort eine Warnmeldung angezeigt. Wenn Sie eine Haltepunktbedingung mit gültiger Syntax aber ungültiger Semantik angeben, wird beim ersten Erreichen des Haltepunkts eine Warnmeldung angezeigt. In beiden Fällen wird der Debugger unterbrochen, wenn er auf den ungültigen Breakpoint trifft. Der Haltepunkt wird nur übersprungen, wenn die Bedingung gültig ist mit `false`bewertet wird.

>[!NOTE]
>Das Verhalten des Felds **Bei Änderung** unterscheidet sich je nach Programmiersprache.
>- Bei System eigenem Code wird die erste Auswertung der Bedingung vom Debugger nicht als Änderung betrachtet. der Haltepunkt bei der ersten Auswertung wird daher nicht gefunden.
>- Bei verwaltetem Code trifft der Debugger den Haltepunkt bei der ersten Auswertung, nachdem **geändert** ausgewählt wurde.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Verwenden von Objekt-IDs in bedingtenC# Ausdrücken F# (nur und)

 Es gibt Zeiten, in denen Sie das Verhalten eines bestimmten Objekts beobachten möchten. Beispielsweise können Sie herausfinden, warum ein Objekt mehrmals in eine Auflistung eingefügt wurde. In C# und F# können Sie Objekt-IDs für bestimmte Instanzen von [Verweistypen](/dotnet/csharp/language-reference/keywords/reference-types) erstellen und in Haltepunktbedingungen verwenden. Die Objekt-ID wird von den Debugdiensten der CLR (Common Language Runtime) generiert und dem Objekt zugeordnet.

**So erstellen Sie eine Objekt-ID:**

1. Legen Sie einen Haltepunkt im Code fest, nachdem das Objekt erstellt wurde.

2. Starten Sie das Debugging, und wenn die Ausführung am Haltepunkt angehalten wird, wählen Sie **Debuggen** > **Fenster** ** > lokal** oder **alt**+**4** aus, **um das Fenster** lokal zu öffnen.

   Suchen Sie die jeweilige Objektinstanz im **Lokal Fenster,** klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Objekt-ID erstellen**aus.

   Sie sollten ein **$** und eine Zahl im **Lokalfenster** einen Haltepunkt festlegen. Dies ist die Objekt-ID.

3. Fügen Sie einen neuen Haltepunkt an dem Punkt hinzu, den Sie untersuchen möchten. beispielsweise, wenn das Objekt der Auflistung hinzugefügt werden soll. Klicken Sie mit der rechten Maustaste auf den Haltepunkt, und wählen Sie **Bedingungen** aus.

4. Verwenden Sie die Objekt-ID im Feld **Bedingter Ausdruck**. Wenn die Variable `item` z. b. das Objekt ist, das der Auflistung hinzugefügt werden soll, wählen Sie **true** aus, und geben Sie **Item = = $\<n >** ein, wobei \<n > die Objekt-ID-Nummer ist.

   Die Ausführung wird an dem Punkt unterbrochen, an dem dieses Objekt der Auflistung hinzugefügt werden soll.

   Um die Objekt-ID zu löschen, klicken Sie im **Lokal Fenster mit** der rechten Maustaste auf die Variable und wählen Objekt- **ID löschen**aus.

> [!NOTE]
> Objekt-IDs erstellen Weak-Verweise und verhindern nicht, dass das Objekt in die Garbage Collection aufgenommen wird. Sie gelten nur für die aktuelle Debugsitzung.

### <a name="set-a-hit-count-condition"></a>Festlegen der Bedingung für die Treffer Anzahl

Wenn Sie vermuten, dass eine Schleife im Code nach einer bestimmten Anzahl von Iterationen ein fehlerhaftes Verhalten aufweist, können Sie einen Haltepunkt festlegen, um die Ausführung nach dieser Anzahl von Treffern zu unterbrechen, anstatt wiederholt **F5** drücken zu müssen, um diese Iteration zu erreichen.

Wählen Sie unter **Bedingungen** im Fenster halte **Punkt Einstellungen** die Option **Treffer Anzahl**aus, und geben Sie dann die Anzahl der Iterationen an. Im folgenden Beispiel wird der Breakpoint so festgelegt, dass er für jede andere Iterationen auf Treffer trifft:

![Breakpoint-Treffer Anzahl](../debugger/media/breakpointhitcount.png "Breakpointhitcount")

### <a name="set-a-filter-condition"></a>Festlegen einer Filterbedingung

Sie können einen Haltepunkt so einschränken, dass dieser nur auf bestimmten Geräten oder in angegebenen Prozesse und Threads aktiviert wird.

Wählen Sie unter **Bedingungen** im Fenster halte **Punkt Einstellungen** die Option **Filter**aus, und geben Sie dann einen oder mehrere der folgenden Ausdrücke ein:

- MachineName = "name"
- ProcessId = value
- ProcessName = "name"
- ThreadId = value
- ThreadName = "name"

Schließen Sie Zeichenfolgewerte in doppelte Anführungszeichen ein. Sie können Klauseln mit `&` (AND), `||` (OR), `!` (NOT), und Klammern kombinieren.

## <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Funktions Breakpoints festlegen

Sie können die Ausführung unterbrechen, wenn eine Funktion aufgerufen wird. Dies ist beispielsweise hilfreich, wenn Sie den Funktionsnamen, aber nicht seinen Speicherort kennen. Dies ist auch nützlich, wenn Sie über Funktionen verfügen, die denselben Namen aufweisen, und Sie alle unterbrechen möchten (z. b. überladene Funktionen oder Funktionen in verschiedenen Projekten).

**So legen Sie einen Funktions Haltepunkt fest:**

1. Wählen Sie **Debuggen** > **neuen Breakpoint** > **Funktions Breakpoints**aus, oder drücken Sie **alt**+**F9** > **STRG**+**B**.

   Sie können auch im Fenster **Breakpoints** die Option **New** > **Function Breakpoint** auswählen.

1. Geben Sie im Dialogfeld **neuer Funktions Breakpunkt** den Funktionsnamen in das Feld **Funktionsname** ein.

   So schränken Sie die Funktionsspezifikation ein:

   - Verwenden Sie den voll qualifizierten Funktionsnamen.

     Beispiel: `Namespace1.ClassX.MethodA()`

   - Fügen Sie die Parametertypen einer überladenen Funktion hinzu.

     Beispiel: `MethodA(int, string)`

   - Verwenden Sie das Symbol "!", um das Modul anzugeben.

     Ein Beispiel: `App1.dll!MethodA`

   - Verwenden Sie den Kontext Operator in C++nativem Format.

     `{function, , [module]} [+<line offset from start of method>]`

     Ein Beispiel: `{MethodA, , App1.dll}+2`

1. Wählen Sie in der Dropdown Liste **Sprache** die Sprache der Funktion aus.

1. Klicken Sie auf **OK**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Festlegen eines Funktions halte Punkts mit einer Speicheradresse ( C++ nur System eigen)
 Sie können die Adresse eines Objekts verwenden, um einen Funktions Haltepunkt für eine Methode festzulegen, die von einer bestimmten Instanz einer Klasse aufgerufen wird.  Wenn Sie z. b. ein adressierbares Objekt vom Typ `my_class`haben, können Sie einen Funktions Haltepunkt für die `my_method` Methode festlegen, die von der-Instanz aufgerufen wird.

1. Legen Sie einen Haltepunkt fest, nachdem die Instanz der-Klasse instanziiert wurde.

2. Suchen Sie nach der Adresse der Instanz (z. b. `0xcccccccc`).

3. Wählen Sie **Debuggen** > **neuen Breakpoint** > **Funktions Breakpoints**aus, oder drücken Sie **alt**+**F9** > **STRG**+**B**.

4. Fügen Sie Folgendes in das Feld **Funktions Name** ein, und **C++** wählen Sie Sprache aus.

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="BKMK_set_a_data_breakpoint_managed"></a>Festlegen von Daten Breakpoints (.net Core 3,0 oder höher)

Daten Breakpoints unterbrechen die Ausführung, wenn sich die-Eigenschaft eines bestimmten Objekts ändert.

**So legen Sie einen Daten Haltepunkt fest**

1. Starten Sie in einem .net Core-Projekt das Debuggen, und warten Sie, bis ein Haltepunkt erreicht wird.

2. Klicken Sie **im Fenster** Auto, **Überwachung**oder lokal mit der rechten Maustaste auf eine Eigenschaft, und wählen Sie im Kontext **Menü die Option**unter **brechen bei Wertänderungen** aus.

    ![Haltepunkt für verwaltete Daten](../debugger/media/managed-data-breakpoint.png "Haltepunkt für verwaltete Daten")

Daten Breakpoints in .net Core funktionieren nicht für:

- Eigenschaften, die in QuickInfo, lokal, Auto oder Überwachungsfenster nicht erweiterbar sind
- Statische Variablen
- Klassen mit dem Attribut "tbuggertypeproxy"
- Felder innerhalb von Strukturen

::: moniker-end

## <a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Daten Breakpoints festlegen (nur C++ nativ)

 Daten Breakpoints unterbrechen die Ausführung, wenn sich ein Wert ändert, der an einer bestimmten Speicheradresse gespeichert ist. Wenn der Wert ausgelesen jedoch nicht geändert wird, wird die Ausführung nicht unterbrochen.

**So legen Sie einen Daten Haltepunkt fest:**

1. Starten Sie C++ in einem Projekt das Debuggen, und warten Sie, bis ein Haltepunkt erreicht wird. Wählen Sie im Menü **Debuggen** die Option **Neuer Haltepunkt** > **Daten Breakpoint** aus.

    Sie können auch **im Fenster** **Breakpoints** den Eintrag **New** > **Data Breakpoint** auswählen oder mit der rechten Maustaste auf ein Element im Fenster **Auto,** **Watch**oder lokal klicken und unter **brechen bei Wertänderungen** im Kontextmenü auswählen.

2. Geben Sie im Feld **Adresse** eine Speicheradresse oder einen Ausdruck ein, der als Speicheradresse ausgewertet wird. Geben Sie beispielsweise `&avar` ein, um die Ausführung bei einer Änderung des Inhalts der Variable `avar` zu unterbrechen.

3. Geben Sie im Feld **Byteanzahl** die Anzahl der Bytes an, die der Debugger überwachen soll. Wenn Sie beispielsweise **4**auswählen, überwacht der Debugger vier Bytes ab `&avar` und unterbricht, wenn eines dieser Bytes seinen Wert ändert.

Daten Breakpoints funktionieren unter den folgenden Bedingungen nicht:
- Ein Prozess, der nicht gedebuggt wird, wird in einen Speicherbereich geschrieben.
- Der Speicherbereich wird von mindestens zwei Prozessen gemeinsam verwendet.
- Der Speicherort wird innerhalb des Kernels aktualisiert. Wenn z. b. der Arbeitsspeicher an die 32-Bit-Windows-`ReadFile` Funktion weitergegeben wird, wird der Arbeitsspeicher aus dem Kernel Modus aktualisiert, sodass der Debugger bei der Aktualisierung nicht unterbricht.
- Dabei ist der Überwachungs Ausdruck auf 32-Bit-Hardware und 8 Bytes auf 64-Bit-Hardware größer als 4 Bytes. Dies ist eine Einschränkung der x86-Architektur.

> [!NOTE]
> - Daten Breakpoints sind von bestimmten Speicheradressen abhängig. Die Adresse einer Variablen ändert sich von einer Debugsitzung zur nächsten, sodass Daten Breakpoints am Ende jeder Debugsitzung automatisch deaktiviert werden.
>
> - Wenn Sie einen Datenhaltepunkt bei einer lokalen Variable festlegen, bleibt der Haltepunkt aktiviert, wenn die Funktion beendet wird, die Speicheradresse ist jedoch nicht mehr gültig, und das Verhalten des Haltepunkts ist unvorhersehbar. Wenn Sie einen Daten Haltepunkt in einer lokalen Variable festlegen, sollten Sie den Breakpoint vor dem Beenden der Funktion löschen oder deaktivieren.

## <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Verwalten von Haltepunkten im Haltepunktefenster

 Mit dem Fenster **Breakpoints** können Sie alle Breakpoints in der Projekt Mappe anzeigen und verwalten. Dieser zentralisierte Speicherort ist besonders bei einer großen Projekt Mappe oder bei komplexen Debugszenarien hilfreich, in denen Haltepunkte wichtig sind.

Im Fenster **Breakpoints** können Sie Breakpoints durchsuchen, sortieren, Filtern, aktivieren, deaktivieren oder löschen. Sie können auch Bedingungen und Aktionen festlegen oder einen neuen Funktions-oder Daten Haltepunkt hinzufügen.

Um das Fenster **Breakpoints** zu öffnen, wählen Sie **Debuggen** > **Fenster** > **Breakpoints**aus, oder drücken Sie **alt**+**F9** oder **STRG**+**alt**+**B**.

![Fenster "Breakpoints"](../debugger/media/breakpointswindow.png ""Haltepunkte" (Fenster)")

Um die Spalten auszuwählen, die im Fenster **Breakpoints** angezeigt werden sollen, wählen Sie **Spalten anzeigen**aus. Wählen Sie eine Spaltenüberschrift aus, um die Liste der Breakpoints nach dieser Spalte zu sortieren.

### <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Haltepunktbezeichnungen
Mit Bezeichnungen können Sie die Liste der Breakpoints im Fenster **Breakpoints** sortieren und filtern.

1. Wenn Sie einem Breakpoint eine Bezeichnung hinzufügen möchten, klicken Sie mit der rechten Maustaste auf den Breakpoint im Quellcode oder im Fenster **Breakpoints** , und wählen Sie dann **Bezeichnungen bearbeiten**aus. Fügen Sie eine neue Bezeichnung hinzu, oder wählen Sie eine vorhandene Bezeichnung aus, und klicken Sie dann auf **OK**.
2. Sortieren Sie die **breakpointliste im Fenster Breakpoints** , indem Sie die **Bezeichnungen**, **Bedingungen**oder andere Spaltenüberschriften auswählen. Sie können die **anzuzeigenden** Spalten auswählen, indem Sie in der Symbolleiste die Option Spalten anzeigen auswählen.

### <a name="export-and-import-breakpoints"></a>Exportieren und Importieren von Haltepunkten
 Wenn Sie den Zustand und den Speicherort der Breakpoints speichern oder freigeben möchten, können Sie Sie exportieren oder importieren.

- Um einen einzelnen Haltepunkt in eine XML-Datei zu exportieren, klicken Sie mit der rechten Maustaste auf den Breakpoint im Fenster Quellcode oder **Breakpoints** , und wählen Sie **exportieren** oder **Exportieren ausgewählt**aus. Wählen Sie einen Export Speicherort aus, und klicken Sie dann auf **Speichern**. Der Standard Speicherort ist der Projektmappenordner.
- Wenn Sie mehrere Haltepunkte exportieren möchten, wählen Sie im Fenster **Breakpoints** die Kontrollkästchen neben den Breakpoints aus, oder geben Sie Suchkriterien in das **Suchfeld** ein. Wählen Sie das Symbol **alle Haltepunkte exportieren, die dem aktuellen Suchkriterium entsprechen** aus, und speichern Sie die Datei.
- Wenn Sie alle Haltepunkte exportieren möchten, deaktivieren Sie alle Kontrollkästchen, und lassen Sie das **Suchfeld** leer. Wählen Sie das Symbol **alle Haltepunkte exportieren, die dem aktuellen Suchkriterium entsprechen** aus, und speichern Sie die Datei.
- Wenn Sie Haltepunkte importieren möchten, wählen Sie im Fenster **Breakpoints** das Symbol halte **Punkte aus einer Datei importieren aus** , navigieren Sie zum Speicherort der XML-Datei, und wählen Sie **Öffnen**aus.

## <a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a>Haltepunkte in Debuggerfenstern festlegen

Sie können auch Haltepunkte in den Fenstern " **aufrufsstapel** " und " **Disassembly** -Debugger" festlegen.

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Festlegen eines halte Punkts im Fenster "aufrufsstapel"

 Um bei der Anweisung oder Zeile zu unterbrechen, zu der eine aufrufende Funktion zurückkehrt, können Sie im Fenster **Aufruf Stapel** einen Haltepunkt festlegen.

**So legen Sie einen Haltepunkt im Fenster "aufrufsstapel" fest:**

1. Um das Fenster "Fenster" **aufzurufen** , müssen Sie während des Debuggens angehalten werden. Wählen Sie **Debuggen** > **Windows** > - **aufrufsstapel**, oder drücken Sie **STRG**+**alt**+**C**.

2. Klicken Sie im Fenster **Aufruf Stapel** mit der rechten Maustaste auf die aufrufende Funktion, und wählen Sie halte **Punkt** > halte **Punkt einfügen**aus, oder drücken Sie **F9**.

   Ein breakpointsymbol wird neben dem Namen des Funktions Aufrufes am linken Rand der aufrufsstapel angezeigt.

Der Haltepunkt für die Haltepunkt-Haltepunkt wird im Fenster **Breakpoints** als Adresse mit einem Speicherbereich angezeigt, der der nächsten ausführbaren Anweisung in der Funktion entspricht.

Der Debugger unterbricht bei der Anweisung.

Weitere Informationen zur Aufrufliste finden Sie unter [How to: Use the Call Stack Window (Vorgehensweise: Verwenden des Fensters „Aufrufliste“)](../debugger/how-to-use-the-call-stack-window.md).

Informationen zur visuellen Ablauf Verfolgung von Breakpoints während der Codeausführung finden Sie unter [map-Methoden in der-aufrufsstapel während des](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Festlegen eines halte Punkts im Disassemblyfenster

1. Um das Disassemblyfenster zu öffnen, müssen Sie während des Debuggens angehalten werden. Wählen Sie **Debuggen** > **Windows** > **Disassembly**aus, oder drücken Sie **alt**+**8**.

2. Klicken Sie im Fenster **Disassembly** auf den linken Rand der Anweisung, bei der Sie unterbrechen möchten. Sie können es auch auswählen und **F9**drücken, oder mit der rechten Maustaste klicken und halte **Punkt** > halte **Punkt einfügen**auswählen.

## <a name="see-also"></a>Siehe auch

- [Was bedeutet „Debuggen“?](../debugger/what-is-debugging.md)
- [Schreiben von C# besserem Code mithilfe von Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Erster Einblick in das Debuggen](../debugger/debugger-feature-tour.md)
- [Behandeln von Problemen mit Breakpoints im Visual Studio-Debugger](../debugger/troubleshooting-breakpoints.md)
