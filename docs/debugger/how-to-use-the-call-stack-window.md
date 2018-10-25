---
title: Anzeigen der Aufrufliste im Visual Studio-Debugger | Microsoft-Dokumentation
ms.custom: H1Hack27Feb2017
ms.date: 04/06/2017
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d390ba4cd47297c6d653cb68693439fd01c16815
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853609"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-visual-studio-debugger"></a>Zeigen Sie die Aufrufliste an und verwenden Sie des Fensters Aufrufliste in Visual Studio-debugger

Mithilfe der **Aufrufliste** Fenster sehen Sie die Funktions- und Prozeduraufrufen, die derzeit auf dem Stapel vorhanden sind. Die **Aufrufliste** Fenster zeigt die Reihenfolge, in dem Methoden und Funktionen werden aufgerufen. Die Aufrufliste ist eine gute Möglichkeit zum Untersuchen und verstehen, den Ausführungsablauf der app.
  
Wenn [Debugsymbole](#bkmk_symbols) sind nicht verfügbar für einen Teil einer Aufrufliste, die **Aufrufliste** Fenster möglicherweise nicht korrekten Informationen für den jeweiligen Teil der Aufrufliste angezeigt. Wenn in diesem Fall wird die folgende Notation angezeigt:  
  
`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> Die **Aufrufliste** Fenster ähnelt der Debug-Perspektive in einigen IDEs wie Eclipse. 
> 
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den hier beschriebenen. Wählen Sie zum Ändern Ihrer Einstellungen **Einstellungen importieren und exportieren** auf die **Tools** Menü.  Finden Sie unter [Personalisieren der IDE](../ide/personalizing-the-visual-studio-ide.md)
  
## <a name="view-the-call-stack-while-in-the-debugger"></a>Anzeigen der Aufrufliste im debugger 
  
- Während des Debuggens in der **Debuggen** , wählen Sie im Menü **Windows > Aufrufliste**.

  ![Fenster "Aufrufliste"](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Ein gelber Pfeil bezeichnet den Stapelrahmen, in dem sich der Ausführungszeiger derzeit befindet. Standardmäßig ist dies der Stapelrahmen, deren Informationen, in der Quelle angezeigt **"lokal"**, **"Auto"**, **Watch**, und **Disassembly** Windows . Wenn Sie den Debuggerkontext in einen anderen Frame im Stapel ändern möchten, erreichen Sie, die von [wechseln zu anderem Stapelrahmen](#bkmk_switch).   
  
## <a name="display-non-user-code-in-the-call-stack-window"></a>Nicht benutzerseitiger Code angezeigt, in dem Fenster "Aufrufliste"  
  
-   Mit der rechten Maustaste die **Aufrufliste** Fenster, und wählen **externen Code anzeigen**.

Nicht benutzerseitiger Code ist Code, der nicht Wenn angezeigt wird [nur mein Code](../debugger/just-my-code.md) aktiviert ist. In verwaltetem Code sind nicht benutzerseitiger Codeframes standardmäßig ausgeblendet. Die folgende Notation wird anstelle der Frames nicht benutzerseitiger Code angezeigt:  
  
**[\<Externen Code >]**  
  
## <a name="bkmk_switch"></a> Wechseln Sie zu anderem Stapelrahmen (Ändern des Debugkontexts)
  
1.  In der **Aufrufliste** der rechten Maustaste auf der Stapel Rahmen, dessen Code und Daten, die Sie anzeigen möchten.

    Sie können auch auf den Frame Doppelklicken der **Aufrufliste** Fenster aus, um auf den ausgewählten Frame wechseln. 
  
2.  Wählen Sie **zu Rahmen wechseln**.  
  
     Neben den Stapelrahmen, die, den Sie ausgewählt haben, wird ein grüner Pfeil in Form einer Welle angezeigt. Der Ausführungszeiger verbleibt im ursprünglichen Rahmen, der noch immer durch einen gelben Pfeil gekennzeichnet ist. Bei Auswahl von **Schritt** oder **Weiter** aus der **Debuggen** Menü Ausführung wird im ursprünglichen Rahmen fortgesetzt, die nicht im neu ausgewählten.  
  
## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Den Quellcode für eine Funktion in der Aufrufliste anzeigen  
  
-   In der **Aufrufliste** der rechten Maustaste auf die Funktion, deren Quellcode Sie, anzeigen möchten und wählen Sie **Gehe zu Quellcode**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Führen Sie an eine bestimmte Funktion aus dem Fenster "Aufrufliste"  
  
-  In der **Aufrufliste** Fenster, wählen Sie die Funktion, mit der rechten Maustaste und wählen Sie **Ausführen bis Cursor**.  
  
## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Legen Sie einen Haltepunkt am Exitpunkt eines Funktionsaufrufs  
  
-   Finden Sie unter [Festlegen eines Haltepunkts in einer Call Stack-Funktion](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).

## <a name="display-calls-to-or-from-another-thread"></a>Anzeigen von Anrufen zu oder von einem anderen thread  
  
-   Mit der rechten Maustaste die **Aufrufliste** Fenster, und wählen **Aufrufe zu/von anderen Threads einschließen**.   
  
## <a name="visually-trace-the-call-stack"></a>Die Aufrufliste visuell zu verfolgen  

Wenn Sie Visual Studio Enterprise (nur) verwenden, können Sie Code Maps für die Aufrufliste beim Debuggen anzeigen.

- In der **Aufrufliste** Fenster, das Kontextmenü zu öffnen. Wählen Sie **Aufrufliste auf Code Map anzeigen**. (Tastatur: **STRG** + **UMSCHALT** + **`**)  
  
    Ausführliche Informationen finden Sie unter [Zuordnen von Methoden in der Aufrufliste beim Debuggen](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Aufrufliste auf Code Map anzeigen](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")
  
## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack"></a>Zeigen Sie den Disassemblierungscode für eine Funktion in der Aufrufliste  
  
-   In der **Aufrufliste** der rechten Maustaste auf die Funktion, deren Disassemblycode Sie, anzeigen möchten und wählen Sie **Gehe zu Disassembly**.    

## <a name="change-the-optional-information-displayed"></a>Ändern Sie die Anzeige optionale Informationen  
  
-   Mit der rechten Maustaste die **Aufrufliste** Fenster und aktivieren oder deaktivieren **anzeigen \<**  _die gewünschten Informationen_ **>**.  
  
## <a name="bkmk_symbols"></a> Symbole für ein Modul laden
In der **Aufrufliste** Fenster können Sie laden die Debugsymbole für Code, der derzeit keine Symbole geladen sind. Bei diesen Symbolen kann es sich um .NET Framework-Symbole oder Systemsymbole handeln, die von den öffentlichen Microsoft-Symbolservern heruntergeladen wurden, oder um Symbole in einem Symbolpfad auf dem Computer, den Sie debuggen.  
  
Finden Sie unter [angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
### <a name="to-load-symbols"></a>So laden Sie Symbole  
  
1.  In der **Aufrufliste** der rechten Maustaste auf der Stapelrahmen, für welche Symbole nicht geladen werden. Der Rahmen wird abgeblendet.  
  
2.  Zeigen Sie auf **Symbole laden** , und klicken Sie dann auf **Microsoft-Symbolserver** (falls verfügbar) oder suchen Sie nach den Symbolpfad.  
  
### <a name="to-set-the-symbol-path"></a>So legen Sie den Symbolpfad fest  
  
1.  In der **Aufrufliste** Fenster wählen **Symboleinstellungen** aus dem Kontextmenü.  
  
     Die **Optionen** Dialogfeld wird geöffnet und die **Symbole** angezeigt wird.  
  
2.  Klicken Sie auf **Symboleinstellungen**.  
  
3.  In der **Optionen** Dialogfeld klicken Sie auf das Ordnersymbol.  
  
     In der **Symboldateien (.pdb) Orte für Symboldateien** Feld ein Cursor angezeigt.  
  
4.  Geben Sie einen Verzeichnispfadnamen zum Symbolspeicherort auf dem Computer ein, den Sie debuggen. Für lokale und remote zu Debuggen ist dies ein Pfad auf dem lokalen Computer.
  
5.  Klicken Sie auf **OK**, um das Dialogfeld **Optionen** zu schließen.  
  
## <a name="see-also"></a>Siehe auch  
 [Gemischter Code und fehlende Daten im Fenster "Aufrufliste"](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)