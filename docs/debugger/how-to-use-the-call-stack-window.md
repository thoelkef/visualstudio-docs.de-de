---
title: "Gewusst wie: Verwenden des Fensters Aufrufliste | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.callstack"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "aspx"
helpviewer_keywords: 
  - "Threading [Visual Studio], Anzeigen von Aufrufen für oder aus"
  - "Funktionen [Debugger], Anzeigen von Code in der Aufrufliste"
  - "Disassemblycode"
  - "Haltepunkte, Fenster „Aufrufliste“"
  - "Debuggen [Visual Studio], Wechseln zu anderem Stapelrahmen"
  - "Debuggen [Visual Studio], Fenster „Aufrufliste“"
  - "Fenster „Aufrufliste“, Anzeigen des Quellcodes für Funktionen in der Aufrufliste"
  - "Stapel, Wechseln von Stapelrahmen"
  - "Fenster „Aufrufliste“, Anzeigen des Disassemblierungscodes für Funktionen in der Aufrufliste"
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
caps.latest.revision: 40
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Verwenden des Fensters Aufrufliste
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mithilfe des Fensters **Aufrufliste** können Sie die Funktions\- und Prozeduraufrufe anzeigen, die sich derzeit im Stapel befinden.  
  
 Das Fenster **Aufrufliste** zeigt den Namen der Funktionen und der Programmiersprache an, in der sie geschrieben sind.  Der Name der Funktion oder der Prozedur wird möglicherweise von optionalen Informationen begleitet, z. B. Modulname, Zeilennummer, Parameternamen, \-typen und \-werte.  Die Anzeige dieser optionalen Informationen kann ein\- bzw. ausgeschaltet werden:  
  
 Ein gelber Pfeil bezeichnet den Stapelrahmen, in dem sich der Ausführungszeiger derzeit befindet.  Dies ist standardmäßig der Rahmen, auf den sich die Informationen im Quellcodefenster, **Disassemblyfenster**, **Lokalfenster**, **Überwachungsfenster** und **Auto\-Fenster** beziehen.  Sie können den Kontext im **Aufruflistenfenster** in einen anderen Rahmen im Stapel ändern.  
  
 Wenn für einen Teil der Aufrufliste keine Debugsymbole verfügbar sind, können im **Aufruflistenfenster** für diesen Teil der Aufrufliste möglicherweise keine korrekten Informationen angezeigt werden.  Die folgende Notation wird angezeigt:  
  
 \[Die Rahmen unten sind möglicherweise falsch und\/oder fehlen, für name.dll wurden keine Symbole geladen\]  
  
 Standardmäßig werden bei verwaltetem Code im Fenster **Aufrufliste** Informationen für Nichtbenutzercode ausgeblendet.  Die folgende Notation wird anstelle der ausgeblendeten Informationen angezeigt:  
  
 **\[\<External Code\>\]**  
  
 Beim Nichtbenutzercode handelt es sich um Code, der nicht vom Typ "Mein Code" ist. Sie können angeben, die Aufruflisteninformationen für Nichtbenutzercode anzuzeigen, indem Sie das Kontextmenü verwenden.  
  
 Im Kontextmemü können Sie auswählen, ob Aufrufe zwischen Threads angezeigt werden sollen.  
  
> [!NOTE]
>  Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen unterscheiden.  Um die Einstellungen zu ändern, wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### So zeigen Sie das Fenster "Aufrufliste" im Unterbrechungsmodus oder im Ausführmodus an  
  
-   Wählen Sie im Menü **Debuggen** die Option **Fenster** aus, und klicken Sie auf **Aufrufliste**.  
  
### So ändern Sie die Anzeige optionaler Informationen  
  
-   Klicken Sie mit der rechten Maustaste auf das Fenster **Aufrufliste**, und aktivieren oder deaktivieren Sie **Anzeigen \<***the information that you want***\>**.  
  
### So zeigen Sie Rahmen mit nicht benutzerseitigem Code im Fenster "Aufrufliste" an  
  
-   Klicken Sie mit der rechten Maustaste auf das Fenster **Aufrufliste**, und wählen Sie **Externen Code anzeigen** aus.  
  
### So wechseln Sie in einen anderen Stapelrahmen  
  
1.  Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf den Rahmen, dessen Code und Daten angezeigt werden sollen.  
  
2.  Wählen Sie **Zu Rahmen wechseln** aus.  
  
     Neben dem ausgewählten Rahmen wird ein grüner Pfeil in Form einer Welle angezeigt.  Der Ausführungszeiger verbleibt im ursprünglichen Rahmen, der noch immer durch einen gelben Pfeil gekennzeichnet ist.  Wenn Sie im Menü **Debuggen** den Befehl **Schritt** oder **Weiter** auswählen, wird die Ausführung nicht im neu ausgewählten, sondern im ursprünglichen Rahmen fortgesetzt.  
  
### So zeigen Sie Aufrufe zu bzw. von anderen Threads an  
  
-   Klicken Sie mit der rechten Maustaste auf das Fenster **Aufrufliste**, und wählen Sie **Aufrufe zu\/von anderen Threads einschließen** aus.  
  
### So zeigen Sie den Quellcode für eine Funktion in der Aufrufliste an  
  
-   Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf die Funktion, deren Quellcode Sie anzeigen möchten, und wählen Sie **Gehe zu Quellcode** aus.  
  
### So verfolgen Sie die Aufrufliste visuell  
  
1.  Öffnen Sie das Kontextmenü im Fenster **Aufrufliste**.  Wählen Sie **Aufrufliste in Code Map anzeigen** aus. \(Tastatur: **STRG** \+ **UMSCHALT** \+ **\`**\)  
  
     Siehe [Zuordnen von Methoden in der Aufrufliste beim Debuggen](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
### So zeigen Sie den Disassembly\-Code für eine Funktion in der Aufrufliste an  
  
-   Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf die Funktion, deren Disassemblycode Sie anzeigen möchten, und wählen Sie **Gehe zu Disassembly** aus.  
  
### So führen Sie im Aufruflistenfenster das Programm bis zu einer angegebenen Funktion aus  
  
-   Weitere Informationen erhalten Sie unter [Ausführung bis zu einer angegebenen Position oder Funktion](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Run_to_a_specified_location_or_function).  
  
### So legen Sie einen Haltepunkt am Exitpunkt eines Funktionsaufrufs fest  
  
-   Weitere Informationen erhalten Sie unter [Festlegen eines Haltepunkts in einer Quellzeile, einer Assemblyanweisung oder einer Aufruflistenfunktion](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_at_a_source_line__assembly_instruction__or_call_stack_function_).  
  
### So laden Sie Symbole für ein Modul  
  
-   Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf den Rahmen mit dem Modul, dessen Symbole Sie erneut laden möchten, und wählen Sie **Symbole laden** aus.  
  
## Laden von Symbolen  
 Im Fenster **Aufrufliste** können Sie Debugsymbole für Code laden, für den derzeit keine Symbole geladen sind.  Bei diesen Symbolen kann es sich um .NET Framework\-Symbole oder Systemsymbole handeln, die von den öffentlichen Microsoft\-Symbolservern heruntergeladen wurden, oder um Symbole in einem Symbolpfad auf dem Computer, den Sie debuggen.  
  
 Siehe [Angeben von Symbol\(PDB\)\- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
#### So laden Sie Symbole  
  
1.  Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf einen Rahmen, für den keine Symbole geladen sind.  Der Rahmen wird abgeblendet.  
  
2.  Zeigen Sie auf **Symbole laden aus**, und klicken Sie dann auf **Microsoft\-Symbolserver** oder **Symbolpfad**.  
  
#### So legen Sie den Symbolpfad fest  
  
1.  Wählen Sie im Fenster **Aufrufliste** im Kontextmenü die Option **Symboleinstellungen** aus.  
  
     Das Dialogfeld **Optionen** wird geöffnet, und die Seite **Symbole** wird angezeigt.  
  
2.  Klicken Sie auf **Symboleinstellungen**.  
  
3.  Klicken Sie im Dialogfeld **Optionen** auf das Ordnersymbol.  
  
     Im Feld **Speicherorte für Symboldateien \(.pdb\)** wird ein Cursor angezeigt.  
  
4.  Geben Sie einen Verzeichnispfadnamen zum Symbolspeicherort auf dem Computer ein, den Sie debuggen.  Beim lokalen Debuggen ist dies der lokale Computer.  Beim Remotedebuggen ist es der Remotecomputer.  
  
5.  Klicken Sie auf **OK**, um das Dialogfeld **Optionen** zu schließen.  
  
## Siehe auch  
 [Gemischter Code und fehlende Daten im Fenster "Aufrufliste"](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [Gewusst wie: Ändern des numerischen Formats von Debuggerfenstern](../Topic/How%20to:%20Change%20the%20Numeric%20Format%20of%20Debugger%20Windows.md)   
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Angeben von Symbol\(PDB\)\- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)