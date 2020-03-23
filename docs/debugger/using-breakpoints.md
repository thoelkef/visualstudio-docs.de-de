---
title: Verwenden von Haltepunkten im Debugger | Microsoft Docs
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301026"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Verwenden von Haltepunkten im Visual Studio-Debugger

Haltepunkte sind eine der wichtigsten Debugmethoden in der Toolbox Ihres Entwicklers. Sie legen Haltepunkte überall dort fest, wo Sie die Debuggerausführung anhalten möchten. Sie können z. B. den Status von Codevariablen anzeigen oder die Aufrufliste an einem bestimmten Haltepunkt anzeigen.  Wenn Sie versuchen, eine Warnung oder ein Problem während der Verwendung von Haltepunkten zu beheben, finden Sie weitere Informationen unter Beheben von [Haltepunkten im Visual Studio-Debugger](../debugger/troubleshooting-breakpoints.md).

> [!NOTE]
> Wenn Sie die Aufgabe oder das Problem kennen, die Sie zu lösen versuchen, aber Wissen, welche Art von Haltepunkt Sie verwenden möchten, finden Sie weitere Informationen unter [Suchen der Debugging-Aufgabe](../debugger/find-your-debugging-task.md#pause-running-code).

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a>Festlegen von Haltepunkten im Quellcode

Sie können einen Haltepunkt für jede beliebige Zeile mit ausführbarem Code festlegen. Im folgenden C-Code können Sie z. B. einen Haltepunkt `for` für die Variablendeklaration, die Schleife oder einen beliebigen Code innerhalb der `for` Schleife festlegen. Sie können keinen Haltepunkt für den Namespace oder die Klassendeklarationen oder für die Methodensignatur festlegen.

Um einen Haltepunkt im Quellcode festzulegen, klicken Sie auf den linken Rand neben einer Codezeile. Sie können auch die Zeile auswählen und **F9**drücken,**Breakpoint** **debugen** > auswählen oder mit der rechten Maustaste klicken und **Haltepunkt** > **einfügen**auswählen. Der Haltepunkt wird als roter Punkt am linken Rand angezeigt.

Für die meisten Sprachen, einschließlich C-, Haltepunkt und aktuelle Ausführungszeilen, werden automatisch hervorgehoben. Für C++-Code können Sie die Hervorhebung von Haltepunkt- und aktuellen Zeilen aktivieren, indem Sie **Tools** (oder **Debug**) > **Optionen** > **Debuggen** >  **markieren ganze Quellpunkte für Haltepunkte und aktuelle Anweisung (nur C++)** auswählen.

![Festlegen eines Haltepunkts](../debugger/media/basicbreakpoint.png "Grundlegender Haltepunkt")

Beim Debuggen wird die Ausführung am Haltepunkt angehalten, bevor der Code in dieser Zeile ausgeführt wird. Das Haltepunktsymbol zeigt einen gelben Pfeil an.

Am Haltepunkt im folgenden Beispiel ist `testInt` der Wert von immer noch 1. Der Wert hat sich also seit der Initialeinstellung der Variablen nicht geändert (auf den Wert 1 festgelegt), da die Anweisung in gelb noch nicht ausgeführt wurde.

![Haltepunktausführung beendet](../debugger/media/breakpointexecution.png "Breakpoint-Ausführung")

Wenn der Debugger am Haltepunkt angehalten wird, können Sie sich den aktuellen Status der App ansehen, einschließlich [variablen Werten](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) und der [Aufrufliste](../debugger/how-to-use-the-call-stack-window.md).

Hier sind einige allgemeine Anweisungen für die Arbeit mit Haltepunkten.

- Der Haltepunkt ist ein Umschalter. Sie können darauf klicken, **F9**drücken oder **den Breakpoint debug** > **toggle** verwenden, um ihn zu löschen oder wieder einzufügen.

- Um einen Haltepunkt zu deaktivieren, ohne ihn zu löschen, bewegen Sie den Mauszeiger darauf, oder klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Haltepunkt deaktivieren**aus. Deaktivierte Haltepunkte werden als leere Punkte am linken Rand oder im **Fenster Haltepunkte** angezeigt. Um einen Haltepunkt erneut zu aktivieren, zeigen Sie mit der Maus darauf oder klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Haltepunkt aktivieren**aus.

- Legen Sie Bedingungen und Aktionen fest, fügen Sie Beschriftungen hinzu und bearbeiten Sie ihn, oder exportieren Sie einen Haltepunkt, indem Sie mit der rechten Maustaste darauf klicken und den entsprechenden Befehl auswählen, oder bewegen Sie den Mauszeiger darüber, und wählen Sie das Symbol **Einstellungen** aus.

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a>Breakpoint-Aktionen und Tracepoints

Ein *Ablaufverfolgungspunkt* ist ein Haltepunkt, der eine Nachricht im **Ausgabefenster** druckt. Ein Tracepoint kann wie eine temporäre Ablaufverfolgungsanweisung in der Programmiersprache fungieren und die Ausführung von Code nicht anhalten. Sie erstellen einen Ablaufverfolgungspunkt, indem Sie im Fenster **Haltepunkteinstellungen** eine spezielle Aktion festlegen. Ausführliche Anweisungen finden Sie unter Verwenden von [Ablaufverfolgungspunkten im Visual Studio-Debugger](../debugger/using-tracepoints.md).

## <a name="breakpoint-conditions"></a>Haltepunktbedingungen

Sie können steuern, wann und wo ein Haltepunkt ausgeführt wird, indem Sie Bedingungen festlegen. Die Bedingung kann ein beliebiger gültiger Ausdruck sein, den der Debugger erkennt. Weitere Informationen zu gültigen Ausdrücken finden Sie unter [Expressions in the Debugger (Ausdrücke im Debugger)](../debugger/expressions-in-the-debugger.md).

**So legen Sie eine Haltepunktbedingung fest:**

1. Klicken Sie mit der rechten Maustaste auf das Haltepunktsymbol, und wählen Sie **Bedingungen**aus. Oder bewegen Sie den Mauszeiger über das Haltepunktsymbol, wählen Sie das Symbol **Einstellungen** aus, und wählen Sie dann Im Fenster **Haltepunkteinstellungen** **Bedingungen** aus.

   Sie können auch Bedingungen im Fenster **Haltepunkte** festlegen, indem Sie mit der rechten Maustaste auf einen Haltepunkt klicken und **Einstellungen**auswählen und dann **Bedingungen**auswählen.

   ![Haltepunkteinstellungen](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. Wählen Sie in der Dropdown-Liste **Bedingten Ausdruck**, **Trefferanzahl**oder **Filter**aus , und legen Sie den Wert entsprechend fest.

3. Wählen Sie **Schließen** oder drücken Sie+**Strg-Eingabe,** um das Fenster **Ctrl** **Haltepunkteinstellungen** zu schließen. Oder wählen Sie im Fenster **Haltepunkte** **OK** aus, um das Dialogfeld zu schließen.

Haltepunkte mit festgelegten Bedingungen **+** werden mit einem Symbol im Quellcode und in den **Breakpoints-Fenstern** angezeigt.

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Erstellen eines bedingten Ausdrucks

Wenn Sie **Bedingten Ausdruck**auswählen, können Sie zwischen zwei Bedingungen wählen: Ist **wahr** oder Wenn **geändert**. Wählen Sie **Ist wahr,** um zu unterbrechen, wenn der Ausdruck erfüllt ist, oder **Wenn geändert,** um zu brechen, wenn der Wert des Ausdrucks geändert wurde.

Im folgenden Beispiel wird der Haltepunkt nur `testInt` erreicht, wenn der Wert **von 4**:

![Haltepunktbedingung lautet "true"](../debugger/media/breakpointconditionistrue.png "Breakpoint ist wahr")

Im folgenden Beispiel wird der Haltepunkt nur `testInt` dann erreicht, wenn sich der Wert von Änderungen ändert:

![Haltepunkt Bei Änderung](../debugger/media/breakpointwhenchanged.png "Haltepunkt Bei Änderung")

Wenn Sie eine Haltepunktbedingung mit ungültiger Syntax festlegen, wird sofort eine Warnmeldung angezeigt. Wenn Sie eine Haltepunktbedingung mit gültiger Syntax aber ungültiger Semantik angeben, wird beim ersten Erreichen des Haltepunkts eine Warnmeldung angezeigt. In beiden Fällen wird der Debugger unterbrochen, wenn er auf den ungültigen Haltepunkt trifft. Der Haltepunkt wird nur übersprungen, wenn die Bedingung gültig ist mit `false`bewertet wird.

>[!NOTE]
>Das Verhalten des Felds **Bei Änderung** unterscheidet sich je nach Programmiersprache.
>- Bei systemeigenem Code betrachtet der Debugger die erste Auswertung der Bedingung nicht als Änderung, sodass der Haltepunkt bei der ersten Auswertung nicht erreicht wird.
>- Bei verwaltetem Code trifft der Debugger bei der ersten Auswertung den Haltepunkt, nachdem **die Option "Wenn geändert"** ausgewählt wurde.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Verwenden von Objekt-IDs in bedingten Ausdrücken (nur C- und F-Code)

 Es gibt Zeiten, in denen Sie das Verhalten eines bestimmten Objekts beobachten möchten. Sie können z. B. herausfinden, warum ein Objekt mehr als einmal in eine Auflistung eingefügt wurde. In C# und F# können Sie Objekt-IDs für bestimmte Instanzen von [Verweistypen](/dotnet/csharp/language-reference/keywords/reference-types) erstellen und in Haltepunktbedingungen verwenden. Die Objekt-ID wird von den Debugdiensten der CLR (Common Language Runtime) generiert und dem Objekt zugeordnet.

**So erstellen Sie eine Objekt-ID:**

1. Legen Sie einen Haltepunkt im Code an einer Stelle fest, nachdem das Objekt erstellt wurde.

2. Beginnen Sie mit dem Debuggen, und wenn die Ausführung am Haltepunkt angehalten wird, wählen Sie**Windows** > **Locals** oder **Alt**+**4** **debuggen** > aus, um das **Locals-Fenster** zu öffnen.

   Suchen Sie die bestimmte Objektinstanz im **Fenster "Locals",** klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Objekt-ID erstellen**aus.

   Im Fenster **$** **"Locals"** sollte eine Pluszahl angezeigt werden. Dies ist die Objekt-ID.

3. Fügen Sie an dem Punkt, den Sie untersuchen möchten, einen neuen Haltepunkt hinzu. z. B. wenn das Objekt der Auflistung hinzugefügt werden soll. Klicken Sie mit der rechten Maustaste auf den Haltepunkt, und wählen Sie **Bedingungen** aus.

4. Verwenden Sie die Objekt-ID im Feld **Bedingter Ausdruck**. `item` Wenn die Variable z. B. das Objekt ist, das der Auflistung hinzugefügt werden soll, wählen Sie Ist **true** und geben Sie das Element == n \< **\<>** ein, wobei n> die Objekt-ID-Nummer ist.

   Die Ausführung wird an dem Punkt unterbrochen, an dem dieses Objekt der Auflistung hinzugefügt werden soll.

   Um die Objekt-ID zu löschen, klicken Sie mit der rechten Maustaste auf die Variable im Fenster **"Locals",** und wählen Sie **Objekt-ID löschen**aus.

> [!NOTE]
> Objekt-IDs erstellen Weak-Verweise und verhindern nicht, dass das Objekt in die Garbage Collection aufgenommen wird. Sie gelten nur für die aktuelle Debugsitzung.

### <a name="set-a-hit-count-condition"></a>Festlegen einer Trefferanzahlbedingung

Wenn Sie vermuten, dass sich eine Schleife im Code nach einer bestimmten Anzahl von Iterationen falsch verhält, können Sie einen Haltepunkt festlegen, um die Ausführung nach dieser Anzahl von Treffern zu beenden, anstatt wiederholt **F5** drücken zu müssen, um diese Iteration zu erreichen.

Wählen Sie unter **Bedingungen** im Fenster **Haltepunkteinstellungen** die Option **Trefferanzahl**aus, und geben Sie dann die Anzahl der Iterationen an. Im folgenden Beispiel wird der Haltepunkt auf jede andere Iteration festgelegt:

![Punkttrefferanzahl](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="set-a-filter-condition"></a>Festlegen einer Filterbedingung

Sie können einen Haltepunkt so einschränken, dass dieser nur auf bestimmten Geräten oder in angegebenen Prozesse und Threads aktiviert wird.

Wählen Sie unter **Bedingungen** im Fenster **Haltepunkteinstellungen** **filteraus,** und geben Sie dann einen oder mehrere der folgenden Ausdrücke ein:

- MachineName = "name"
- ProcessId = value
- ProcessName = "name"
- ThreadId = value
- ThreadName = "name"

Schließen Sie Zeichenfolgewerte in doppelte Anführungszeichen ein. Sie können Klauseln mit `&` (AND), `||` (OR), `!` (NOT), und Klammern kombinieren.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Festlegen von Funktionshaltepunkten

Sie können die Ausführung unterbrechen, wenn eine Funktion aufgerufen wird. Dies ist z. B. nützlich, wenn Sie den Funktionsnamen kennen, aber nicht seinen Speicherort. Es ist auch nützlich, wenn Sie Funktionen mit dem gleichen Namen haben und sie alle unterbrechen möchten (z. B. überladene Funktionen oder Funktionen in verschiedenen Projekten).

**So legen Sie einen Funktionshaltepunkt fest:**

1. Wählen Sie **Debug** > **New Breakpoint** > **Function Breakpoint**, oder drücken Sie **Alt**+**F9** > **Strg**+**B**.

   Sie können auch **Den Neuen** > **Funktionshaltepunkt** im Fenster **Haltepunkte** auswählen.

1. Geben Sie im Dialogfeld **Neue Funktion Breakpoint** den Funktionsnamen in das Feld **Funktionsname** ein.

   So schränken Sie die Funktionsspezifikation ein:

   - Verwenden Sie den vollqualifizierten Funktionsnamen.

     Beispiel: `Namespace1.ClassX.MethodA()`

   - Fügen Sie die Parametertypen einer überladenen Funktion hinzu.

     Beispiel: `MethodA(int, string)`

   - Verwenden Sie das Symbol '!', um das Modul anzugeben.

     Beispiel: `App1.dll!MethodA`

   - Verwenden Sie den Kontextoperator in systemeigenem C++.

     `{function, , [module]} [+<line offset from start of method>]`

     Beispiel: `{MethodA, , App1.dll}+2`

1. Wählen Sie in der Dropdown-Liste **Sprache** die Sprache der Funktion aus.

1. Wählen Sie **OK** aus.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Festlegen eines Funktionshaltepunkts mithilfe einer Speicheradresse (nur natives C++)
 Sie können die Adresse eines Objekts verwenden, um einen Funktionshaltepunkt für eine Methode festzulegen, die von einer bestimmten Instanz einer Klasse aufgerufen wird.  Wenn Sie z. B. `my_class`ein adressierbares Objekt vom `my_method` Typ angeben, können Sie einen Funktionshaltepunkt für die Methode festlegen, die instanziiert aufruft.

1. Legen Sie einen Haltepunkt irgendwo fest, nachdem die Instanz der Klasse instanziiert wurde.

2. Suchen Sie die Adresse der `0xcccccccc`Instanz (z. B. ).

3. Wählen Sie **Debug** > **New Breakpoint** > **Function Breakpoint**, oder drücken Sie **Alt**+**F9** > **Strg**+**B**.

4. Fügen Sie dem Feld **Funktionsname** Folgendes hinzu, und wählen Sie die **Sprache C++aus.**

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>Festlegen von Datenhaltepunkten (.NET Core 3.0 oder höher)

Datenhaltepunkte unterbrechen die Ausführung, wenn sich die Eigenschaft eines bestimmten Objekts ändert.

**So legen Sie einen Datenhaltepunkt fest**

1. Beginnen Sie in einem .NET Core-Projekt mit dem Debuggen, und warten Sie, bis ein Haltepunkt erreicht ist.

2. Klicken Sie im Fenster **Autos**, **Watch**oder **Locals** mit der rechten Maustaste auf eine Eigenschaft, und wählen Sie **Aufbruch aus, wenn sich** der Wert im Kontextmenü ändert.

    ![Verwalteter Daten-Breakpoint](../debugger/media/managed-data-breakpoint.png "Verwalteter Daten-Breakpoint")

Datenhaltepunkte in .NET Core funktionieren nicht für:

- Eigenschaften, die im Fenster QuickInfo, Locals, Autos oder Watch nicht erweiterbar sind
- Statische Variablen
- Klassen mit dem DebuggerTypeProxy-Attribut
- Felder innerhalb von Strukturen

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Festlegen von Datenhaltepunkten (nur natives C++)

 Datenhaltepunkte unterbrechen die Ausführung, wenn sich ein Wert ändert, der an einer angegebenen Speicheradresse gespeichert ist. Wenn der Wert ausgelesen jedoch nicht geändert wird, wird die Ausführung nicht unterbrochen.

**So legen Sie einen Datenhaltepunkt fest:**

1. Starten Sie in einem C++-Projekt mit dem Debuggen, und warten Sie, bis ein Haltepunkt erreicht ist. Wählen Sie im **Menü Debug die** Option Neuer Breakpoint-Daten-Breakpoint **New Breakpoint** > **Data Breakpoint** aus.

    Sie können auch **Neue** > **Datenhaltepunkte** im **Fenster Haltepunkte** auswählen oder mit der rechten Maustaste auf ein Element im Fenster **Autos**, **Watch**oder **Locals** klicken und Pause auswählen, wenn sich der Wert im Kontextmenü **ändert.**

2. Geben Sie im Feld **Adresse** eine Speicheradresse oder einen Ausdruck ein, der zu einer Speicheradresse ausgewertet wird. Geben Sie beispielsweise `&avar` ein, um die Ausführung bei einer Änderung des Inhalts der Variable `avar` zu unterbrechen.

3. Geben Sie im Feld **Byteanzahl** die Anzahl der Bytes an, die der Debugger überwachen soll. Wenn Sie beispielsweise **4**auswählen, überwacht der Debugger vier Bytes ab `&avar` und unterbricht, wenn eines dieser Bytes seinen Wert ändert.

Datenhaltepunkte funktionieren unter den folgenden Bedingungen nicht:
- Ein Prozess, der nicht gedebuggt wird, wird in einen Speicherbereich geschrieben.
- Der Speicherbereich wird von mindestens zwei Prozessen gemeinsam verwendet.
- Der Speicherort wird innerhalb des Kernels aktualisiert. Wenn z. B. der Speicher an `ReadFile` die 32-Bit-Windows-Funktion übergeben wird, wird der Speicher aus dem Kernelmodus aktualisiert, sodass der Debugger das Update nicht aufbricht.
- Wobei der Watch-Ausdruck größer als 4 Byte auf 32-Bit-Hardware und 8 Byte auf 64-Bit-Hardware ist. Dies ist eine Einschränkung der x86-Architektur.

> [!NOTE]
> - Datenhaltepunkte hängen von bestimmten Speicheradressen ab. Die Adresse einer Variablen ändert sich von einer Debugsitzung zur nächsten, sodass Datenhaltepunkte am Ende jeder Debugsitzung automatisch deaktiviert werden.
>
> - Wenn Sie einen Datenhaltepunkt bei einer lokalen Variable festlegen, bleibt der Haltepunkt aktiviert, wenn die Funktion beendet wird, die Speicheradresse ist jedoch nicht mehr gültig, und das Verhalten des Haltepunkts ist unvorhersehbar. Wenn Sie einen Datenhaltepunkt für eine lokale Variable festlegen, sollten Sie den Haltepunkt löschen oder deaktivieren, bevor die Funktion endet.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Verwalten von Haltepunkten im Haltepunktefenster

 Sie können das Fenster **Haltepunkte** verwenden, um alle Haltepunkte in Ihrer Lösung anzuzeigen und zu verwalten. Dieser zentrale Speicherort ist besonders hilfreich in einer großen Lösung oder für komplexe Debugszenarios, in denen Haltepunkte kritisch sind.

Im Fenster **Haltepunkte** können Sie Haltepunkte suchen, sortieren, filtern, aktivieren/deaktivieren oder löschen. Sie können auch Bedingungen und Aktionen festlegen oder eine neue Funktion oder einen neuen Datenhaltepunkt hinzufügen.

Um das **Fenster Haltepunkte** zu öffnen, wählen Sie**Windows-Haltepunkte****Windows** >  **debuggen** > aus , oder drücken Sie **Alt**+**F9** oder **Strg**+**Alt**+**B**.

![Breakpoints-Fenster](../debugger/media/breakpointswindow.png ""Haltepunkte" (Fenster)")

Um die Spalten auszuwählen, die im Fenster **Haltepunkte** angezeigt werden sollen, wählen Sie **Spalten anzeigen**aus. Wählen Sie eine Spaltenüberschrift aus, um die Haltepunktliste nach dieser Spalte zu sortieren.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Haltepunktbezeichnungen
Sie können Beschriftungen verwenden, um die Liste der Haltepunkte im Fenster **Haltepunkte** zu sortieren und zu filtern.

1. Um eine Beschriftung zu einem Haltepunkt hinzuzufügen, klicken Sie mit der rechten Maustaste auf den Haltepunkt im Quellcode oder im **Fenster Haltepunkte,** und wählen Sie dann **Beschriftungen bearbeiten**aus. Fügen Sie eine neue Bezeichnung hinzu, oder wählen Sie eine vorhandene Aus- und stelle dann **OK**aus.
2. Sortieren Sie die Haltepunktliste im Fenster **Haltepunkte,** indem Sie die **Spaltenüberschriften Beschriftungen**, **Bedingungen**oder andere Spaltenüberschriften auswählen. Sie können die anzuzeigenden Spalten auswählen, indem **Sie** Spalten in der Symbolleiste anzeigen auswählen.

### <a name="export-and-import-breakpoints"></a>Exportieren und Importieren von Haltepunkten
 Um den Status und die Position Ihrer Haltepunkte zu speichern oder freizugeben, können Sie sie exportieren oder importieren.

- Um einen einzelnen Haltepunkt in eine XML-Datei zu exportieren, klicken Sie mit der rechten Maustaste auf den Haltepunkt im Quellcode- oder **Breakpoints-Fenster,** und wählen Sie **Ausgewählte exportieren** oder **exportieren**aus. Wählen Sie einen Exportspeicherort aus, und wählen Sie dann **Speichern**aus. Der Standardspeicherort ist der Lösungsordner.
- Um mehrere Haltepunkte zu exportieren, wählen Sie im Fenster **Haltepunkte** die Felder neben den Haltepunkten aus, oder geben Sie Suchkriterien in das Feld **Suchen** ein. Wählen Sie alle Haltepunkte exportieren aus, **die dem aktuellen Suchkriteriensymbol entsprechen,** und speichern Sie die Datei.
- Um alle Haltepunkte zu exportieren, deaktivieren Sie alle Felder, und lassen Sie das **Feld Suchen** leer. Wählen Sie alle Haltepunkte exportieren aus, **die dem aktuellen Suchkriteriensymbol entsprechen,** und speichern Sie die Datei.
- Um Haltepunkte zu importieren, wählen Sie im Fenster **Haltepunkte** die **Haltepunkte aus einem Dateisymbol** importieren aus, navigieren Sie zum Speicherort der XML-Datei, und wählen Sie **Öffnen**aus.

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a>Festlegen von Haltepunkten aus Debuggerfenstern

Sie können auch Haltepunkte aus den Fenster **Aufruflisten** und **Demontage-Debugger** festlegen.

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Festlegen eines Haltepunkts im Fenster Aufrufliste

 Um die Anweisung oder Zeile zu unterbrechen, zu der eine aufrufende Funktion zurückkehrt, können Sie im **Fenster Aufrufliste** einen Haltepunkt festlegen.

**So legen Sie einen Haltepunkt im Fenster Aufrufliste fest:**

1. Um das **Fenster Aufrufliste zu** öffnen, müssen Sie während des Debuggens angehalten werden. Wählen Sie **Debug** > **Debug Windows** > **Call Stack**, oder drücken Sie **Strg**+**Alt**+**C**.

2. Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf die aufrufende Funktion, und wählen Sie **Breakpoint** > **Insert Breakpoint**aus , oder drücken Sie **F9**.

   Neben dem Funktionsaufrufnamen wird am linken Rand der Aufrufliste ein Haltepunktsymbol angezeigt.

Der Aufruflistenhaltepunkt wird im **Fenster Breakpoints** als Adresse mit einem Speicherort angezeigt, der der nächsten ausführbaren Anweisung in der Funktion entspricht.

Der Debugger bricht an der Anweisung.

Weitere Informationen zur Aufrufliste finden Sie unter [How to: Use the Call Stack Window (Vorgehensweise: Verwenden des Fensters „Aufrufliste“)](../debugger/how-to-use-the-call-stack-window.md).

Informationen zum visuellen Ablaufen von Haltepunkten während der Codeausführung finden Sie [unter Zuordnen von Methoden in der Aufrufliste während des Debuggens](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Festlegen eines Haltepunkts im Demontagefenster

1. Um das **Demontagefenster** zu öffnen, müssen Sie während des Debuggens angehalten werden. Wählen Sie**Windows** > **Disassembly** **debuggen** > , oder drücken Sie **Alt**+**8**.

2. Klicken Sie im Fenster **Demontage** auf den linken Rand der Anweisung, an der Sie brechen möchten. Sie können es auch auswählen und **F9**drücken oder mit der rechten Maustaste klicken und **Haltepunkt** > **einfügen Breakpoint**auswählen.

## <a name="see-also"></a>Weitere Informationen

- [Was bedeutet „Debuggen“?](../debugger/what-is-debugging.md)
- [Schreiben von besserem C-Code mithilfe von Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Erster Blick auf das Debuggen](../debugger/debugger-feature-tour.md)
- [Beheben von Haltepunkten im Visual Studio-Debugger](../debugger/troubleshooting-breakpoints.md)
