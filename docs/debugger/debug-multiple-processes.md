---
title: "Debugging von mindestens einem Prozess in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.programs"
  - "vs.debug.processes.attaching"
  - "vs.debug.activeprogram"
  - "vs.debug.attaching"
  - "vs.debug.attachedprocesses"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Debugging von mindestens einem Prozess in Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Hier werden folgende Themen beschrieben: Starten von Debuggingprozessen, Wechseln zwischen Prozessen, Unterbrechen und Fortsetzen der Ausführung, schrittweises Ausführen des Quellcodes, Anhalten des Debuggings sowie Beenden und Abtrennen von Prozessen.  
  
##  <a name="BKMK_Contents"></a> Inhalt  
 [Konfigurieren des Ausführungsverhaltens mehrerer Prozesse](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Suchen der Quell- und Symboldateien (PDB-Dateien)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Starten von mehreren Prozessen in einer VS-Projektmappe, Anfügen an einen Prozess, automatisches Starten eines Prozesses im Debugger](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Wechseln zwischen Prozessen, Unterbrechen und Fortsetzen der Ausführung, schrittweises Ausführen des Quellcodes](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Anhalten des Debuggings, Beenden und Abtrennen von Prozessen](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
##  <a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a> Konfigurieren des Ausführungsverhaltens mehrerer Prozesse  
 Wenn standardmäßig mehrere Prozesse im Debugger ausgeführt werden, wirken sich die Befehle für Unterbrechen, Durchlaufen und Beenden des Debuggers normalerweise auf alle Prozesse aus.  Wenn beispielsweise ein Prozess an einem Haltepunkt angehalten wird, wird die Ausführung aller anderen Prozesse auch angehalten.  Sie können dieses Standardverhalten ändern, um mehr Kontrolle über die Ziele von Ausführungsbefehlen zu erhalten.  
  
1.  Klicken Sie im Menü **Debuggen** auf **Optionen und Einstellungen**.  
  
2.  Deaktivieren Sie im Dialogfeld **Debugging** auf der Seite **Allgemein** das Kontrollkästchen **Alle Prozesse anhalten, wenn ein Prozess anhält**.  
  
 ![Zurück nach oben](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Suchen der Quell\- und Symboldateien \(PDB\-Dateien\)  
 Um zum Quellcode eines Prozesses zu navigieren, muss der Debugger Zugriff auf die Quell\- und Symboldateien des Prozesses haben.  Siehe [Angeben von Symbol\(PDB\)\- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Wenn Sie nicht auf die Dateien eines Prozesses zugreifen können, können Sie mithilfe des Disassemblyfensters navigieren.  Siehe [Gewusst wie: Verwenden des Fensters Disassembly](../debugger/how-to-use-the-disassembly-window.md).  
  
 ![Zurück nach oben](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a> Starten von mehreren Prozessen in einer VS\-Projektmappe, Anfügen an einen Prozess, automatisches Starten eines Prozesses im Debugger  
  
-   [Debuggen von mehreren Prozessen in einer Visual Studio-Projektmappe](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • [Ändern des Startprojekts](#BKMK_Change_the_startup_project) • [Starten eines bestimmten Projekts in einer Projektmappe](#BKMK_Start_a_specific_project_in_a_solution) • [Starten mehrerer Projekte in einer Projektmappe](#BKMK_Start_multiple_projects_in_a_solution) • [Anfügen an einen Prozess](#BKMK_Attach_to_a_process) • [Automatisches Starten eines Prozesses im Debugger](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
>  Auch wenn sich das untergeordnete Projekt in derselben Projektmappe befindet, wird der Debugger nicht automatisch an einen untergeordneten Prozess angefügt, der durch einen debuggten Prozess gestartet wird.  So debuggen Sie einen untergeordneten Prozess  
>   
>  -   Fügen Sie den Debugger an den untergeordneten Prozess an, nachdem dieser gestartet wurde.  
>   
>      \- oder \-  
> -   Konfigurieren Sie Windows so, dass der untergeordnete Prozess in einer neuen Instanz des Debuggers automatisch gestartet wird.  
  
###  <a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a> Debuggen von mehreren Prozessen in einer Visual Studio\-Projektmappe  
 Wenn Sie mehr als ein Projekt in einer Visual Studio\-Projektmappe haben, die unabhängig ausgeführt werden kann \(Projekte, die in separaten Prozessen ausgeführt werden\), können Sie auswählen, welche Projekte vom Debugger gestartet werden.  
  
 ![Starttyp wird für ein Projekt geändert](../debugger/media/dbg_execution_startmultipleprojects.png "DBG\_Execution\_StartMultipleProjects")  
  
####  <a name="BKMK_Change_the_startup_project"></a> Ändern des Startprojekts  
 Um das Startprojekt für eine Projektmappe zu ändern, wählen Sie das Projekt im Projektmappen\-Explorer aus, und wählen Sie anschließend im Kontextmenü die Option **Als Startprojekt festlegen**.  
  
####  <a name="BKMK_Start_a_specific_project_in_a_solution"></a> Starten eines bestimmten Projekts in einer Projektmappe  
 Um ein Projekt für eine Projektmappe ohne Ändern des Standardstartprojekts zu starten, wählen Sie es im Projektmappen\-Explorer aus, und wählen Sie anschließend im Kontextmenü die Option **Debuggen**.  Sie können dann die Option **Neue Instanz starten** oder **In neue Instanz springen** wählen.  
  
 ![Zurück nach oben](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Starten von mehreren Prozessen in einer VS-Projektmappe, Anfügen an einen Prozess, automatisches Starten eines Prozesses im Debugger](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Zurück nach oben](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
####  <a name="BKMK_Start_multiple_projects_in_a_solution"></a> Starten mehrerer Projekte in einer Projektmappe  
  
1.  Wählen Sie die Projektmappe im Projektmappen\-Explorer aus, und wählen dann im Kontextmenü die Option **Eigenschaften**.  
  
2.  Wählen Sie im Dialogfeld **Eigenschaften** die Optionen **Allgemeine Eigenschaften** und **Startprojekt** aus.  
  
3.  Für jedes Projekt, das Sie ändern möchten, wählen Sie entweder **Starten**, **Starten ohne Debugging** oder **Keine** aus.  
  
 ![Zurück nach oben](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Starten von mehreren Prozessen in einer VS-Projektmappe, Anfügen an einen Prozess, automatisches Starten eines Prozesses im Debugger](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Zurück nach oben](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
###  <a name="BKMK_Attach_to_a_process"></a> Anfügen an einen Prozess  
 Der Debugger kann auch an Programme *angefügt* werden, die in Prozessen außerhalb von Visual Studio ausgeführt werden, einschließlich Programme, die auf einem Remotegerät ausgeführt werden.  Nachdem Sie den Debugger an ein Programm angefügt haben, können Sie dessen Ausführungsbefehle verwenden, den Programmzustand überprüfen usw.  Die Möglichkeiten zum Überprüfen des Programms sind ggf. eingeschränkt. Dies hängt davon ab, ob das Programm mit Debuginformationen erstellt wurde, ob Sie Zugriff auf den Quellcode des Programms haben und ob der JIT\-Compiler der Common Language Runtime die Debuginformationen verfolgt.  
  
 Weitere Informationen finden Sie unter [Anhängen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 **Anfügen an einen auf dem lokalen Computer ausgeführten Prozess**  
  
 Wählen Sie **Debuggen**, **An den Prozess anhängen** aus.  Wählen Sie den Prozess im Dialogfeld **An den Prozess anhängen** in der Liste **Verfügbare Prozesse** aus, und klicken Sie dann auf **Anfügen**.  
  
 ![Dialogfeld "An den Prozess anhängen"](../debugger/media/dbg_attachtoprocessdlg.png "DBG\_AttachToProcessDlg")  
  
 ![Zurück nach oben](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Automatisches Starten eines Prozesses im Debugger  
 In bestimmten Fällen müssen Sie möglicherweise den Startcode für ein Programm debuggen, das von einem anderen Prozess gestartet wird.  Zu den Beispielen hierfür gehören Dienste und benutzerdefinierte Setupaktionen.  Für diese Szenarios können Sie festlegen, dass der Debugger beim Starten der Anwendung gestartet und automatisch an die Anwendung angefügt wird.  
  
1.  Starten Sie den Registrierungs\-Editor \(**regedit.exe**\).  
  
2.  Suchen Sie den Ordner **HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Windows NT\\CurrentVersion\\Image File Execution Options**.  
  
3.  Wählen Sie den Ordner der Anwendung aus, die Sie im Debugger starten möchten.  
  
     Wenn der Name der Anwendung nicht als untergeordneter Ordner aufgeführt wird, wählen Sie die Option für **Bilddatei\-Ausführungsoptionen** aus, und wählen Sie dann im Kontextmenü die Optionen **Schlüssel**, **Neu** aus.  Wählen Sie den neuen Schlüssel aus, klicken Sie im Kontextmenü auf **Umbenennen**, und geben Sie dann den Namen der Anwendung ein.  
  
4.  Klicken Sie im Kontextmenü des Anwendungsordners auf **Neu**, **Zeichenfolgenwert**.  
  
5.  Ändern Sie den Namen des neuen Werts von **New Value** zu `Debugger`.  
  
6.  Klicken Sie im Kontextmenü des Debuggereintrags auf **Anpassen**.  
  
7.  Geben Sie im Dialogfeld "Zeichenfolgenwerte bearbeiten" den Eintrag `vsjitdebugger.exe` im Feld **Wertdaten** ein.  
  
     ![Dialogfeld "Zeichenfolge bearbeiten"](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "DBG\_Execution\_AutomaticStart\_EditStringDlg")  
  
 ![Eintrag für automatischen Debuggerstart in "regedit.exe"](../debugger/media/dbg_execution_automaticstart_result.png "DBG\_Execution\_AutomaticStart\_Result")  
  
 ![Zurück nach oben](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Wechseln zwischen Prozessen, Unterbrechen und Fortsetzen der Ausführung, schrittweises Ausführen des Quellcodes  
  
-   [Wechseln zwischen Prozessen](#BKMK_Switch_between_processes) • [Befehle für Unterbrechen, Durchlaufen und Fortsetzen](#BKMK_Break__step__and_continue_commands)  
  
###  <a name="BKMK_Switch_between_processes"></a> Wechseln zwischen Prozessen  
 Sie können beim Debuggen mit mehreren Prozessen verbunden sein, es ist jedoch jeweils nur ein Prozess im Debugger aktiv.  Sie können den aktiven oder *aktuellen* Prozess auf der Symbolleiste "Debugspeicherort" oder im Fenster **Prozesse** festlegen.  Um zwischen den Prozessen zu wechseln, müssen sich beide Prozesse im Unterbrechungsmodus befinden.  
  
 **So legen Sie den aktuellen Prozess fest**  
  
-   Klicken Sie auf der Symbolleiste "Debugspeicherort" auf **Prozess**, um das Listenfeld **Prozess** anzuzeigen.  Wählen Sie den Prozess aus, den Sie als aktuellen Prozess festlegen möchten.  
  
     ![Zwischen Prozessen wechseln](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG\_Execution\_SwitchBetweenModules")  
  
     Wenn die Symbolleiste **Debugspeicherort** nicht sichtbar ist, wählen Sie **Extras**, **Anpassen** aus.  Klicken Sie auf der Registerkarte **Symbolleisten** auf **Debugspeicherort**.  
  
-   Öffnen Sie das Fenster **Prozesse** \(Verknüpfung **Ctrl\+Alt\+Z**\), suchen Sie den Prozess, den Sie als aktuellen Prozess festlegen möchten, und doppelklicken Sie darauf.  
  
     ![Prozessfenster](../debugger/media/dbg_processeswindow.png "DBG\_ProcessesWindow")  
  
     Der aktuelle Prozess ist durch einen gelben Pfeil gekennzeichnet.  
  
 Wenn Sie zu einem Projekt wechseln, wird dieses als aktueller Prozess zum Debuggen festgelegt.  In den angezeigten Debuggerfenstern ist der Zustand für den aktuellen Prozess angegeben, und alle Befehle für die schrittweise Ausführung beeinflussen nur den aktuellen Prozess.  
  
 ![Zurück nach oben](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Wechseln zwischen Prozessen, Unterbrechen und Fortsetzen der Ausführung, schrittweises Ausführen des Quellcodes](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Zurück nach oben](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
###  <a name="BKMK_Break__step__and_continue_commands"></a> Befehle für Unterbrechen, Durchlaufen und Fortsetzen  
  
> [!NOTE]
>  Standardmäßig beeinflussen die Debuggerbefehle für Unterbrechen, Durchlaufen und Fortsetzen sämtliche Prozesse, die debuggt werden.  Um dieses Verhalten zu ändern, finden Sie unter [Konfigurieren des Ausführungsverhaltens mehrerer Prozesse](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Befehl**|**Alle Prozesse anhalten, wenn ein Prozess anhält**<br /><br /> Aktiviert \(Standard\)|**Alle Prozesse anhalten, wenn ein Prozess anhält**<br /><br /> Gelöscht|  
|Menü **Debuggen**:<br /><br /> -   **Alle unterbrechen**|Alle Prozesse werden unterbrochen.|Alle Prozesse werden unterbrochen.|  
|Menü **Debuggen**:<br /><br /> -   **Continue**|Alle Prozesse werden fortgesetzt.|Alle angehaltenen Prozesse werden fortgesetzt.|  
|Menü **Debuggen**:<br /><br /> -   **Einzelschritt**<br />-   **Prozedurschritt**<br />-   **Ausführen bis Rücksprung**|Alle Prozesse werden während der aktuellen Prozessschritte ausgeführt.<br /><br /> Anschließend werden alle Prozesse unterbrochen.|Aktuelle Prozessschritte.<br /><br /> Angehaltene Prozesse werden fortgesetzt.<br /><br /> Ausgeführte Prozesse werden fortgesetzt.|  
|Menü **Debuggen**:<br /><br /> -   **Einzelschritt in aktuellem Prozess**<br />-   **Prozedurschritt in aktuellem Prozess**<br />-   **Ausführen bis Rücksprung in aktuellem Prozess**|Nicht zutreffend|Aktuelle Prozessschritte.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei \(angehaltener Zustand oder Ausführzustand\).|  
|Quellcodefenster<br /><br /> -   **Haltepunkt**|Alle Prozesse werden unterbrochen.|Nur der Prozess im Quellcodefenster wird unterbrochen.|  
|Kontextmenü des Quellcodefensters:<br /><br /> -   **Ausführen bis Cursor**<br /><br /> Das Quellcodefenster muss sich im aktuellen Prozess befinden.|Alle Prozesse werden ausgeführt, während der Prozess im Quellcodefenster bis zum Cursor ausgeführt und dann unterbrochen wird.<br /><br /> Anschließend werden alle anderen Prozesse unterbrochen.|Der Prozess im Quellcodefenster wird bis zum Cursor ausgeführt.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei \(angehaltener Zustand oder Ausführzustand\).|  
|Kontextmenü des Fensters **Prozesse**:<br /><br /> -   **Prozess anhalten**|Nicht zutreffend|Der ausgewählte Prozess wird angehalten.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei \(angehaltener Zustand oder Ausführzustand\).|  
|Kontextmenü des Fensters **Prozesse**:<br /><br /> -   **Prozess fortsetzen**|Nicht zutreffend|Der ausgewählte Prozess wird fortgesetzt.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei \(angehaltener Zustand oder Ausführzustand\).|  
  
 ![Zurück nach oben](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Wechseln zwischen Prozessen, Unterbrechen und Fortsetzen der Ausführung, schrittweises Ausführen des Quellcodes](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Zurück nach oben](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a> Anhalten des Debuggings, Beenden und Abtrennen von Prozessen  
  
-   [Befehle für Anhalten, Beenden und Abtrennen](#BKMK_Stop__terminate__and_detach_commands)  
  
 Durch Auswählen von **Debuggen**, **Debuggen beenden**, während mehrere Prozesse im Debugger geöffnet sind, beendet der Debugger standardmäßig alle Prozesse bzw. wird von allen Prozessen getrennt. Dies hängt davon ab, wie der Prozess im Debugger geöffnet war:  
  
-   Wenn der aktuelle Prozess im Debugger gestartet wurde, wird dieser Prozess beendet.  
  
-   Wenn der Debugger an den aktuellen Prozess angefügt wurde, wird er vom Prozess getrennt. Der Prozess wird weiterhin ausgeführt.  
  
 Wenn Sie beispielsweise das Debuggen eines Prozesses aus einer Visual Studio\-Projektmappe gestartet haben, fügen Sie den Debugger an einen anderen, bereits ausgeführten Prozess an, und wählen Sie dann **Debuggen beenden**. Die Debugsitzung und der in Visual Studio gestartete Prozess werden beendet, während der angefügte Prozess weiterhin ausgeführt wird.  Sie können die folgenden Schritte ausführen, um die Methode zum Beenden des Debuggings festzulegen.  
  
> [!NOTE]
>  Die Option **Alle Prozesse anhalten, wenn ein Prozess anhält** beeinflusst nicht das Anhalten des Debuggings bzw. das Beenden und Abtrennen von Prozessen.  
  
 **So ändern Sie die Einstellung, wie "Debuggen beenden" einen einzelnen Prozess beeinflusst**  
  
-   Öffnen Sie das Fenster **Prozesse** \(Verknüpfung **Ctrl\+Alt\+Z**\).  Wählen Sie einen Prozess aus, und aktivieren oder deaktivieren Sie das Kontrollkästchen **Nach Beenden des Debuggings trennen**.  
  
###  <a name="BKMK_Stop__terminate__and_detach_commands"></a> Befehle für Anhalten, Beenden und Abtrennen  
  
|||  
|-|-|  
|**Befehl**|**Beschreibung**|  
|Menü **Debuggen**:<br /><br /> -   **Debuggen beenden**|Es sei denn, das Verhalten wird von der Option **Nach Beenden des Debuggings trennen** im Fenster **Prozesse** geändert:<br /><br /> 1.  Die vom Debugger gestarteten Prozesse werden beendet.<br />2.  Angefügte Prozesse werden vom Debugger getrennt.|  
|Menü **Debuggen**:<br /><br /> -   **Alle beenden**|Alle Prozesse werden beendet.|  
|Menü **Debuggen**:<br /><br /> -   **Alle trennen**|Der Debugger wird von allen Prozessen getrennt.|  
|Kontextmenü des Fensters **Prozesse**:<br /><br /> -   **Prozess abtrennen**|Der Debugger wird vom ausgewählten Prozess getrennt.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei \(angehaltener Zustand oder Ausführzustand\).|  
|Kontextmenü des Fensters **Prozesse**:<br /><br /> -   **Prozess beenden**|Der ausgewählte Prozess wird beendet.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei \(angehaltener Zustand oder Ausführzustand\).|  
|Kontextmenü des Fensters **Prozesse**:<br /><br /> -   **Nach Beenden des Debuggings trennen**|Wechselt zwischen dem Verhalten von **Debuggen** und **Debuggen beenden** für den ausgewählten Prozess:<br /><br /> -   Aktiviert: Der Debugger wird vom Prozess getrennt.<br />-   Deaktiviert: Der Prozess wird beendet.|  
  
 ![Zurück nach oben](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Anhalten des Debuggings, Beenden und Abtrennen von Prozessen](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Zurück nach oben](~/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
## Siehe auch  
 [Angeben von Symbol\(PDB\)\- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Anhängen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md)   
 [Just\-In\-Time\-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)