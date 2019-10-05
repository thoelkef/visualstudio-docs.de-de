---
title: Anzeigen der Rückruf Stapel im Debugger | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 10/29/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0b9fb6e809f1124a10a6a2b4e35bc59806787a6
ms.sourcegitcommit: 8a3545329a58e446672181cfed2083f850e1ad14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71814331"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>Anzeigen der aufrufsstapel und Verwenden des Fensters "Fenster" im Debugger

Mithilfe des Fensters **Aufrufliste** können Sie die Funktions- und Prozeduraufrufe anzeigen, die sich derzeit im Stapel befinden. Im Fenster **Aufrufliste** wird die Reihenfolge angezeigt, in der Methoden und Funktionen aufgerufen werden. Die Aufrufliste bietet eine nützliche Möglichkeit zum Untersuchen und Verstehen des Ausführungsablaufs einer App.

Wenn das [Debuggen von Symbolen](#bkmk_symbols) für einen Teil einer Aufruf Stapel nicht verfügbar ist, kann das Fenster **Aufruf Stapel** möglicherweise keine korrekten Informationen für diesen Teil der Aufruf Stapel anzeigen, stattdessen wird Folgendes angezeigt:

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> Das Fenster **Aufrufliste** ist mit der Debugperspektive in einigen IDEs wie Eclipse vergleichbar.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den hier beschriebenen. Wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern.  Siehe [Zurücksetzen von Einstellungen](../ide/environment-settings.md#reset-settings).

## <a name="view-the-call-stack-while-in-the-debugger"></a>Anzeigen der aufrufsstapel im Debugger

- Wählen Sie beim Debuggen im Menü **Debuggen** die Option **Windows->-Aufrufe**

  ![Aufruf Listenfenster](../debugger/media/dbg_basics_callstack_window.png "callstackwindow")

Ein gelber Pfeil bezeichnet den Stapelrahmen, in dem sich der Ausführungszeiger derzeit befindet. Standardmäßig werden die Informationen dieses Stapels in den Fenstern "Quelle **", "lokal", "** Auto **", "** **Überwachung**" und " **Disassembly** " angezeigt. Wechseln Sie zu [einem anderen Stapel Rahmen](#bkmk_switch), um den debuggerkontext in einen anderen Frame im Stapel zu ändern.

## <a name="display-non-user-code-in-the-call-stack-window"></a>Anzeigen von Nichtbenutzer Code im Fenster "aufrufsstapel"

- Klicken Sie mit der rechten Maustaste auf das Fenster **Aufrufliste**, und wählen Sie **Externen Code anzeigen** aus.

Bei Nichtbenutzer Code handelt es sich um Code, der nicht angezeigt wird, wenn [nur eigenen Code](../debugger/just-my-code.md) aktiviert ist. In verwaltetem Code werden Nichtbenutzer Code rahmenstandard mäßig ausgeblendet. Die folgende Notation wird anstelle der Nichtbenutzer Code Rahmen angezeigt:

`[<External Code>]`

## <a name="bkmk_switch"></a>Wechseln Sie zu einem anderen Stapel Rahmen (ändern Sie den debuggerkontext).

1. Klicken Sie im Fenster " **aufrufsstapel** " mit der rechten Maustaste auf den Stapel Rahmen, dessen Code und Daten Sie anzeigen möchten.

    Sie können auch auf einen Frame im Fenster "Fenster" **aufgerufen** werden, um zu diesem Frame zu wechseln.

2. Wählen Sie **Switch to Frame** (Zu Frame wechseln) aus.

     Neben dem Stapel Rahmen, den Sie ausgewählt haben, wird ein grüner Pfeil mit einem geschweiften Ende angezeigt. Der Ausführungszeiger verbleibt im ursprünglichen Rahmen, der noch immer durch einen gelben Pfeil gekennzeichnet ist. Wenn Sie im Menü **Debuggen** den Befehl **Schritt** oder **Weiter** auswählen, wird die Ausführung nicht im neu ausgewählten, sondern im ursprünglichen Frame fortgesetzt.

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Anzeigen des Quellcodes für eine Funktion in der aufrufsstapel

- Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf die Funktion, deren Quellcode Sie anzeigen möchten, und wählen Sie **Gehe zu Quellcode** aus.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Ausführen bis zu einer bestimmten Funktion aus dem Fenster "aufrufsstapel"

- Wählen Sie im Fenster " **CallStack** " die Funktion aus, klicken Sie mit der rechten Maustaste, und wählen Sie dann **Ausführen bis Cursor**aus.

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Festlegen eines halte Punkts am Beendigungs Punkt eines Funktions Aufrufes

- Weitere Informationen finden Sie [unter Festlegen eines halte Punkts in einer Funktion der-Funktion](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="display-calls-to-or-from-another-thread"></a>Aufrufe von oder von einem anderen Thread anzeigen

- Klicken Sie mit der rechten Maustaste auf das Fenster **Aufrufliste**, und wählen Sie **Aufrufe zu/von anderen Threads einschließen** aus.

## <a name="visually-trace-the-call-stack"></a>Visuelles verfolgen der aufrufsstapel

In Visual Studio Enterprise (nur) können Sie Code Maps für die aufrufsstapel beim Debuggen anzeigen.

- Öffnen Sie das Kontextmenü im Fenster **Aufrufliste**. Wählen Sie **in der Code Map die Option Show Stack anzeigen** (**STRG** + **Shift** +  **`** ).

    Weitere Informationen finden Sie unter [map-Methoden in der aufrufsstapel beim Debuggen](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Aufruf Liste in Code Map Show](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "callstackoncodemap") anzeigen

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Anzeigen des Disassemblycodes für eine Funktion in der aufrufsstapel (C#, C++, Visual Basic, F#)

- Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf die Funktion, deren Disassemblycode Sie anzeigen möchten, und wählen Sie **Gehe zu Disassembly** aus.

## <a name="change-the-optional-information-displayed"></a>Ändern der angezeigten optionalen Informationen

- Klicken Sie mit der rechten Maustaste in das Fenster " **aufrufsstapel** ", und legen Sie **\<-** _Informationen_anzeigen **>** fest.

## <a name="bkmk_symbols"></a>Laden von Symbolen für ein ModulC#( C++,, Visual Basic F#,)

Im Fenster **Aufrufliste** können Sie Debugsymbole für Code laden, für den derzeit keine Symbole geladen sind. Bei diesen Symbolen kann es sich um .NET Framework-Symbole oder Systemsymbole handeln, die von den öffentlichen Microsoft-Symbolservern heruntergeladen wurden, oder um Symbole in einem Symbolpfad auf dem Computer, den Sie debuggen.

Weitere Informationen finden Sie unter [Angeben von Symbol- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-load-symbols"></a>So laden Sie Symbole

1. Klicken Sie **im Fenster "** Fenster" mit der rechten Maustaste auf den Stapel Rahmen, für den Symbole nicht geladen werden. Der Rahmen wird abgeblendet.

2. Zeigen Sie auf **Symbole laden** , und wählen Sie dann **Microsoft-Symbol Server** (falls verfügbar) aus, oder navigieren Sie zum Symbol Pfad.

### <a name="to-set-the-symbol-path"></a>So legen Sie den Symbolpfad fest

1. Wählen Sie im Fenster **Aufrufliste** im Kontextmenü die Option **Symboleinstellungen** aus.

     Das Dialogfeld **Optionen** wird geöffnet, und die Seite **Symbole** wird angezeigt.

2. Wählen Sie **Symbol Einstellungen**aus.

3. Klicken Sie im Dialogfeld **Optionen** auf das Ordnersymbol.

     Im Feld **Speicherorte für Symboldateien (.pdb)** wird ein Cursor angezeigt.

4. Geben Sie einen Verzeichnis Pfadnamen zum Symbol Speicherort auf dem Computer ein, den Sie Debuggen. Beim lokalen und Remote Debuggen ist dies ein Pfad auf dem lokalen Computer.

5. Wählen Sie **OK** aus, um das Dialogfeld **Optionen** zu schließen.

## <a name="see-also"></a>Siehe auch

- [Gemischter Code und fehlende Daten im Fenster "Aufrufliste"](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [Viewing data in the debugger (Anzeigen von Daten im Debugger)](../debugger/viewing-data-in-the-debugger.md)
- [Specify symbol (.pdb) and source files (Angeben von Symboldateien (PDB) und Quelldateien)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)