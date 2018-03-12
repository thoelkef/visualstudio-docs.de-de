---
title: In Visual Studio-Debugger die Aufrufliste anzeigen | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 04/06/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e10b81ff07b77e2fd6202d2f5fb27392fe8134c2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-visual-studio-debugger"></a>Zeigen Sie die Aufrufliste an und verwenden Sie des Fensters Aufrufliste in Visual Studio-debugger

Mithilfe der **Aufrufliste** Fenster sehen Sie die Funktions- und Prozeduraufrufen, die derzeit im Stapel befinden. Die **Aufrufliste** Fenster zeigt die Reihenfolge, in der Funktionen und Methoden werden aufgerufen. Die Aufrufliste ist eine gute Möglichkeit, untersuchen und Verstehen der Ausführungsfluss einer app.
  
Wenn [Debugsymbole](#bkmk_symbols) stehen nicht für einen Teil der Aufrufliste die **Aufrufliste** Fenster möglicherweise nicht korrekt Informationen für diesen Teil der Aufrufliste angezeigt. In diesem Fall wird die folgende Notation angezeigt:  
  
`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

>  [!NOTE]
> Die **Aufrufliste** Fenster ähnelt der Debug-Perspektive in einigen IDEs wie Eclipse. 

> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den hier beschriebenen. Wählen Sie zum Ändern Ihrer Einstellungen **Einstellungen importieren und exportieren** auf die **Tools** Menü.  Finden Sie unter [Personalisieren der IDE](../ide/personalizing-the-visual-studio-ide.md)
  
## <a name="view-the-call-stack-while-in-the-debugger"></a>Anzeigen der Aufrufliste im debugger 
  
-   Während des Debuggens, in der **Debuggen** klicken Sie im Menü **Windows > Aufrufliste**.

 ![Fenster "Aufrufliste"](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Ein gelber Pfeil bezeichnet den Stapelrahmen, in dem sich der Ausführungszeiger derzeit befindet. Standardmäßig ist dies der Stapelrahmen entspricht, dessen Informationen, in der Quelle angezeigt **"lokal"**, **"Auto"**, **Überwachen**, und **Disassembly** Windows . Wenn Sie den Kontext des Debuggers mit einem anderen Rahmen im Stapel ändern möchten, Sie können dies vornehmen, indem [wechseln zu anderem Stapelrahmen](#bkmk_switch).   
  
## <a name="display-non-user-code-in-the-call-stack-window"></a>Anzeigen von nicht-benutzerseitigen Code im Fenster "Aufrufliste"  
  
-   Mit der rechten Maustaste die **Aufrufliste** und wählen Sie **externen Code anzeigen**.

Nichtbenutzercode wird jeglicher Code, der nicht angezeigt wird [nur mein Code](../debugger/just-my-code.md) aktiviert ist. In verwaltetem Code werden nicht-benutzerseitigen Codeframes standardmäßig ausgeblendet. Die folgende Notation wird anstelle der nicht-benutzerseitigen Codeframes angezeigt:  
  
**[\<Externer Code >]**  
  
## <a name="bkmk_switch"></a>Wechseln Sie zu anderem Stapelrahmen (Ändern des Debugkontexts)
  
1.  In der **Aufrufliste** Fenster mit der rechten Maustaste im Stapel sind der Rahmen, dessen Code und Daten, die Sie anzeigen möchten.

    Oder doppelklicken Sie auf einen Frame in der **Aufrufliste** Fenster, um auf den ausgewählten Frame zu wechseln. 
  
2.  Wählen Sie **zu Rahmen wechseln**.  
  
     Neben den Stapelrahmen, den Sie ausgewählt haben, wird ein grüner Pfeil in Form einer Welle angezeigt. Der Ausführungszeiger verbleibt im ursprünglichen Rahmen, der noch immer durch einen gelben Pfeil gekennzeichnet ist. Bei Auswahl des **Schritt** oder **Fortfahren** aus der **Debuggen** Menü Ausführung wird im ursprünglichen Rahmen fortgesetzt, die nicht im neu ausgewählten.  
  
## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Zeigen Sie den Quellcode für eine Funktion in der Aufrufliste an.  
  
-   In der **Aufrufliste** der rechten Maustaste auf die Funktion, deren Quellcode Sie, anzeigen möchten und wählen Sie **Gehe zu Quellcode**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Führen Sie aus dem Fenster "Aufrufliste" eine bestimmte Funktion  
  
-  In der **Aufrufliste** Fenster, wählen Sie die Funktion, mit der rechten Maustaste und wählen Sie **Ausführen bis Cursor**.  
  
## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Legen Sie einen Haltepunkt am Exitpunkt eines Funktionsaufrufs  
  
-   Finden Sie unter [Festlegen eines Haltepunkts in einem Stapel Funktion](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).

## <a name="display-calls-to-or-from-another-thread"></a>Anzeigen von Anrufen zu oder von einem anderen thread  
  
-   Mit der rechten Maustaste die **Aufrufliste** und wählen Sie **Aufrufe zu / von anderen Threads einschließen**.   
  
## <a name="visually-trace-the-call-stack"></a>Die Aufrufliste visuell zu verfolgen  

Wenn Sie Visual Studio Enterprise (nur) verwenden, können Sie Code Maps für die Aufrufliste während des Debuggens anzeigen.

- In der **Aufrufliste** Fenster, das Kontextmenü zu öffnen. Wählen Sie **Aufrufliste in Codezuordnung anzeigen**. (Tastatur: **STRG** + **UMSCHALT** + **`**)  
  
    Ausführliche Informationen finden Sie unter [Zuordnen von Methoden in der Aufrufliste während des Debuggens](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Aufrufliste in Codezuordnung anzeigen](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")
  
## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack"></a>Zeigen Sie den Disassemblierungscode für eine Funktion in der Aufrufliste  
  
-   In der **Aufrufliste** der rechten Maustaste auf die Funktion, deren Disassemblycode Sie, anzeigen möchten und wählen Sie **Gehe zu Disassembly**.    

## <a name="change-the-optional-information-displayed"></a>Ändern Sie die Anzeige optionale Informationen  
  
-   Mit der rechten Maustaste die **Aufrufliste** Fenster "und" Set "oder" Clear **anzeigen \<**  *die gewünschten Informationen*  **>** .  
  
## <a name="bkmk_symbols"></a>Symbole für ein Modul laden
In der **Aufrufliste** Fenster können Sie laden Debugsymbole für Code, der derzeit keine Symbole geladen sind. Bei diesen Symbolen kann es sich um .NET Framework-Symbole oder Systemsymbole handeln, die von den öffentlichen Microsoft-Symbolservern heruntergeladen wurden, oder um Symbole in einem Symbolpfad auf dem Computer, den Sie debuggen.  
  
Finden Sie unter [angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
### <a name="to-load-symbols"></a>So laden Sie Symbole  
  
1.  In der **Aufrufliste** der rechten Maustaste auf der Stapelrahmen, für welche Symbole nicht geladen werden. Der Rahmen wird abgeblendet.  
  
2.  Zeigen Sie auf **Symbole laden** , und klicken Sie dann auf **Microsoft-Symbolserver** (falls verfügbar) oder wechseln Sie zu den Symbolpfad.  
  
### <a name="to-set-the-symbol-path"></a>So legen Sie den Symbolpfad fest  
  
1.  In der **Aufrufliste** Fenster, wählen Sie **Symboleinstellungen** aus dem Kontextmenü.  
  
     Die **Optionen** Dialogfeld wird geöffnet und die **Symbole** angezeigt wird.  
  
2.  Klicken Sie auf **Symbol Settings**.  
  
3.  In der **Optionen** Dialogfeld klicken Sie auf das Symbol "Ordner".  
  
     In der **Speicherorte für Symboldateien (.pdb) Symbol** Feld ein Cursor angezeigt.  
  
4.  Geben Sie einen Verzeichnispfadnamen zum Symbolspeicherort auf dem Computer ein, den Sie debuggen. Für lokale und remote zu Debuggen ist dies ein Pfad auf dem lokalen Computer.
  
5.  Klicken Sie auf **OK**, um das Dialogfeld **Optionen** zu schließen.  
  
## <a name="see-also"></a>Siehe auch  
 [Gemischter Code und fehlende Daten im Fenster "Aufrufliste"](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)