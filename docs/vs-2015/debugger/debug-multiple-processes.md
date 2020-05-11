---
title: Debuggen mehrerer Prozesse | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a2679825d41a6360dde05e7511d607f8be69dfa
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301440"
---
# <a name="debug-multiple-processes"></a>Debuggen mehrerer Prozesse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hier werden folgende Themen beschrieben: Starten von Debuggingprozessen, Wechseln zwischen Prozessen, Unterbrechen und Fortsetzen der Ausführung, schrittweises Ausführen des Quellcodes, Anhalten des Debuggings sowie Beenden und Abtrennen von Prozessen.  
  
## <a name="contents"></a><a name="BKMK_Contents"></a>Inhalt  
 [Konfigurieren des Ausführungsverhaltens mehrerer Prozesse](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Suchen der Quell- und Symboldateien (.pdb)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Starten von mehreren Prozessen in einer VS-Projektmappe, Anfügen an einen Prozess, automatisches Starten eines Prozesses im Debugger](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Wechseln zwischen Prozessen, Unterbrechen und Fortsetzen der Ausführung, schrittweises Ausführen des Quellcodes](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Anhalten des Debuggings, Beenden und Abtrennen von Prozessen](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
## <a name="configure-the-execution-behavior-of-multiple-processes"></a><a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>Konfigurieren des Ausführungsverhaltens mehrerer Prozesse  
 Wenn standardmäßig mehrere Prozesse im Debugger ausgeführt werden, wirken sich die Befehle für Unterbrechen, Durchlaufen und Beenden des Debuggers normalerweise auf alle Prozesse aus. Wenn beispielsweise ein Prozess an einem Haltepunkt angehalten wird, wird die Ausführung aller anderen Prozesse auch angehalten. Sie können dieses Standardverhalten ändern, um mehr Kontrolle über die Ziele von Ausführungsbefehlen zu erhalten.  
  
1. Klicken Sie im Menü **Debuggen** auf **Optionen und Einstellungen**.  
  
2. Deaktivieren Sie auf der Seite **Debugging**, **Allgemein** das Kontrollkästchen Alle Prozesse unterbrechen, wenn ein Prozess das Kontrollkästchen **aufbricht.**  
  
   ![Zurück zu den oberen](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalten](#BKMK_Contents)  
  
## <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Suchen der Quell- und Symboldateien (.pdb)  
 Um zum Quellcode eines Prozesses zu navigieren, muss der Debugger Zugriff auf die Quell- und Symboldateien des Prozesses haben. Siehe [Symbol (.pdb) und Quelldateien angeben](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Wenn Sie nicht auf die Dateien eines Prozesses zugreifen können, können Sie mithilfe des Disassemblyfensters navigieren. Siehe [Gewusst wie: Verwenden des Demontagefensters](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Zurück zu den oberen](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalten](#BKMK_Contents)  
  
## <a name="start-multiple-processes-in-a-vs-solution-attach-to-a-process-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a>Starten Mehrerer Prozesse in einer VS-Lösung, Anfügen an einen Prozess, automatisches Starten eines Prozesses im Debugger  
  
- [Starten Sie das Debuggen mehrerer Prozesse in einer Visual Studio-Projektmappe](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • [Ändern des Startprojekts](#BKMK_Change_the_startup_project) • [Starten eines bestimmten Projekts in einer Projektmappe](#BKMK_Start_a_specific_project_in_a_solution) • [Starten mehrerer Projekte in einer Projektmappe](#BKMK_Start_multiple_projects_in_a_solution) • [An einen Prozess anfügen](#BKMK_Attach_to_a_process) • [Automatisch einen Prozess im Debugger starten](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
> Auch wenn sich das untergeordnete Projekt in derselben Projektmappe befindet, wird der Debugger nicht automatisch an einen untergeordneten Prozess angefügt, der durch einen debuggten Prozess gestartet wird. So debuggen Sie einen untergeordneten Prozess  
> 
> - Fügen Sie den Debugger an den untergeordneten Prozess an, nachdem dieser gestartet wurde.  
> 
>   Oder  
>   - Konfigurieren Sie Windows so, dass der untergeordnete Prozess in einer neuen Instanz des Debuggers automatisch gestartet wird.  
  
### <a name="start-debugging-multiple-processes-in-a-visual-studio-solution"></a><a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a>Starten des Debuggens mehrerer Prozesse in einer Visual Studio-Lösung  
 Wenn Sie mehr als ein Projekt in einer Visual Studio-Projektmappe haben, die unabhängig ausgeführt werden kann (Projekte, die in separaten Prozessen ausgeführt werden), können Sie auswählen, welche Projekte vom Debugger gestartet werden.  
  
 ![Starttyp wird für ein Projekt geändert](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
#### <a name="change-the-startup-project"></a><a name="BKMK_Change_the_startup_project"></a>Ändern des Startprojekts  
 Um das Startprojekt für eine Projektmappe zu ändern, wählen Sie das Projekt im Projektmappen-Explorer aus, und wählen Sie dann im Kontextmenü **als Startprojekt festlegen** aus.  
  
#### <a name="start-a-specific-project-in-a-solution"></a><a name="BKMK_Start_a_specific_project_in_a_solution"></a>Starten eines bestimmten Projekts in einer Projektmappe  
 Um ein Projekt für eine Projektmappe zu starten, ohne das Standardstartprojekt zu ändern, wählen Sie das Projekt im Projektmappen-Explorer aus, und wählen Sie dann im Kontextmenü **Debuggen** aus. Sie können dann **Neue Instanz starten** oder Schritt in neue **Instanz**wählen.  
  
 ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Mehrere Prozesse in einer VS-Lösung starten, an einen Prozess anhängen, automatisch einen Prozess im Debugger starten](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Zurück zu den oberen](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalten](#BKMK_Contents)  
  
#### <a name="start-multiple-projects-in-a-solution"></a><a name="BKMK_Start_multiple_projects_in_a_solution"></a>Starten mehrerer Projekte in einer Projektmappe  
  
1. Wählen Sie die Projektmappe im Projektmappen-Explorer aus, und wählen Sie dann **Eigenschaften** im Kontextmenü aus.  
  
2. Wählen Sie im Dialogfeld **Eigenschaften** die Option **Allgemeine Eigenschaften**, **Startprojekt** aus.  
  
3. Wählen Sie für jedes Projekt, das Sie ändern möchten, entweder **Start**, **Start ohne Debugging**oder **Keine**.  
  
   ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Mehrere Prozesse in einer VS-Lösung starten, an einen Prozess anhängen, automatisch einen Prozess im Debugger starten](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![Zurück zu den oberen](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalten](#BKMK_Contents)  
  
### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a>An einen Prozess anfügen  
 Der Debugger kann auch an Programme *angefügt* werden, die in Prozessen außerhalb von Visual Studio ausgeführt werden, einschließlich Programmen, die auf einem Remotegerät ausgeführt werden. Nachdem Sie den Debugger an ein Programm angefügt haben, können Sie dessen Ausführungsbefehle verwenden, den Programmzustand überprüfen usw. Die Möglichkeiten zum Überprüfen des Programms sind ggf. eingeschränkt. Dies hängt davon ab, ob das Programm mit Debuginformationen erstellt wurde, ob Sie Zugriff auf den Quellcode des Programms haben und ob der JIT-Compiler der Common Language Runtime die Debuginformationen verfolgt.  
  
 Weitere Informationen finden Sie [unter Anfügen an laufende Prozesse.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
 **Anfügen an einen auf dem lokalen Computer ausgeführten Prozess**  
  
 Wählen Sie **Debug**, **Attach to Process**. Wählen Sie im Dialogfeld **An Prozess anfügen** den Prozess aus der Liste **Verfügbare Prozesse** aus, und wählen Sie dann **Anfügen**aus.  
  
 ![An das Dialogfeld Prozess anfügen](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Zurück zu den oberen](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalten](#BKMK_Contents)  
  
### <a name="automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Automatisches Starten eines Prozesses im Debugger  
 In bestimmten Fällen müssen Sie möglicherweise den Startcode für ein Programm debuggen, das von einem anderen Prozess gestartet wird. Zu den Beispielen hierfür gehören Dienste und benutzerdefinierte Setupaktionen. Für diese Szenarios können Sie festlegen, dass der Debugger beim Starten der Anwendung gestartet und automatisch an die Anwendung angefügt wird.  
  
1. Starten Sie den Registrierungs-Editor (**regedit.exe**).  
  
2. Navigieren Sie zum Ordner **HKEY_LOCAL_MACHINE-Software-Microsoft-Windows-NT-CurrentVersion-Bild-Dateiausführungsoptionen.**  
  
3. Wählen Sie den Ordner der Anwendung aus, die Sie im Debugger starten möchten.  
  
    Wenn der Name der App nicht als untergeordneter Ordner aufgeführt ist, wählen Sie **Bilddateiausführungsoptionen** aus, und wählen Sie dann Im Kontextmenü **Neue**, **Taste** aus. Wählen Sie die neue Taste aus, wählen Sie im Kontextmenü **umbenennen** aus, und geben Sie dann den Namen der App ein.  
  
4. Wählen Sie im Kontextmenü des App-Ordners **Neu**, **String Value**.  
  
5. Ändern Sie den Namen des neuen `debugger`Werts von Neuer **Wert** in .  
  
6. Wählen Sie im Kontextmenü des Debuggereintrags Die Option **Ändern**aus.  
  
7. Geben Sie `vsjitdebugger.exe` im Dialogfeld String bearbeiten in das Feld **Wertdaten** ein.  
  
    ![Dialogfeld "Zeichenfolge bearbeiten"](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Eintrag für automatischen Debuggerstart in "regedit.exe"](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![Zurück zu den oberen](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalten](#BKMK_Contents)  
  
## <a name="switch-processes-break-and-continue-execution-step-through-source"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Wechseln von Prozessen, Unterbrechung und Fortsetzung der Ausführung, Schritt durch Quelle  
  
- [Wechseln zwischen Prozessen](#BKMK_Switch_between_processes) • [Befehlsbefehle unterbrechen, stufen und fortsetzen](#BKMK_Break__step__and_continue_commands)  
  
### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Wechseln zwischen Prozessen  
 Sie können beim Debuggen mit mehreren Prozessen verbunden sein, es ist jedoch jeweils nur ein Prozess im Debugger aktiv. Sie können den aktiven oder *aktuellen* Prozess in der Symbolleiste Debugspeicherort oder im Fenster **Prozesse** festlegen. Um zwischen den Prozessen zu wechseln, müssen sich beide Prozesse im Unterbrechungsmodus befinden.  
  
 **So legen Sie den aktuellen Prozess fest**  
  
- Wählen Sie auf der Symbolleiste "Debugspeicherort" die Option **Prozess** aus, um das Listenfeld **Prozess** anzuzeigen. Wählen Sie den Prozess aus, den Sie als aktuellen Prozess festlegen möchten.  
  
   ![Wechsel zwischen Prozessen](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   Wenn die **Symbolleiste "Speicherort debuggen"** nicht sichtbar ist, wählen Sie **Extras**, **Anpassen**aus. Wählen Sie auf der Registerkarte **Symbolleisten** die Option **Speicherort debuggen**aus.  
  
- Öffnen Sie das Fenster **Prozesse** (Verknüpfung **Strg+Alt+Z**), suchen Sie den Prozess, den Sie als aktuellen Prozess festlegen möchten, und doppelklicken Sie darauf.  
  
   ![Prozessfenster](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   Der aktuelle Prozess ist durch einen gelben Pfeil gekennzeichnet.  
  
  Wenn Sie zu einem Projekt wechseln, wird dieses als aktueller Prozess zum Debuggen festgelegt. In den angezeigten Debuggerfenstern ist der Zustand für den aktuellen Prozess angegeben, und alle Befehle für die schrittweise Ausführung beeinflussen nur den aktuellen Prozess.  
  
  ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Switch-Prozesse, unterbrechen und die Ausführung fortsetzen, Schritt durch Quelle](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![Zurück zu den oberen](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalten](#BKMK_Contents)  
  
### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Befehle für Unterbrechen, Durchlaufen und Fortsetzen  
  
> [!NOTE]
> Standardmäßig beeinflussen die Debuggerbefehle für Unterbrechen, Durchlaufen und Fortsetzen sämtliche Prozesse, die debuggt werden. Informationen zum Ändern dieses Verhaltens finden Sie unter [Konfigurieren des Ausführungsverhaltens mehrerer Prozesse](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Befehl**|**Alle Prozesse unterbrechen, wenn ein Prozess unterbrochen wird**<br /><br /> Aktiviert (Standard)|**Alle Prozesse unterbrechen, wenn ein Prozess unterbrochen wird**<br /><br /> Gelöscht|  
|**Debugmenü:**<br /><br /> -   **Break All**|Alle Prozesse werden unterbrochen.|Alle Prozesse werden unterbrochen.|  
|**Debugmenü:**<br /><br /> -   **Weiter**|Alle Prozesse werden fortgesetzt.|Alle angehaltenen Prozesse werden fortgesetzt.|  
|**Debugmenü:**<br /><br /> -   **Schritt in**<br />-   **Step Over**<br />-   **Step Out**|Alle Prozesse werden während der aktuellen Prozessschritte ausgeführt.<br /><br /> Anschließend werden alle Prozesse unterbrochen.|Aktuelle Prozessschritte.<br /><br /> Angehaltene Prozesse werden fortgesetzt.<br /><br /> Ausgeführte Prozesse werden fortgesetzt.|  
|**Debugmenü:**<br /><br /> -   **Schritt in den aktuellen Prozess**<br />-   **Schritt über aktuellen Prozess**<br />-   **Schritt aus dem aktuellen Prozess**|–|Aktuelle Prozessschritte.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|  
|Quellcodefenster<br /><br /> -   **Haltepunkt**|Alle Prozesse werden unterbrochen.|Nur der Prozess im Quellcodefenster wird unterbrochen.|  
|Kontextmenü des Quellcodefensters:<br /><br /> -   **Ausführen zum Cursor**<br /><br /> Das Quellcodefenster muss sich im aktuellen Prozess befinden.|Alle Prozesse werden ausgeführt, während der Prozess im Quellcodefenster bis zum Cursor ausgeführt und dann unterbrochen wird.<br /><br /> Anschließend werden alle anderen Prozesse unterbrochen.|Der Prozess im Quellcodefenster wird bis zum Cursor ausgeführt.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|  
|**Kontextmenü für Prozesse:**<br /><br /> -   **Break-Prozess**|–|Der ausgewählte Prozess wird angehalten.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|  
|**Kontextmenü für Prozesse:**<br /><br /> -   **Fortsetzung des Prozesses**|–|Der ausgewählte Prozess wird fortgesetzt.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|  
  
 ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Switch-Prozesse, unterbrechen und die Ausführung fortsetzen, Schritt durch Quelle](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Zurück zu den oberen](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalten](#BKMK_Contents)  
  
## <a name="stop-debugging-terminate-or-detach-from-processes"></a><a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a>Beenden des Debuggens, Beenden oder Trennens von Prozessen  
  
- [Befehle für Anhalten, Beenden und Abtrennen](#BKMK_Stop__terminate__and_detach_commands)  
  
  Wenn Sie Debug **wählen,** beenden Sie das **Debuggen,** wenn mehrere Prozesse im Debugger geöffnet sind, der Debugger beendet oder löst sich standardmäßig von allen Prozessen, je nachdem, wie der Prozess im Debugger geöffnet wurde:  
  
- Wenn der aktuelle Prozess im Debugger gestartet wurde, wird dieser Prozess beendet.  
  
- Wenn der Debugger an den aktuellen Prozess angefügt wurde, wird er vom Prozess getrennt. Der Prozess wird weiterhin ausgeführt.  
  
  Wenn Sie beispielsweise mit dem Debuggen eines Prozesses aus einer Visual Studio-Lösung beginnen, an einen anderen Prozess anfügen, der bereits ausgeführt wird, und dann **das Debuggen beenden**auswählen, wird der in Visual Studio gestartete Prozess beendet, während der von Ihnen angefügte Prozess weiterhin ausgeführt wird. Sie können die folgenden Schritte ausführen, um die Methode zum Beenden des Debuggings festzulegen.  
  
> [!NOTE]
> Die Option **Alle Prozesse unterbrechen, wenn ein Prozess unterbrochen** wird, wirkt sich nicht auf das Beenden des Debuggens oder Beendens und Trennens von Prozessen aus.  
  
 **So ändern Sie die Einstellung, wie "Debuggen beenden" einen einzelnen Prozess beeinflusst**  
  
- Öffnen Sie das **Fenster Prozesse** (Verknüpfung **Strg+Alt+Z**). Aktivieren Sie einen Prozess, und aktivieren oder deaktivieren Sie dann das Kontrollkästchen **Trennen beim Debuggen beendet.**  
  
### <a name="stop-terminate-and-detach-commands"></a><a name="BKMK_Stop__terminate__and_detach_commands"></a>Befehle zum Beenden, Beenden und Trennen  
  
|||  
|-|-|  
|**Befehl**|**Beschreibung**|  
|**Debugmenü:**<br /><br /> -   **Beenden des Debuggens**|Es sei denn, das Verhalten wird durch **Prozesse** Fenster **Trennen beim Debuggen beendet** Option geändert:<br /><br /> 1. Prozesse, die vom Debugger gestartet werden, werden beendet.<br />2. Angefügte Prozesse werden vom Debugger getrennt.|  
|**Debugmenü:**<br /><br /> -   **Beenden Sie alle**|Alle Prozesse werden beendet.|  
|**Debugmenü:**<br /><br /> -   **Alle trennen**|Der Debugger wird von allen Prozessen getrennt.|  
|**Kontextmenü für Prozesse:**<br /><br /> -   **Ablösungsprozess**|Der Debugger wird vom ausgewählten Prozess getrennt.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|  
|**Kontextmenü für Prozesse:**<br /><br /> -   **Beendigungsprozess**|Der ausgewählte Prozess wird beendet.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|  
|**Kontextmenü für Prozesse:**<br /><br /> -   **Trennen beim Debuggen stoppen**|Schaltet das Verhalten von **Debug ,** Beenden **des Debuggens** für den ausgewählten Prozess um:<br /><br /> - Aktiviert: Der Debugger löst sich vom Prozess.<br />- Gelöscht: Der Prozess wird beendet.|  
  
 ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Beenden des Debuggens, Beenden oder Trennens von Prozessen](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Zurück zu den oberen](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalten](#BKMK_Contents)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Symbol (.pdb) und Quelldateien angeben](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [An laufende Prozesse anfügen](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Navigieren durch Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md)   
 [Just-In-Time-Debugging](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
