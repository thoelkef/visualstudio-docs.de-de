---
title: Verwenden Sie Haltepunkte im Debugger | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 10/15/2018
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
ms.openlocfilehash: 3f9150a815f424c0b4a7bfe5f2e92ea7cd424ddb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62902106"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Verwenden von Haltepunkten in Visual Studio-debugger
Haltepunkte sind eines der wichtigsten Debugverfahren in der Toolbox für Entwickler. Sie können Haltepunkte festlegen, wo der Debugger die Ausführung angehalten werden soll. Beispielsweise empfiehlt es sich um den Status der Codevariablen oder sehen Sie sich die Aufrufliste an einem bestimmten Haltepunkt. Wenn Sie zum ersten Mal versuchen, Code zu debuggen, sollten Sie [Debuggen für Einsteiger](../debugger/debugging-absolute-beginners.md) lesen, bevor Sie diesen Artikel durchgehen.

## <a name="BKMK_Overview"></a> Setzen Sie Haltepunkte im Quellcode
 Sie können einen Haltepunkt für jede beliebige Zeile mit ausführbarem Code festlegen. Z. B. im folgenden C#-Code, Sie können einen Haltepunkt festlegen der Deklaration von Variablen, die `for` -Schleife oder Code innerhalb der `for` Schleife. Sie können nicht auf den Namespace oder den Klassendeklarationen oder die Signatur der Methode einen Haltepunkt festlegen.

 Klicken Sie in den linken Rand neben einer Codezeile, zum Festlegen eines Haltepunkts im Quellcode. Sie können auch auswählen, die Zeile, und drücken Sie **F9**Option **Debuggen** > **Haltepunkt ein/aus**, oder mit der rechten Maustaste, und wählen Sie **Haltepunkt**  >  **Haltepunkt einfügen**. Der Haltepunkt wird als ein roter Punkt am linken Rand angezeigt.

In C# Code, der Haltepunkt und der aktuellen Ausführung Zeilen werden automatisch hervorgehoben. Für C++ Code, die Sie aktivieren können, auf die Herausarbeitung der Haltepunkt und die aktuellen Zeilen dazu **Tools** (oder **Debuggen**) > **Optionen**  >  **Debuggen** >  **bei Haltepunkten und aktueller Anweisung gesamte Quellcodezeile markieren (C++ nur)**.

 ![Festlegen eines Haltepunkts](../debugger/media/basicbreakpoint.png "grundlegende Haltepunkt")

 Wenn Sie Debuggen, hält die Ausführung am Haltepunkt, bevor der Code in dieser Zeile ausgeführt wird. Das Haltepunktsymbol wird einen gelben Pfeil.

 Die Ausführung am Haltepunkt in der folgenden Beispiel wird der Wert des `testInt` ist immer noch 1.

 ![Haltepunktausführung beendet](../debugger/media/breakpointexecution.png "haltepunktausführung")

 Wenn der Debugger am Haltepunkt beendet wurde, können Sie den aktuellen Status der app, einschließlich der Variablenwerte und die Aufrufliste anzeigen. Weitere Informationen zur Aufrufliste finden Sie unter [Vorgehensweise: Verwenden Sie das Fenster "Aufrufliste"](../debugger/how-to-use-the-call-stack-window.md).

- Der Haltepunkt ist eine Umschaltoption. Sie klicken Sie darauf, drücken Sie die **F9**, oder verwenden Sie **Debuggen** > **Haltepunkt ein/aus** zu löschen oder erneut eingefügt werden.

- Um einen Haltepunkt deaktivieren, ohne ihn zu löschen, zeigen Sie auf oder Maustaste, und wählen Sie **Haltepunkt deaktivieren**. Deaktivierte Haltepunkte, die als leere Punkte am linken Rand angezeigt werden oder die **Haltepunkte** Fenster. Um einen Haltepunkt wieder zu aktivieren, zeigen Sie auf oder der rechten Maustaste darauf, und wählen Sie **Haltepunkt aktivieren**.

- Festlegen von Bedingungen und Aktionen, hinzufügen und Bezeichnungen bearbeiten oder einen Haltepunkt zu exportieren, indem sie und den entsprechenden Befehl auswählen oder mit dem Mauszeiger auf ihn auswählen der **Einstellungen** Symbol.

## <a name="BKMK_Set_a_breakpoint_in_a_function"></a> Legen Sie Haltepunkte vom Debugger windows

Sie können auch festlegen, Haltepunkte aus der **Aufrufliste** und **Disassembly** Debuggerfenster.

### <a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a> Festlegen eines Haltepunkts im Aufruflistenfenster

 Um bei der Anweisung oder der Zeile, die eine aufrufende Funktion zurückkehrt, unterbrechen, können Sie einen Haltepunkt festlegen, der **Aufrufliste** Fenster.

**So legen einen Haltepunkt in das Fenster "Aufrufliste":**

1. Zum Öffnen der **Aufrufliste** Fenster Sie während des Debuggens angehalten werden müssen. Wählen Sie **Debuggen** > **Windows** > **Aufrufliste**, oder drücken Sie **STRG** + **Alt**+**C**.

2. In der **Aufrufliste** mit der rechten Maustaste auf die Aufruffunktion, und wählen Sie **Haltepunkt** > **Haltepunkt einfügen**, oder drücken Sie **F9**.

   Ein Haltepunktsymbol wird neben dem funktionsaufrufnamen am linken Rand der Aufrufliste angezeigt.

Wird der aufruflistenhaltepunkt angezeigt, der **Haltepunkte** -Fenster als eine Adresse mit Speicherort, der der nächsten ausführbaren Anweisung der Funktion entspricht.

Der Debugger bei der Anweisung.

Weitere Informationen zur Aufrufliste finden Sie unter [Vorgehensweise: Verwenden Sie das Fenster "Aufrufliste"](../debugger/how-to-use-the-call-stack-window.md).

Zur visuellen nachverfolgung während der codeausführung, finden Sie unter [Zuordnen von Methoden in der Aufrufliste beim Debuggen](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Festlegen eines Haltepunkts im Disassemblyfenster

1. Zum Öffnen der **Disassembly** Fenster Sie während des Debuggens angehalten werden müssen. Wählen Sie **Debuggen** > **Windows** > **Disassembly**, oder drücken Sie **Alt** + **8**.

2. In der **Disassembly** Fenster, klicken Sie in den linken Rand der Anweisung, die Sie unterbrechen möchten. Sie können auch auswählen, und drücken Sie die **F9**, oder mit der rechten Maustaste, und wählen Sie **Haltepunkt** > **Haltepunkt einfügen**.

## <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> Festlegen von Haltepunkten-Funktion

  Sie können die Ausführung unterbrechen, wenn eine Funktion aufgerufen wird.

**So legen Sie einen Funktionshaltepunkt fest:**

1. Wählen Sie **Debuggen** > **Neuer Haltepunkt** > **Funktions-Haltepunkts**, oder drücken Sie **Alt** + **F9** > **STRG**+**B**.

   Sie können auch auswählen, **neu** > **Funktions-Haltepunkts** in die **Haltepunkte** Fenster.

1. In der **neue Funktions-Haltepunkts** Dialogfeld Geben Sie den Funktionsnamen in der **Funktionsnamen** Feld.

   Um die Funktionsspezifikation einzugrenzen:

   - Verwenden Sie den vollqualifizierten Funktionsnamen.

     Beispiel: `Namespace1.ClassX.MethodA()`

   - Fügen Sie die Parametertypen einer überladenen Funktion hinzu.

     Beispiel: `MethodA(int, string)`

   - Verwenden der "!" Symbol für das Modul angeben.

     Ein Beispiel: `App1.dll!MethodA`

   - Verwenden Sie den Kontextoperator in systemeigenem C++.

     `{function, , [module]} [+<line offset from start of method>]`

     Ein Beispiel: `{MethodA, , App1.dll}+2`

1. In der **Sprache** Dropdownliste, wählen Sie die Sprache der Funktion.

1. Klicken Sie auf **OK**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Festlegen eines Funktionshaltepunkts mit einer Speicheradresse (nur systemeigener C++)
 Sie können die Adresse eines Objekts verwenden, einen Funktionshaltepunkt für eine Methode namens von einer bestimmten Instanz einer Klasse festlegen.  Angenommen, ein adressierbares Objekt des Typs `my_class`, Sie können eine Funktions-Haltepunkts festlegen, auf die `my_method` -Methode, die Aufrufe Instanz.

1. Legen Sie einen Haltepunkt an einer beliebigen Stelle, nachdem die Instanz der Klasse instanziiert wird.

2. Suchen Sie die Adresse der Instanz (z. B. `0xcccccccc`).

3. Wählen Sie **Debuggen** > **Neuer Haltepunkt** > **Funktions-Haltepunkts**, oder drücken Sie **Alt** + **F9** > **STRG**+**B**.

4. Fügen Sie den folgenden der **Funktionsnamen** , und wählen Sie **C++** Sprache.

    ```C++
    ((my_class *) 0xcccccccc)->my_method
    ```

::: moniker range=">= vs-2019"

## <a name="BKMK_set_a_data_breakpoint_managed"></a>Festlegen von Datenhaltepunkten (.NET Core 3.0 oder höher)

Datenhaltepunkte unterbrechen die Ausführung, wenn ein bestimmtes Objekt der Eigenschaft ändert.

**Festlegen ein Haltepunkts für Daten**

1. In einem .NET Core-Projekt mit dem beginnen Sie Debuggen, und warten Sie, bis ein Haltepunkt erreicht wird.

2. In der **"Auto"**, **Watch**, oder **"lokal"** mit der rechten Maustaste auf eine Eigenschaft, und wählen Sie **unterbrechen, wenn der Wert ändert** im Kontextmenü.

    ![Verwaltete Datenhaltepunkt](../debugger/media/managed-data-breakpoint.png "verwaltet Datenhaltepunkt")

Datenhaltepunkte in .NET Core funktioniert nicht für:

- Eigenschaften, die nicht in der QuickInfo, "lokal", "Auto", erweiterbar sind oder Überwachung (Fenster)
- Statische Variablen
- Klassen mit dem DebuggerTypeProxy-Attribut
- Felder in Strukturen 

::: moniker-end

## <a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Festlegen von Datenhaltepunkten (nur systemeigener C++)

 Datenhaltepunkte unterbrechen die Ausführung, wenn ein Wert, der an einer angegebenen Adresse arbeitsspeicheränderungen gespeichert. Wenn der Wert ausgelesen jedoch nicht geändert wird, wird die Ausführung nicht unterbrochen.

**Um einen Datenhaltepunkt festzulegen:**

1. In einem C++-Projekt mit dem beginnen Sie Debuggen, und warten Sie, bis ein Haltepunkt erreicht wird. Auf der **Debuggen** Menü wählen **Neuer Haltepunkt** > **Datenhaltepunkt**

    Sie können auch auswählen, **neu** > **Datenhaltepunkt** in die **Haltepunkte** Fenster oder auf ein Element in der **"Auto"**, **Watch**, oder **"lokal"** Fenster, und wählen **unterbrechen, wenn der Wert ändert**im Kontextmenü.

2. Geben Sie im Feld **Adresse** eine Speicheradresse oder einen Ausdruck ein, der als Speicheradresse ausgewertet wird. Geben Sie beispielsweise `&avar` ein, um die Ausführung bei einer Änderung des Inhalts der Variable `avar` zu unterbrechen.

3. Geben Sie im Feld **Byteanzahl** die Anzahl der Bytes an, die der Debugger überwachen soll. Wenn Sie beispielsweise **4**auswählen, überwacht der Debugger vier Bytes ab `&avar` und unterbricht, wenn eines dieser Bytes seinen Wert ändert.

Datenhaltepunkte funktionieren nicht unter den folgenden Bedingungen:
- Ein Prozess, der nicht gedebuggt wird, wird in einen Speicherbereich geschrieben.
- Der Speicherbereich wird von mindestens zwei Prozessen gemeinsam verwendet.
- Der Speicherort wird innerhalb des Kernels aktualisiert. Wenn Speicher an der 32-Bit-Windows übergeben wird z. B. `ReadFile` -Funktion, der Speicher vom Kernelmodus, damit das Update der Debugger unterbricht aktualisiert.

>[!NOTE]
>- Datenhaltepunkte richten sich nach spezifischen Speicheradressen. Die Adresse einer Variablen ändert sich von einer Debugsitzung zur nächsten, sodass Datenhaltepunkte am Ende einer Debugsitzung automatisch deaktiviert werden.
>
>- Wenn Sie einen Datenhaltepunkt bei einer lokalen Variable festlegen, bleibt der Haltepunkt aktiviert, wenn die Funktion beendet wird, die Speicheradresse ist jedoch nicht mehr gültig, und das Verhalten des Haltepunkts ist unvorhersehbar. Wenn Sie einen Datenhaltepunkt auf eine lokale Variable festlegen, sollten Sie löschen oder deaktivieren diesen vor dem Ende der Funktion.

## <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Verwalten von Haltepunkten im Haltepunktefenster

 Sie können die **Haltepunkte** Fenster anzeigen und Verwalten aller Haltepunkte in der Projektmappe. Dieser zentrale Speicherort ist besonders hilfreich, in großen Projektmappen oder komplexen Debugszenarios, in denen Haltepunkte wichtig sind.

In der **Haltepunkte** Fenster, Sie können zu suchen, sortieren, filtern, aktivieren/deaktivieren oder Löschen von Breakpoints. Sie können auch Bedingungen und Aktionen festlegen oder eine neue Funktion oder ein Datenhaltepunkt hinzufügen.

Zum Öffnen der **Haltepunkte** wählen Sie im Fenster **Debuggen** > **Windows** > **Haltepunkte**, oder drücken Sie  **ALT**+**F9** oder **STRG**+**Alt**+**B**.

![Fenster "Breakpoints"](../debugger/media/breakpointswindow.png "Fenster \"Breakpoints\"")

Anzuzeigende Spalten auswählen der **Haltepunkte** wählen Sie im Fenster **Spalten einblenden**. Wählen Sie eine Spaltenüberschrift, um die Liste der Haltepunkte nach dieser Spalte zu sortieren.

### <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Haltepunktbezeichnungen
Sie können Bezeichnungen zu sortieren und Filtern Sie die Liste von Haltepunkten in der **Haltepunkte** Fenster.

1. Um eine Bezeichnung einem Haltepunkt hinzuzufügen, Maustaste den Breakpoint im Quellcode oder die **Haltepunkte** Fenster, und wählen Sie dann **Bezeichnungen bearbeiten**. Eine neue Bezeichnung hinzufügen oder ein vorhandenes Zertifikat, und wählen Sie dann **OK**.
2. Sortiert die Haltepunktliste in der **Haltepunkte** Fenster durch Auswahl der **Bezeichnungen**, **Bedingungen**, oder andere Spaltenüberschriften. Sie können auswählen, die Spalten für die anzuzeigenden dazu **Spalten einblenden** auf der Symbolleiste.

### <a name="export-and-import-breakpoints"></a>Exportieren und Importieren von Haltepunkten
 Sie können zum Speichern oder freigeben, den Status und den Speicherort der Haltepunkte, exportieren oder importieren.

- Um einen einzelnen Breakpoint in einer XML-Datei zu exportieren, Maustaste den Breakpoint im Quellcode oder **Haltepunkte** , und wählen **exportieren** oder **Exportieren ausgewählter**. Wählen Sie einen Speicherort exportieren, und wählen Sie dann **speichern**. Der Standardspeicherort ist der Projektmappenordner.
- So exportieren Sie mehrere Haltepunkte festlegen, in der **Haltepunkte** Fenster, aktivieren Sie die Kontrollkästchen neben den Breakpoints, oder geben Sie Suchkriterien in der **Suche** Feld. Wählen Sie die **exportieren Sie alle Haltepunkte mit den aktuellen Suchkriterien übereinstimmen** Symbol, und speichern Sie die Datei.
- Um alle Haltepunkte exportieren möchten, deaktivieren Sie alle Felder aus, und lassen Sie die **Suche** Feld leer. Wählen Sie die **exportieren Sie alle Haltepunkte mit den aktuellen Suchkriterien übereinstimmen** Symbol, und speichern Sie die Datei.
- Zum Importieren von Haltepunkten, in der **Haltepunkte** wählen Sie im Fenster der **Haltepunkte aus einer Datei importieren** Symbol, um den Speicherort der XML-Datei navigieren, und wählen **öffnen**.

## <a name="breakpoint-conditions"></a>Haltepunktbedingungen
 Sie können steuern, wann und wo ein Haltepunkt ausgeführt wird, indem Sie Bedingungen festlegen. Die Bedingung kann jeder gültige Ausdruck sein, den der Debugger erkennt. Weitere Informationen zu gültigen Ausdrücken finden Sie unter [Expressions in the Debugger (Ausdrücke im Debugger)](../debugger/expressions-in-the-debugger.md).

**Um eine Bedingung für Haltepunkt festzulegen:**

1. Mit der rechten Maustaste in des Haltepunkt-Symbols, und wählen Sie **Bedingungen**. Oder zeigen Sie auf das Haltepunktsymbol, wählen die **Einstellungen** Symbol, und wählen Sie dann **Bedingungen** in die **Haltepunkteinstellungen** Fenster.

   Sie können auch Bedingungen festlegen, der **Haltepunkte** Fenster, indem Sie mit der rechten Maustaste eines Haltepunkts, und wählen **Einstellungen**, und wählen Sie dann **Bedingungen**.

   ![Haltepunkteinstellungen](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. Wählen Sie in der Dropdown-Liste **Bedingungsausdruck**, **Trefferanzahl**, oder **Filter**, und legen Sie den Wert entsprechend.

3. Wählen Sie **schließen** , oder drücken Sie **STRG**+**EINGABETASTE** schließen die **Haltepunkteinstellungen** Fenster. Alternativ wählen Sie in der **Haltepunkte** wählen Sie im Fenster **OK** um das Dialogfeld zu schließen.

Haltepunkte mit Bedingungen werden mit einem **+** Symbol im Quellcode und **Haltepunkte** Windows.

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="conditional-expression"></a>Bedingter Ausdruck

Bei der Auswahl **Bedingungsausdruck**, Sie können zwischen zwei Bedingungen auswählen: **Ist "true"** oder **Änderung**. Wählen Sie **ist "true"** zu unterbrechen, wenn der Ausdruck erfüllt ist, oder **Änderung** zu unterbrechen, wenn der Wert des Ausdrucks geändert hat.

 Im folgenden Beispiel wird der Haltepunkt erreicht nur, wenn der Wert des `testInt` ist **4**:

 ![Haltepunktbedingung wahr ist](../debugger/media/breakpointconditionistrue.png "Haltepunkt ist \"true\"")

 Im folgenden Beispiel wird der Haltepunkt erreicht nur, wenn der Wert des `testInt` Änderungen:

 ![Haltepunkt bei Änderung](../debugger/media/breakpointwhenchanged.png "Haltepunkt Wenn geändert")

 Wenn Sie eine Haltepunktbedingung mit ungültiger Syntax festlegen, wird sofort eine Warnmeldung angezeigt. Wenn Sie eine Haltepunktbedingung mit gültiger Syntax aber ungültiger Semantik angeben, wird beim ersten Erreichen des Haltepunkts eine Warnmeldung angezeigt. In jedem Fall unterbricht der Debugger auf, wenn er den ungültigen Breakpoint erreicht. Der Haltepunkt wird nur übersprungen, wenn die Bedingung gültig ist mit `false`bewertet wird.

 >[!NOTE]
 >Das Verhalten des Felds **Bei Änderung** unterscheidet sich je nach Programmiersprache.
 >- Für nativen Code betrachtet nicht Debugger die erste Auswertung der Bedingung, sodass der Haltepunkt bei der ersten Auswertung kein Änderung.
 >- Für verwalteten Code, trifft der Debugger den Breakpoint in der ersten Auswertung nach **Änderung** ausgewählt ist.

### <a name="using-object-ids-in-conditional-expressions-c-and-f-only"></a>Verwenden von Objekt-IDs in bedingten Ausdrücken (C# und F# nur)
 Es gibt Situationen, wenn Sie das Verhalten eines bestimmten Objekts beobachten möchten. Beispielsweise empfiehlt es sich um herauszufinden, warum ein Objekt mehr als einmal in einer Auflistung eingefügt wurde. In C# und F# können Sie Objekt-IDs für bestimmte Instanzen von [Verweistypen](/dotnet/csharp/language-reference/keywords/reference-types) erstellen und in Haltepunktbedingungen verwenden. Die Objekt-ID wird von den Debugdiensten der CLR (Common Language Runtime) generiert und dem Objekt zugeordnet.

**So erstellen Sie eine Objekt-ID:**

1. Legen Sie einen Haltepunkt im Code einer Stelle nach der Erstellung des Objekts.

2. Mit dem Debuggen beginnen, und wählen Sie bei der Ausführung am Haltepunkt angehalten wird, **Debuggen** > **Windows** > **"lokal"** oder **Alt** + **4** zum Öffnen der **"lokal"** Fenster.

   Suchen Sie den Haltepunkt in der **"lokal"** rechten Maustaste, und wählen Sie **Objekt-ID**.

   Sie sollten ein **$** und eine Zahl im **Lokalfenster** einen Haltepunkt festlegen. Dies ist die Objekt-ID.

3. Fügen Sie einen neuen Haltepunkt, an dem Punkt, die, den Sie untersuchen möchten; z. B. wenn das Objekt ist, das der Auflistung hinzugefügt werden. Klicken Sie mit der rechten Maustaste auf den Haltepunkt, und wählen Sie **Bedingungen** aus.

4. Verwenden Sie die Objekt-ID im Feld **Bedingter Ausdruck**. Z. B. wenn die Variable `item` ist das Objekt der Auflistung, die Option hinzugefügt werden **ist "true"** und **item == $\<n >**, wobei \<n > ist die Objekt-ID-Nummer .

   Die Ausführung wird an dem Punkt unterbrochen, an dem dieses Objekt der Auflistung hinzugefügt werden soll.

   Um die Objekt-ID zu löschen, Maustaste die Variable in der **"lokal"** Fenster, und wählen **Objekt-ID löschen**.

>[!NOTE]
>Objekt-IDs erstellen Weak-Verweise und verhindern nicht, dass das Objekt in die Garbage Collection aufgenommen wird. Sie gelten nur für die aktuelle Debugsitzung.

### <a name="hit-count"></a>Trefferanzahl
 Wenn Sie vermuten, dass eine Schleife im Code nach einer bestimmten Anzahl von Iterationen ein fehlerhaftes Verhalten aufweist, können Sie festlegen, dass einen Haltepunkt zum Beenden der Ausführung nach dieser Anzahl von Treffern, anstatt wiederholt drücken **F5** Iteration zu erreichen.

 Klicken Sie unter **Bedingungen** in die **Haltepunkteinstellungen** wählen Sie im Fenster **Trefferanzahl**, und geben Sie dann auf die Anzahl der Iterationen. Im folgenden Beispiel wird der Haltepunkt erreicht wird, bei jeder Iteration festgelegt:

 ![Trefferanzahl für Haltepunkt](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="filter"></a>Filter
Sie können einen Haltepunkt so einschränken, dass dieser nur auf bestimmten Geräten oder in angegebenen Prozesse und Threads aktiviert wird.

Klicken Sie unter **Bedingungen** in die **Haltepunkteinstellungen** wählen Sie im Fenster **Filter**, und geben Sie dann eine oder mehrere der folgenden Ausdrücke:

- MachineName = "name"
- ProcessId = value
- ProcessName = "name"
- ThreadId = value
- ThreadName = "name"

Schließen Sie Zeichenfolgewerte in doppelte Anführungszeichen ein. Sie können Klauseln mit `&` (AND), `||` (OR), `!` (NOT), und Klammern kombinieren.

## <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Haltepunktaktionen und Ablaufverfolgungspunkte
 Beim *Ablaufverfolgungspunkt* handelt es sich um einen Haltepunkt, der eine Meldung im Fenster **Ausgabe** ausgibt. Ein Ablaufverfolgungspunkt kann wie eine temporäre Trace-Anweisung in der Programmiersprache reagieren.

**So legen Sie einen Ablaufverfolgungspunkt fest:**

1. Mit der rechten Maustaste eines Haltepunkts, und wählen Sie **Aktionen**. Oder im der **Haltepunkteinstellungen** Fenster, zeigen Sie auf den Haltepunkt, wählen Sie die **Einstellungen** Symbol, und wählen Sie dann **Aktionen**.

1. Geben Sie eine Nachricht in die **Meldung im Ausgabefenster protokollieren** Feld. Die Nachricht kann generische Textzeichenfolgen, die Werte der Variablen oder Ausdrücke in geschweiften Klammern und Formatbezeichner enthalten ([c#](../debugger/format-specifiers-in-csharp.md) und [C++](../debugger/format-specifiers-in-cpp.md)) für die Werte.

   Sie können auch die folgenden speziellen Schlüsselwörter in der Nachricht verwenden:

   - **$ADDRESS** -aktuelle Anweisung
   - **$CALLER** -Aufrufen des Funktionsnamens
   - **$CALLSTACK** -Aufrufliste
   - **$FUNCTION** -Name der aktuellen Funktion
   - **$PID** -Prozess-Id
   - **$PNAME** -Name des Prozesses
   - **$TID** -Thread-Id
   - **$TNAME** -Threadname
   - **$TICK** -Anzahl der Ticks (aus Windows `GetTickCount`)

1. So drucken Sie die Nachricht an die **Ausgabe** Fenster ohne Unterbrechung, wählen die **Ausführung fortsetzen** Kontrollkästchen. Deaktivieren Sie das Kontrollkästchen, um die Nachricht und unterbricht die Ausführung an der Ablaufverfolgungspunkt zu drucken.

Ablaufverfolgungspunkte werden als rote Diamanten in den linken Rand des Quellcodes angezeigt und **Haltepunkte** Windows.

## <a name="see-also"></a>Siehe auch

- [Was bedeutet „Debuggen“?](../debugger/what-is-debugging.md)
- [Schreiben Sie besser C# code mithilfe von Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Ein erster Blick auf das Debuggen](../debugger/debugger-feature-tour.md)
- [Problembehandlung von Haltepunkten in Visual Studio-debugger](../debugger/troubleshooting-breakpoints.md)