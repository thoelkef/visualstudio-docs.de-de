---
title: Anzeigen der Aufrufliste im Debugger | Microsoft-Dokumentation
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
ms.openlocfilehash: 2673ed9a69a80b2e9ab9275ff54909e33e4434f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906351"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>Anzuzeigen Sie die Aufrufliste, und verwenden Sie das Fenster "Aufrufliste" im debugger

Mithilfe des Fensters **Aufrufliste** können Sie die Funktions- und Prozeduraufrufe anzeigen, die sich derzeit im Stapel befinden. Im Fenster **Aufrufliste** wird die Reihenfolge angezeigt, in der Methoden und Funktionen aufgerufen werden. Die Aufrufliste bietet eine nützliche Möglichkeit zum Untersuchen und Verstehen des Ausführungsablaufs einer App.

Wenn [Debugsymbole](#bkmk_symbols) sind nicht verfügbar für einen Teil einer Aufrufliste, die **Aufrufliste** Fenster ist möglicherweise nicht in der richtigen Informationen für diesen Teil der Aufrufliste angezeigt, stattdessen anzeigen:

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> Das Fenster **Aufrufliste** ist mit der Debugperspektive in einigen IDEs wie Eclipse vergleichbar.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den hier beschriebenen. Wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern.  Finden Sie unter [Einstellungen zurücksetzen](../ide/environment-settings.md#reset-settings).

## <a name="view-the-call-stack-while-in-the-debugger"></a>Anzeigen der Aufrufliste im debugger

- Während des Debuggens in der **Debuggen** , wählen Sie im Menü **Windows > Aufrufliste**.

  ![Fenster "Aufrufliste"](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Ein gelber Pfeil bezeichnet den Stapelrahmen, in dem sich der Ausführungszeiger derzeit befindet. Standardmäßig diesen Stapelrahmen Informationen wird angezeigt, in der Quelle **"lokal"**, **"Auto"**, **Watch**, und **Disassembly** Windows. So ändern Sie die Debuggerkontext zu einem anderen Frame im Stapel [wechseln zu anderem Stapelrahmen](#bkmk_switch).

## <a name="display-non-user-code-in-the-call-stack-window"></a>Nicht benutzerseitiger Code angezeigt, in dem Fenster "Aufrufliste"

- Klicken Sie mit der rechten Maustaste auf das Fenster **Aufrufliste**, und wählen Sie **Externen Code anzeigen** aus.

Nicht benutzerseitiger Code ist Code, der nicht Wenn angezeigt wird [nur mein Code](../debugger/just-my-code.md) aktiviert ist. In verwaltetem Code sind nicht benutzerseitiger Codeframes standardmäßig ausgeblendet. Die folgende Notation wird anstelle der Frames nicht benutzerseitiger Code angezeigt:

`[<External Code>]`

## <a name="bkmk_switch"></a> Wechseln Sie zu anderem Stapelrahmen (Ändern des Debugkontexts)

1. In der **Aufrufliste** der rechten Maustaste auf der Stapel Rahmen, dessen Code und Daten, die Sie anzeigen möchten.

    Sie können auch auf den Frame Doppelklicken der **Aufrufliste** Fenster, wechseln Sie zu diesem Frame.

2. Wählen Sie **Switch to Frame** (Zu Frame wechseln) aus.

     Neben den Stapelrahmen, die, den Sie ausgewählt haben, wird ein grüner Pfeil in Form einer Welle angezeigt. Der Ausführungszeiger verbleibt im ursprünglichen Rahmen, der noch immer durch einen gelben Pfeil gekennzeichnet ist. Wenn Sie im Menü **Debuggen** den Befehl **Schritt** oder **Weiter** auswählen, wird die Ausführung nicht im neu ausgewählten, sondern im ursprünglichen Frame fortgesetzt.

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Den Quellcode für eine Funktion in der Aufrufliste anzeigen

- Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf die Funktion, deren Quellcode Sie anzeigen möchten, und wählen Sie **Gehe zu Quellcode** aus.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Führen Sie an eine bestimmte Funktion aus dem Fenster "Aufrufliste"

- In der **Aufrufliste** Fenster, wählen Sie die Funktion, mit der rechten Maustaste, und wählen Sie dann **Ausführen bis Cursor**.

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Legen Sie einen Haltepunkt am Exitpunkt eines Funktionsaufrufs

- Finden Sie unter [Festlegen eines Haltepunkts in einer Call Stack-Funktion](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).

## <a name="display-calls-to-or-from-another-thread"></a>Anzeigen von Anrufen zu oder von einem anderen thread

- Klicken Sie mit der rechten Maustaste auf das Fenster **Aufrufliste**, und wählen Sie **Aufrufe zu/von anderen Threads einschließen** aus.

## <a name="visually-trace-the-call-stack"></a>Die Aufrufliste visuell zu verfolgen

In Visual Studio Enterprise (nur) können Sie Code Maps für die Aufrufliste beim Debuggen anzeigen.

- Öffnen Sie das Kontextmenü im Fenster **Aufrufliste**. Wählen Sie **Aufrufliste auf Code Map anzeigen** (**STRG** + **UMSCHALT** + **`**).

    Weitere Informationen finden Sie unter [Zuordnen von Methoden in der Aufrufliste beim Debuggen](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Aufrufliste auf Code Map anzeigen](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Zeigen Sie den Disassemblierungscode für eine Funktion in der Aufrufliste (C#, C++, Visual Basic F#)

- Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf die Funktion, deren Disassemblycode Sie anzeigen möchten, und wählen Sie **Gehe zu Disassembly** aus.

## <a name="change-the-optional-information-displayed"></a>Ändern Sie die Anzeige optionale Informationen

- Mit der rechten Maustaste den **Aufrufliste** Fenster und aktivieren oder deaktivieren **anzeigen \<**  _die gewünschten Informationen_ **>**.

## <a name="bkmk_symbols"></a> Laden von Symbolen für ein Modul (C#, C++, Visual Basic F#)

Im Fenster **Aufrufliste** können Sie Debugsymbole für Code laden, für den derzeit keine Symbole geladen sind. Bei diesen Symbolen kann es sich um .NET Framework-Symbole oder Systemsymbole handeln, die von den öffentlichen Microsoft-Symbolservern heruntergeladen wurden, oder um Symbole in einem Symbolpfad auf dem Computer, den Sie debuggen.

Weitere Informationen finden Sie unter [Angeben von Symbol- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-load-symbols"></a>So laden Sie Symbole

1. In der **Aufrufliste** der rechten Maustaste auf der Stapelrahmen, für welche Symbole nicht geladen werden. Der Rahmen wird abgeblendet.

2. Zeigen Sie auf **Symbole laden** und wählen Sie dann **Microsoft-Symbolserver** (falls verfügbar), oder navigieren Sie zu den Symbolpfad.

### <a name="to-set-the-symbol-path"></a>So legen Sie den Symbolpfad fest

1. Wählen Sie im Fenster **Aufrufliste** im Kontextmenü die Option **Symboleinstellungen** aus.

     Das Dialogfeld **Optionen** wird geöffnet, und die Seite **Symbole** wird angezeigt.

2. Wählen Sie **Symboleinstellungen**.

3. Klicken Sie im Dialogfeld **Optionen** auf das Ordnersymbol.

     Im Feld **Speicherorte für Symboldateien (.pdb)** wird ein Cursor angezeigt.

4. Geben Sie einen Verzeichnispfadnamen zum Symbolspeicherort auf dem Computer, den Sie debuggen. Für lokale und remote zu Debuggen ist dies ein Pfad auf dem lokalen Computer.

5. Wählen Sie **OK** schließen die **Optionen** Dialogfeld.

## <a name="see-also"></a>Siehe auch

- [Gemischter Code und fehlende Daten im Fenster "Aufrufliste"](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [Viewing data in the debugger (Anzeigen von Daten im Debugger)](../debugger/viewing-data-in-the-debugger.md)
- [Specify symbol (.pdb) and source files (Angeben von Symboldateien (PDB) und Quelldateien)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)