---
title: 'Gewusst wie: Verwenden des Fensters "aufrufsstapel" | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 84c0bfead1633da13b4284cad04ace674045b057
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697474"
---
# <a name="how-to-use-the-call-stack-window"></a>Gewusst wie: Verwenden des Fensters Aufrufliste
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe des Fensters **Aufrufliste** können Sie die Funktions- und Prozeduraufrufe anzeigen, die sich derzeit im Stapel befinden.  
  
 Das Fenster " **aufrufsstapel** " zeigt den Namen der einzelnen Funktionen und die Programmiersprache an, in der Sie geschrieben ist. Der Name der Funktion oder der Prozedur wird möglicherweise von optionalen Informationen begleitet, z. B. Modulname, Zeilennummer, Parameternamen, -typen und -werte. Die Anzeige dieser optionalen Informationen kann ein- bzw. ausgeschaltet werden:  
  
 Ein gelber Pfeil bezeichnet den Stapelrahmen, in dem sich der Ausführungszeiger derzeit befindet. Standardmäßig ist dies der Frame, dessen Informationen in **den Fenstern Quelle** , **Disassembly**, **lokal, über** **Wachen**und Auto angezeigt werden. Wenn Sie den Kontext in einen anderen Frame auf dem Stapel ändern möchten, können Sie dies im Fenster "Fenster" **aufzurufen** .  
  
 Wenn das Debuggen von Symbolen für einen Teil einer Aufruf Stapel nicht verfügbar ist, kann das Fenster **Aufruf Stapel** möglicherweise keine korrekten Informationen für diesen Teil der Aufruf Stapel anzeigen. Die folgende Notation wird angezeigt:  
  
 [Die Rahmen unten sind möglicherweise falsch und/oder fehlen, für name.dll wurden keine Symbole geladen]  
  
 In verwaltetem Code standardmäßig. Das Fenster " **aufrufsstapel** " blendet Informationen für Nichtbenutzer Code aus. Die folgende Notation wird anstelle der ausgeblendeten Informationen angezeigt:  
  
 **[\<External Code>]**  
  
 Beim Nichtbenutzercode handelt es sich um Code, der nicht vom Typ "Mein Code" ist. Sie können angeben, die Aufruflisteninformationen für Nichtbenutzercode anzuzeigen, indem Sie das Kontextmenü verwenden.  
  
 Im Kontextmemü können Sie auswählen, ob Aufrufe zwischen Threads angezeigt werden sollen.  
  
> [!NOTE]
> Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen unterscheiden. Wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-call-stack-window-in-break-mode-or-in-run-mode"></a>So zeigen Sie das Fenster "Aufrufliste" im Unterbrechungsmodus oder im Ausführmodus an  
  
- Wählen Sie im Menü **Debuggen** die Option **Fenster** aus, **und klicken Sie dann auf die**Option  
  
### <a name="to-change-the-optional-information-displayed"></a>So ändern Sie die Anzeige optionaler Informationen  
  
- Klicken Sie **mit der rechten** Maustaste auf das Fenster "Fenster", und legen Sie ** \<**_the information that you want_**> anzeigen **fest.  
  
### <a name="to-display-non-user-code-frames-in-the-call-stack-window"></a>So zeigen Sie Rahmen mit nicht benutzerseitigem Code im Fenster "Aufrufliste" an  
  
- Klicken Sie mit der rechten Maustaste auf das Fenster **Aufrufliste**, und wählen Sie **Externen Code anzeigen** aus.  
  
### <a name="to-switch-to-another-stack-frame"></a>So wechseln Sie in einen anderen Stapelrahmen  
  
1. Klicken Sie im Fenster " **aufrufsstapel** " mit der rechten Maustaste auf den Frame, dessen Code und Daten Sie anzeigen möchten.  
  
2. Wählen Sie **Switch to Frame** (Zu Frame wechseln) aus.  
  
     Neben dem ausgewählten Rahmen wird ein grüner Pfeil in Form einer Welle angezeigt. Der Ausführungszeiger verbleibt im ursprünglichen Rahmen, der noch immer durch einen gelben Pfeil gekennzeichnet ist. Wenn Sie im Menü **Debuggen** den Befehl **Schritt** oder **Weiter** auswählen, wird die Ausführung nicht im neu ausgewählten, sondern im ursprünglichen Frame fortgesetzt.  
  
### <a name="to-display-calls-to-or-from-another-thread"></a>So zeigen Sie Aufrufe zu bzw. von anderen Threads an  
  
- Klicken Sie mit der rechten Maustaste auf das Fenster **Aufrufliste**, und wählen Sie **Aufrufe zu/von anderen Threads einschließen** aus.  
  
### <a name="to-view-the-source-code-for-a-function-on-the-call-stack"></a>So zeigen Sie den Quellcode für eine Funktion in der Aufrufliste an  
  
- Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf die Funktion, deren Quellcode Sie anzeigen möchten, und wählen Sie **Gehe zu Quellcode** aus.  
  
### <a name="to-visually-trace-the-call-stack"></a>So verfolgen Sie die Aufrufliste visuell  
  
1. Öffnen Sie das Kontextmenü im Fenster **Aufrufliste**. Wählen Sie **in Code Map die Option aufrufsstapel anzeigen** (Tastatur: **STRG**  +  **UMSCHALT**  +  **`** )  
  
     Weitere Informationen finden Sie [unter Map-Methoden in der-aufrufsstapel](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)  
  
### <a name="to-view-the-disassembly-code-for-a-function-on-the-call-stack"></a>So zeigen Sie den Disassembly-Code für eine Funktion in der Aufrufliste an  
  
- Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf die Funktion, deren Disassemblycode Sie anzeigen möchten, und wählen Sie **Gehe zu Disassembly** aus.  
  
### <a name="to-run-to-a-specific-function-from-the-call-stack-window"></a>So führen Sie im Aufruflistenfenster das Programm bis zu einer angegebenen Funktion aus  
  
- Wählen Sie im Fenster " **CallStack** " die Funktion aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Ausführen bis Cursor**aus.  
  
### <a name="to-set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>So legen Sie einen Haltepunkt am Exitpunkt eines Funktionsaufrufs fest  
  
- Weitere Informationen finden Sie unter [Festlegen von Breakpoints in Debuggerfenstern](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).  
  
### <a name="to-load-symbols-for-a-module"></a>So laden Sie Symbole für ein Modul  
  
- Klicken Sie im Fenster " **CallStack** " mit der rechten Maustaste auf den Frame, der das Modul anzeigt, dessen Symbole Sie erneut laden möchten, und wählen Sie **Symbole laden**aus.  
  
## <a name="loading-symbols"></a>Laden von Symbolen  
 Im Fenster **Aufrufliste** können Sie Debugsymbole für Code laden, für den derzeit keine Symbole geladen sind. Bei diesen Symbolen kann es sich um .NET Framework-Symbole oder Systemsymbole handeln, die von den öffentlichen Microsoft-Symbolservern heruntergeladen wurden, oder um Symbole in einem Symbolpfad auf dem Computer, den Sie debuggen.  
  
 Weitere Informationen finden Sie unter [Angeben von Symbol- (.pdb) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
#### <a name="to-load-symbols"></a>So laden Sie Symbole  
  
1. Klicken Sie im Fenster " **aufrufsstapel** " mit der rechten Maustaste auf den Frame, für den Symbole nicht geladen werden. Der Rahmen wird abgeblendet.  
  
2. Zeigen Sie auf **Symbole laden aus** , und klicken Sie dann auf **Microsoft-Symbol Server** oder **Symbol Pfad**.  
  
#### <a name="to-set-the-symbol-path"></a>So legen Sie den Symbolpfad fest  
  
1. Wählen Sie im Fenster **Aufrufliste** im Kontextmenü die Option **Symboleinstellungen** aus.  
  
     Das Dialogfeld **Optionen** wird geöffnet, und die Seite **Symbole** wird angezeigt.  
  
2. Klicken Sie auf **Symbol Einstellungen**.  
  
3. Klicken Sie im Dialogfeld **Optionen** auf das Ordnersymbol.  
  
     Im Feld **Speicherorte für Symboldateien (.pdb)** wird ein Cursor angezeigt.  
  
4. Geben Sie einen Verzeichnispfadnamen zum Symbolspeicherort auf dem Computer ein, den Sie debuggen. Beim lokalen Debuggen ist dies der lokale Computer. Beim Remotedebuggen ist es der Remotecomputer.  
  
5. Klicken Sie auf **OK**, um das Dialogfeld **Optionen** zu schließen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gemischter Code und fehlende Informationen im Fenster "aufrufsstapel"](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [Gewusst wie: Ändern des numerischen Formats von Debuggerfenstern](https://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)   
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Angeben von Symbol-(PDB-) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)
