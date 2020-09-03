---
title: Debuggen mehrerer Prozesse | Microsoft-Dokumentation
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
ms.openlocfilehash: 97d98522e011023cb3a021a69c9a82e8bb34cef3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533275"
---
# <a name="debug-multiple-processes"></a>Debuggen mehrerer Prozesse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hier werden folgende Themen beschrieben: Starten von Debuggingprozessen, Wechseln zwischen Prozessen, Unterbrechen und Fortsetzen der Ausführung, schrittweises Ausführen des Quellcodes, Anhalten des Debuggings sowie Beenden und Abtrennen von Prozessen.  
  
## <a name="contents"></a><a name="BKMK_Contents"></a> Inhalt  
 [Konfigurieren des Ausführungsverhaltens mehrerer Prozesse](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Suchen der Quell-und Symbol Dateien (. pdb)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Starten von mehreren Prozessen in einer VS-Projektmappe, Anfügen an einen Prozess, automatisches Starten eines Prozesses im Debugger](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Wechseln zwischen Prozessen, Unterbrechen und Fortsetzen der Ausführung, schrittweises Ausführen des Quellcodes](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Anhalten des Debuggings, Beenden und Abtrennen von Prozessen](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
## <a name="configure-the-execution-behavior-of-multiple-processes"></a><a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a> Konfigurieren des Ausführungs Verhaltens mehrerer Prozesse  
 Wenn standardmäßig mehrere Prozesse im Debugger ausgeführt werden, wirken sich die Befehle für Unterbrechen, Durchlaufen und Beenden des Debuggers normalerweise auf alle Prozesse aus. Wenn beispielsweise ein Prozess an einem Haltepunkt angehalten wird, wird die Ausführung aller anderen Prozesse auch angehalten. Sie können dieses Standardverhalten ändern, um mehr Kontrolle über die Ziele von Ausführungsbefehlen zu erhalten.  
  
1. Klicken Sie im Menü **Debuggen** auf **Optionen und Einstellungen**.  
  
2. Deaktivieren Sie auf der Seite **Debuggen**, **Allgemein** das Kontrollkästchen **alle Prozesse anhalten, wenn ein Prozess unterbrochen** wird.  
  
   ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
## <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Suchen der Quell- und Symboldateien (.pdb)  
 Um zum Quellcode eines Prozesses zu navigieren, muss der Debugger Zugriff auf die Quell- und Symboldateien des Prozesses haben. Weitere Informationen finden Sie unter [Angeben von Symbol-(PDB-) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Wenn Sie nicht auf die Dateien eines Prozesses zugreifen können, können Sie mithilfe des Disassemblyfensters navigieren. Siehe Gewusst [wie: Verwenden des Disassemblyfensters](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
## <a name="start-multiple-processes-in-a-vs-solution-attach-to-a-process-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a> Starten mehrerer Prozesse in einer vs-Projekt Mappe, Anfügen an einen Prozess, automatisches Starten eines Prozesses im Debugger  
  
- [Starten des Debuggens mehrerer Prozesse in einer Visual Studio](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) -Projekt Mappe • [Ändern des Start Projekts](#BKMK_Change_the_startup_project) • [Starten eines bestimmten Projekts in einer Projekt](#BKMK_Start_a_specific_project_in_a_solution) Mappe • [Starten mehrerer Projekte in einer](#BKMK_Start_multiple_projects_in_a_solution) Projekt Mappe • [Anfügen an einen Prozess](#BKMK_Attach_to_a_process) • [Automatisches Starten eines Prozesses im Debugger](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
> Auch wenn sich das untergeordnete Projekt in derselben Projektmappe befindet, wird der Debugger nicht automatisch an einen untergeordneten Prozess angefügt, der durch einen debuggten Prozess gestartet wird. So debuggen Sie einen untergeordneten Prozess  
> 
> - Fügen Sie den Debugger an den untergeordneten Prozess an, nachdem dieser gestartet wurde.  
> 
>   Oder  
>   - Konfigurieren Sie Windows so, dass der untergeordnete Prozess in einer neuen Instanz des Debuggers automatisch gestartet wird.  
  
### <a name="start-debugging-multiple-processes-in-a-visual-studio-solution"></a><a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a> Starten des Debuggens mehrerer Prozesse in einer Visual Studio-Projekt Mappe  
 Wenn Sie mehr als ein Projekt in einer Visual Studio-Projektmappe haben, die unabhängig ausgeführt werden kann (Projekte, die in separaten Prozessen ausgeführt werden), können Sie auswählen, welche Projekte vom Debugger gestartet werden.  
  
 ![Ändern des Starttyps für ein Projekt](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
#### <a name="change-the-startup-project"></a><a name="BKMK_Change_the_startup_project"></a> Ändern des Start Projekts  
 Um das Startprojekt für eine Projekt Mappe zu ändern, wählen Sie das Projekt in Projektmappen-Explorer aus, und wählen Sie dann im Kontextmenü die Option **als Startprojekt festlegen** aus.  
  
#### <a name="start-a-specific-project-in-a-solution"></a><a name="BKMK_Start_a_specific_project_in_a_solution"></a> Starten eines bestimmten Projekts in einer Projekt Mappe  
 Um ein Projekt für eine Projekt Mappe zu starten, ohne das Standard Startprojekt zu ändern, wählen Sie das Projekt in Projektmappen-Explorer aus, und wählen Sie anschließend im Kontextmenü **Debuggen** aus. Anschließend können Sie **neue Instanz starten** oder **in neue Instanz**springen auswählen.  
  
 ![Zurück zum](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Anfang: Starten mehrerer Prozesse in einer vs-Projekt Mappe, Anfügen an einen Prozess, automatisches Starten eines Prozesses im Debugger](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
#### <a name="start-multiple-projects-in-a-solution"></a><a name="BKMK_Start_multiple_projects_in_a_solution"></a> Starten mehrerer Projekte in einer Projekt Mappe  
  
1. Wählen Sie die Projekt Mappe in Projektmappen-Explorer aus, und klicken Sie dann im Kontextmenü auf **Eigenschaften** .  
  
2. Wählen Sie im Dialogfeld **Eigenschaften** die Option **Allgemeine Eigenschaften**, **Startprojekt** aus.  
  
3. Wählen Sie für jedes Projekt, das Sie ändern möchten, entweder **starten**, **Starten ohne Debugging**oder **keine**aus.  
  
   ![Zurück zum](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Anfang: Starten mehrerer Prozesse in einer vs-Projekt Mappe, Anfügen an einen Prozess, automatisches Starten eines Prozesses im Debugger](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> Anfügen an einen Prozess  
 Der Debugger kann auch an Programme angefügt *werden, die* in Prozessen außerhalb von Visual Studio ausgeführt werden, einschließlich Programmen, die auf einem Remote Gerät ausgeführt werden. Nachdem Sie den Debugger an ein Programm angefügt haben, können Sie dessen Ausführungsbefehle verwenden, den Programmzustand überprüfen usw. Die Möglichkeiten zum Überprüfen des Programms sind ggf. eingeschränkt. Dies hängt davon ab, ob das Programm mit Debuginformationen erstellt wurde, ob Sie Zugriff auf den Quellcode des Programms haben und ob der JIT-Compiler der Common Language Runtime die Debuginformationen verfolgt.  
  
 Weitere Informationen finden [Sie unter Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) .  
  
 **Anfügen an einen auf dem lokalen Computer ausgeführten Prozess**  
  
 Wählen Sie **Debuggen**, **an den Prozess anhängen**aus. Wählen Sie im Dialogfeld **an den Prozess anhängen** den Prozess in der Liste **Verfügbare Prozesse** aus, und klicken Sie dann auf **Anfügen**.  
  
 Dialogfeld ![An Prozess anfügen](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
### <a name="automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Automatisches Starten eines Prozesses im Debugger  
 In bestimmten Fällen müssen Sie möglicherweise den Startcode für ein Programm debuggen, das von einem anderen Prozess gestartet wird. Zu den Beispielen hierfür gehören Dienste und benutzerdefinierte Setupaktionen. Für diese Szenarios können Sie festlegen, dass der Debugger beim Starten der Anwendung gestartet und automatisch an die Anwendung angefügt wird.  
  
1. Starten Sie den Registrierungs-Editor (**regedit.exe**).  
  
2. Navigieren Sie zum Ordner **HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options** .  
  
3. Wählen Sie den Ordner der Anwendung aus, die Sie im Debugger starten möchten.  
  
    Wenn der Name der APP nicht als untergeordneter Ordner aufgeführt ist, wählen Sie **Bild Datei Ausführungs Optionen** aus, und klicken Sie dann im Kontextmenü auf **neu**und dann auf **Schlüssel** . Wählen Sie den neuen Schlüssel aus, wählen Sie im Kontextmenü **Umbenennen** aus, und geben Sie dann den Namen der APP ein.  
  
4. Wählen Sie im Kontextmenü des Ordners "App" die Option **neu**, **Zeichen folgen Wert**aus.  
  
5. Ändern Sie den Namen des neuen Werts aus dem **neuen** Wert in `debugger` .  
  
6. Wählen Sie im Kontextmenü des Debuggers den Eintrag **ändern**aus.  
  
7. Geben Sie im Dialogfeld Zeichenfolge bearbeiten `vsjitdebugger.exe` im Feld **Wertdaten** ein.  
  
    ![Dialogfeld "Zeichenfolge bearbeiten"](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Eintrag für automatischen Debuggerstart in „regedit.exe“](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
## <a name="switch-processes-break-and-continue-execution-step-through-source"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Wechseln von Prozessen, unterbrechen und Fortsetzen der Ausführung, schrittweises Ausführen  
  
- [Wechseln zwischen Prozessen](#BKMK_Switch_between_processes) • [Befehle zum Abbrechen, Schritt und fortsetzen](#BKMK_Break__step__and_continue_commands)  
  
### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Wechseln zwischen Prozessen  
 Sie können beim Debuggen mit mehreren Prozessen verbunden sein, es ist jedoch jeweils nur ein Prozess im Debugger aktiv. Sie können den aktiven oder *aktuellen* Prozess auf der Symbolleiste Debugspeicherort oder im Fenster **Prozesse** festlegen. Um zwischen den Prozessen zu wechseln, müssen sich beide Prozesse im Unterbrechungsmodus befinden.  
  
 **So legen Sie den aktuellen Prozess fest**  
  
- Wählen Sie auf der Symbolleiste Debugspeicherort die Option **Prozess** aus, um das Listenfeld **Prozess** anzuzeigen. Wählen Sie den Prozess aus, den Sie als aktuellen Prozess festlegen möchten.  
  
   ![Wechseln zwischen Prozessen](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   Wenn die Symbolleiste **Debugspeicherort** nicht sichtbar ist **, wählen Sie**Extras, **Anpassen**aus. Wählen Sie auf der Registerkarte **Symbolleisten** **Debugspeicherort**aus.  
  
- Öffnen Sie das Fenster **Prozesse** (Tastenkombination **STRG + ALT + Z**), suchen Sie den Prozess, den Sie als aktuellen Prozess festlegen möchten, und doppelklicken Sie darauf.  
  
   ![Fenster „Prozesse“](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   Der aktuelle Prozess ist durch einen gelben Pfeil gekennzeichnet.  
  
  Wenn Sie zu einem Projekt wechseln, wird dieses als aktueller Prozess zum Debuggen festgelegt. In den angezeigten Debuggerfenstern ist der Zustand für den aktuellen Prozess angegeben, und alle Befehle für die schrittweise Ausführung beeinflussen nur den aktuellen Prozess.  
  
  ![Zurück zu den ersten](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [switchprozessen, unterbrechen und Fortsetzen der Ausführung, schrittweises Ausführen der Quelle](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Befehle für Unterbrechen, Durchlaufen und Fortsetzen  
  
> [!NOTE]
> Standardmäßig beeinflussen die Debuggerbefehle für Unterbrechen, Durchlaufen und Fortsetzen sämtliche Prozesse, die debuggt werden. Informationen zum Ändern dieses Verhaltens finden Sie unter [Konfigurieren des Ausführungs Verhaltens mehrerer Prozesse](#BKMK_Configure_the_execution_behavior_of_multiple_processes) .  
  
|**Befehl**|**Alle Prozesse anhalten, wenn ein Prozess unterbrochen wird**<br /><br /> Aktiviert (Standard)|**Alle Prozesse anhalten, wenn ein Prozess unterbrochen wird**<br /><br /> Gelöscht|  
|-|-|-|
|Menü **Debuggen** :<br /><br /> -   **Alle abbrechen**|Alle Prozesse werden unterbrochen.|Alle Prozesse werden unterbrochen.|  
|Menü **Debuggen** :<br /><br /> -   **Auch**|Alle Prozesse werden fortgesetzt.|Alle angehaltenen Prozesse werden fortgesetzt.|  
|Menü **Debuggen** :<br /><br /> -   **Einzelschritt**<br />-   **Prozedur Schritt**<br />-   **Rücksprung**|Alle Prozesse werden während der aktuellen Prozessschritte ausgeführt.<br /><br /> Anschließend werden alle Prozesse unterbrochen.|Aktuelle Prozessschritte.<br /><br /> Angehaltene Prozesse werden fortgesetzt.<br /><br /> Ausgeführte Prozesse werden fortgesetzt.|  
|Menü **Debuggen** :<br /><br /> -   **Aktuellen Prozessschritt Weise ausführen**<br />-   **Aktuellen Prozess überspringen**<br />-   **Aktuellen Prozess ausführen**|Nicht zutreffend|Aktuelle Prozessschritte.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|  
|Quellcodefenster<br /><br /> -   **Haltepunkt**|Alle Prozesse werden unterbrochen.|Nur der Prozess im Quellcodefenster wird unterbrochen.|  
|Kontextmenü des Quellcodefensters:<br /><br /> -   **Ausführen bis Cursor**<br /><br /> Das Quellcodefenster muss sich im aktuellen Prozess befinden.|Alle Prozesse werden ausgeführt, während der Prozess im Quellcodefenster bis zum Cursor ausgeführt und dann unterbrochen wird.<br /><br /> Anschließend werden alle anderen Prozesse unterbrochen.|Der Prozess im Quellcodefenster wird bis zum Cursor ausgeführt.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|  
|Kontextmenü des **Prozess** Fensters:<br /><br /> -   **Prozess Abbrechen**|Nicht zutreffend|Der ausgewählte Prozess wird angehalten.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|  
|Kontextmenü des **Prozess** Fensters:<br /><br /> -   **Prozess fortsetzen**|Nicht zutreffend|Der ausgewählte Prozess wird fortgesetzt.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|  
  
 ![Zurück zu den ersten](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [switchprozessen, unterbrechen und Fortsetzen der Ausführung, schrittweises Ausführen der Quelle](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
## <a name="stop-debugging-terminate-or-detach-from-processes"></a><a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a> Beenden des Debuggens, beenden oder Trennen von Prozessen  
  
- [Befehle für Anhalten, Beenden und Abtrennen](#BKMK_Stop__terminate__and_detach_commands)  
  
  Wenn Sie **Debuggen**, **Debuggen beenden** , wenn mehrere Prozesse im Debugger geöffnet sind, wird der Debugger standardmäßig beendet oder von allen Prozessen getrennt, je nachdem, wie der Prozess im Debugger geöffnet wurde:  
  
- Wenn der aktuelle Prozess im Debugger gestartet wurde, wird dieser Prozess beendet.  
  
- Wenn der Debugger an den aktuellen Prozess angefügt wurde, wird er vom Prozess getrennt. Der Prozess wird weiterhin ausgeführt.  
  
  Wenn Sie z. b. mit dem Debuggen eines Prozesses aus einer Visual Studio-Projekt Mappe beginnen, an einen anderen Prozess anfügen, der bereits ausgeführt wird, und dann **Debuggen beenden**, wird die Debugsitzung beendet, der in Visual Studio gestartete Prozess wird beendet, während der angefügte Prozess weiterhin ausgeführt wird. Sie können die folgenden Schritte ausführen, um die Methode zum Beenden des Debuggings festzulegen.  
  
> [!NOTE]
> Die Option **alle Prozesse anhalten, wenn ein Prozess unterbrochen** nicht das Beenden des Debuggens oder das Beenden und trennen von Prozessen beeinträchtigt.  
  
 **So ändern Sie die Einstellung, wie "Debuggen beenden" einen einzelnen Prozess beeinflusst**  
  
- Öffnen Sie das Fenster **Prozesse** (Tastenkombination **STRG + ALT + Z**). Wählen Sie einen Prozess aus, und aktivieren oder deaktivieren Sie das Kontrollkästchen **beim Beenden des Debuggens trennen** .  
  
### <a name="stop-terminate-and-detach-commands"></a><a name="BKMK_Stop__terminate__and_detach_commands"></a> Beenden, beenden und trennen von Befehlen  
  
|**Befehl**|**Beschreibung**|  
|-|-|  
|Menü **Debuggen** :<br /><br /> -   **Debuggen Abbrechen**|Es sei denn, das Verhalten wird durch die Option zum Trennen von **Prozessen** **beim Debuggen** geändert:<br /><br /> 1. vom Debugger gestartete Prozesse werden beendet.<br />2. angefügte Prozesse werden vom Debugger getrennt.|  
|Menü **Debuggen** :<br /><br /> -   **Alle beenden**|Alle Prozesse werden beendet.|  
|Menü **Debuggen** :<br /><br /> -   **Alle trennen**|Der Debugger wird von allen Prozessen getrennt.|  
|Kontextmenü des **Prozess** Fensters:<br /><br /> -   **Prozess trennen**|Der Debugger wird vom ausgewählten Prozess getrennt.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|  
|Kontextmenü des **Prozess** Fensters:<br /><br /> -   **Prozess beenden**|Der ausgewählte Prozess wird beendet.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|  
|Kontextmenü des **Prozess** Fensters:<br /><br /> -   **Beim Beenden des Debuggens trennen**|Schaltet das Verhalten des **Debuggens**um und **beendet das Debuggen** für den ausgewählten Prozess:<br /><br /> -Aktiviert: der Debugger trennt den Prozess.<br />-Gelöscht: der Prozess wird beendet.|  
  
 ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Beenden des Debuggens, beenden oder Trennen von Prozessen](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben von Symbol-(PDB-) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Navigieren durch Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md)   
 [Just-in-Time-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
