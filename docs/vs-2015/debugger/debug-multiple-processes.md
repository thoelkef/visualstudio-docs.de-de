---
title: Debuggen mehrerer Prozesse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 56982a3b5c0a0d8a5cb0b682ab67b6f5eb133dd1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793047"
---
# <a name="debug-multiple-processes"></a>Debuggen mehrerer Prozesse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hier werden folgende Themen beschrieben: Starten von Debuggingprozessen, Wechseln zwischen Prozessen, Unterbrechen und Fortsetzen der Ausführung, schrittweises Ausführen des Quellcodes, Anhalten des Debuggings sowie Beenden und Abtrennen von Prozessen.  
  
##  <a name="BKMK_Contents"></a> Inhalt  
 [Konfigurieren des ausführungsverhaltens mehrerer Prozesse](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Suchen der Quell- und Symboldateien (PDB-Dateien)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Starten von mehreren Prozessen in einer Visual Studio-Projektmappe, Anfügen an einen Prozess, automatisches Starten eines Prozesses im debugger](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Wechseln zwischen Sie Prozessen, unterbrechen Sie und fortsetzen Sie der Ausführung, schrittweises Ausführen des Quellcodes](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Anhalten des Debuggings, beenden und Abtrennen von Prozessen](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
##  <a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a> Konfigurieren des ausführungsverhaltens mehrerer Prozesse  
 Wenn standardmäßig mehrere Prozesse im Debugger ausgeführt werden, wirken sich die Befehle für Unterbrechen, Durchlaufen und Beenden des Debuggers normalerweise auf alle Prozesse aus. Wenn beispielsweise ein Prozess an einem Haltepunkt angehalten wird, wird die Ausführung aller anderen Prozesse auch angehalten. Sie können dieses Standardverhalten ändern, um mehr Kontrolle über die Ziele von Ausführungsbefehlen zu erhalten.  
  
1. Klicken Sie im Menü **Debuggen** auf **Optionen und Einstellungen**.  
  
2. Auf der **Debuggen**, **allgemeine** Deaktivieren der **alle Prozesse anhalten, wenn ein Prozess anhält** Kontrollkästchen.  
  
   ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Suchen der Quell- und Symboldateien (PDB-Dateien)  
 Um zum Quellcode eines Prozesses zu navigieren, muss der Debugger Zugriff auf die Quell- und Symboldateien des Prozesses haben. Weitere Informationen finden Sie unter [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Wenn Sie nicht auf die Dateien eines Prozesses zugreifen können, können Sie mithilfe des Disassemblyfensters navigieren. Finden Sie unter [Vorgehensweise: Verwenden des Disassembierungsfensters](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a> Starten von mehreren Prozessen in einer Visual Studio-Projektmappe, Anfügen an einen Prozess, automatisches Starten eines Prozesses im debugger  
  
-   [Starten Sie das Debuggen mehrerer Prozesse in Visual Studio-Projektmappe](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • [Ändern des Startprojekts](#BKMK_Change_the_startup_project) • [Starten eines bestimmten Projekts in einer Projektmappe](#BKMK_Start_a_specific_project_in_a_solution) • [Starten mehrerer Projekte in einer Lösung](#BKMK_Start_multiple_projects_in_a_solution) • [Anfügen an einen Prozess](#BKMK_Attach_to_a_process) • [Automatisches Starten eines Prozesses im Debugger](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
>  Auch wenn sich das untergeordnete Projekt in derselben Projektmappe befindet, wird der Debugger nicht automatisch an einen untergeordneten Prozess angefügt, der durch einen debuggten Prozess gestartet wird. So debuggen Sie einen untergeordneten Prozess  
> 
> - Fügen Sie den Debugger an den untergeordneten Prozess an, nachdem dieser gestartet wurde.  
> 
>   - oder -   
>   -   Konfigurieren Sie Windows so, dass der untergeordnete Prozess in einer neuen Instanz des Debuggers automatisch gestartet wird.  
  
###  <a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a> Starten Sie das Debuggen mehrerer Prozesse in Visual Studio-Projektmappe  
 Wenn Sie mehr als ein Projekt in einer Visual Studio-Projektmappe haben, die unabhängig ausgeführt werden kann (Projekte, die in separaten Prozessen ausgeführt werden), können Sie auswählen, welche Projekte vom Debugger gestartet werden.  
  
 ![Ändern des Starttyps für ein Projekt](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
####  <a name="BKMK_Change_the_startup_project"></a> Ändern des Startprojekts  
 Um das Startprojekt für eine Lösung zu ändern, wählen Sie das Projekt im Projektmappen-Explorer, und wählen Sie dann **als Startprojekt festlegen** aus dem Kontextmenü.  
  
####  <a name="BKMK_Start_a_specific_project_in_a_solution"></a> Starten Sie ein bestimmtes Projekt in einer Projektmappe  
 Um ein Projekt für eine Projektmappe ohne Ändern der Standard-Startprojekt zu starten, wählen Sie das Projekt im Projektmappen-Explorer, und wählen Sie dann **Debuggen** aus dem Kontextmenü. Dann können Sie **neue Instanz starten** oder **in neue Instanz springen**.  
  
 ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Starten von mehreren Prozessen in einer Visual Studio-Projektmappe, Anfügen an einen Prozess, automatisches Starten eines Prozesses im Debugger](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
####  <a name="BKMK_Start_multiple_projects_in_a_solution"></a> Starten Sie mehrere Projekte in einer Projektmappe  
  
1. Wählen Sie die Projektmappe im Projektmappen-Explorer, und wählen Sie dann **Eigenschaften** im Kontextmenü.  
  
2. Wählen Sie **allgemeine Eigenschaften**, **Startprojekt** auf die **Eigenschaften** Dialogfeld.  
  
3. Für jedes Projekt, das Sie ändern möchten, wählen Sie entweder **starten**, **Starten ohne debugging**, oder **keine**.  
  
   ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Starten von mehreren Prozessen in einer Visual Studio-Projektmappe, Anfügen an einen Prozess, automatisches Starten eines Prozesses im Debugger](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
###  <a name="BKMK_Attach_to_a_process"></a> Fügen an einen Prozess an  
 Der Debugger kann auch mit *Anfügen* auf Programme, die in Prozessen außerhalb von Visual Studio ausgeführt werden, einschließlich Programme, die auf einem Remotegerät ausgeführt werden. Nachdem Sie den Debugger an ein Programm angefügt haben, können Sie dessen Ausführungsbefehle verwenden, den Programmzustand überprüfen usw. Die Möglichkeiten zum Überprüfen des Programms sind ggf. eingeschränkt. Dies hängt davon ab, ob das Programm mit Debuginformationen erstellt wurde, ob Sie Zugriff auf den Quellcode des Programms haben und ob der JIT-Compiler der Common Language Runtime die Debuginformationen verfolgt.  
  
 Finden Sie unter [Anfügen an ausgeführte Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) für Weitere Informationen.  
  
 **Fügen Sie an einen Prozess, der auf dem lokalen Computer ausgeführt wird an**  
  
 Wählen Sie **Debuggen**, **an den Prozess anhängen**. Auf der **an den Prozess anhängen** Dialogfeld Feld, wählen Sie den Prozess aus der **verfügbare Prozesse** aus, und klicken Sie dann auf **Anfügen**.  
  
 ![Fügen Sie zum Verarbeiten (Dialogfeld)](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Automatisches Starten eines Prozesses im debugger  
 In bestimmten Fällen müssen Sie möglicherweise den Startcode für ein Programm debuggen, das von einem anderen Prozess gestartet wird. Zu den Beispielen hierfür gehören Dienste und benutzerdefinierte Setupaktionen. Für diese Szenarios können Sie festlegen, dass der Debugger beim Starten der Anwendung gestartet und automatisch an die Anwendung angefügt wird.  
  
1. Starten Sie den Registrierungs-Editor (**regedit.exe**).  
  
2. Navigieren Sie zu der **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options** Ordner.  
  
3. Wählen Sie den Ordner der Anwendung aus, die Sie im Debugger starten möchten.  
  
    Wenn der Name der app nicht als untergeordneter Ordner aufgeführt ist, wählen Sie **Image File Execution Options** und wählen Sie dann **neu**, **Schlüssel** im Kontextmenü. Wählen Sie den neuen Schlüssel und dann **umbenennen** im Kontextmenü, und geben Sie dann den Namen der app.  
  
4. Wählen Sie im Kontextmenü des Anwendungsordners **neu**, **Zeichenfolgenwert**.  
  
5. Ändern Sie den Namen des neuen Werts von **neuer Wert** zu `debugger`.  
  
6. Wählen Sie im Kontextmenü des debuggereintrags **ändern**.  
  
7. Geben Sie im Dialogfeld Zeichenfolge bearbeiten `vsjitdebugger.exe` in die **Wertdaten** Feld.  
  
    ![Bearbeiten Sie im Dialogfeld Zeichenfolge](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Für automatischen debuggerstart Eintrag im regedit.exe](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Wechseln zwischen Sie Prozessen, unterbrechen Sie und fortsetzen Sie der Ausführung, schrittweises Ausführen des Quellcodes  
  
-   [Wechseln zwischen Prozessen](#BKMK_Switch_between_processes) • [unterbrechen, durchlaufen und Fortsetzen von Befehlen](#BKMK_Break__step__and_continue_commands)  
  
###  <a name="BKMK_Switch_between_processes"></a> Wechseln zwischen Prozessen  
 Sie können beim Debuggen mit mehreren Prozessen verbunden sein, es ist jedoch jeweils nur ein Prozess im Debugger aktiv. Sie können festlegen, dass die aktive oder *aktuelle* verarbeiten, in der Symbolleiste Debugspeicherort oder in der **Prozesse** Fenster. Um zwischen den Prozessen zu wechseln, müssen sich beide Prozesse im Unterbrechungsmodus befinden.  
  
 **Zum Festlegen des aktuellen Prozesses**  
  
- Wählen Sie auf der Symbolleiste Debugspeicherort **Prozess** zum Anzeigen der **Prozess** Listenfeld. Wählen Sie den Prozess aus, den Sie als aktuellen Prozess festlegen möchten.  
  
   ![Wechseln zwischen Prozessen](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   Wenn die **Debugspeicherort** Symbolleiste nicht angezeigt wird, wählen **Tools**, **anpassen**. Auf der **Symbolleisten** Registerkarte **Debugspeicherort**.  
  
- Öffnen der **Prozesse** Fenster (Kontextmenü **Strg + Alt + Z**), suchen Sie den Prozess, die Sie als aktuellen Prozess festlegen möchten, und doppelklicken Sie darauf.  
  
   ![Fenster "Prozesse"](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   Der aktuelle Prozess ist durch einen gelben Pfeil gekennzeichnet.  
  
  Wenn Sie zu einem Projekt wechseln, wird dieses als aktueller Prozess zum Debuggen festgelegt. In den angezeigten Debuggerfenstern ist der Zustand für den aktuellen Prozess angegeben, und alle Befehle für die schrittweise Ausführung beeinflussen nur den aktuellen Prozess.  
  
  ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Wechseln zwischen Prozessen, unterbrechen und Fortsetzen der Ausführung, schrittweises Ausführen des Quellcodes](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
###  <a name="BKMK_Break__step__and_continue_commands"></a> Unterbrechen, durchlaufen und Fortsetzen von Befehlen  
  
> [!NOTE]
>  Standardmäßig beeinflussen die Debuggerbefehle für Unterbrechen, Durchlaufen und Fortsetzen sämtliche Prozesse, die debuggt werden. Um dieses Verhalten zu ändern, finden Sie unter [Konfigurieren des ausführungsverhaltens mehrerer Prozesse](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Befehl**|**Anhalten Sie alle Prozesse, wenn ein Prozess anhält**<br /><br /> Aktiviert (Standard)|**Anhalten Sie alle Prozesse, wenn ein Prozess anhält**<br /><br /> Deaktiviert|  
|**Debuggen von** Menü:<br /><br /> -   **Alle unterbrechen**|Alle Prozesse werden unterbrochen.|Alle Prozesse werden unterbrochen.|  
|**Debuggen von** Menü:<br /><br /> -   **Fortsetzen**|Alle Prozesse werden fortgesetzt.|Alle angehaltenen Prozesse werden fortgesetzt.|  
|**Debuggen von** Menü:<br /><br /> -   **Einzelschritt**<br />-   **Prozedurschritt**<br />-   **Ausführen bis Rücksprung**|Alle Prozesse werden während der aktuellen Prozessschritte ausgeführt.<br /><br /> Anschließend werden alle Prozesse unterbrochen.|Aktuelle Prozessschritte.<br /><br /> Angehaltene Prozesse werden fortgesetzt.<br /><br /> Ausgeführte Prozesse werden fortgesetzt.|  
|**Debuggen von** Menü:<br /><br /> -   **Einzelschritt in aktuellem Prozess**<br />-   **Prozedurschritt in aktuellem Prozess**<br />-   **Ausführen bis Rücksprung aktuellem Prozess**|Nicht zutreffend|Aktuelle Prozessschritte.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|  
|Quellcodefenster<br /><br /> -   **Haltepunkt**|Alle Prozesse werden unterbrochen.|Nur der Prozess im Quellcodefenster wird unterbrochen.|  
|Kontextmenü des Quellcodefensters:<br /><br /> -   **Führen bis Cursor aus**<br /><br /> Das Quellcodefenster muss sich im aktuellen Prozess befinden.|Alle Prozesse werden ausgeführt, während der Prozess im Quellcodefenster bis zum Cursor ausgeführt und dann unterbrochen wird.<br /><br /> Anschließend werden alle anderen Prozesse unterbrochen.|Der Prozess im Quellcodefenster wird bis zum Cursor ausgeführt.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|  
|**Prozesse** Kontext-Menü "Fenster":<br /><br /> -   **Prozess anhalten**|Nicht zutreffend|Der ausgewählte Prozess wird angehalten.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|  
|**Prozesse** Kontext-Menü "Fenster":<br /><br /> -   **Setzen Sie fort**|Nicht zutreffend|Der ausgewählte Prozess wird fortgesetzt.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|  
  
 ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Wechseln zwischen Prozessen, unterbrechen und Fortsetzen der Ausführung, schrittweises Ausführen des Quellcodes](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a> Anhalten des Debuggings, beenden und Abtrennen von Prozessen  
  
- [Beenden, beenden und Abtrennen von Befehlen](#BKMK_Stop__terminate__and_detach_commands)  
  
  Wenn Sie auswählen, wird standardmäßig **Debuggen**, **Debuggen beenden** Wenn mehrere Prozesse im Debugger geöffnet sind, wird der Debugger beendet oder getrennt von allen Prozessen, je nachdem, wie der Prozess, in geöffnet wurde der Debugger:  
  
- Wenn der aktuelle Prozess im Debugger gestartet wurde, wird dieser Prozess beendet.  
  
- Wenn der Debugger an den aktuellen Prozess angefügt wurde, wird er vom Prozess getrennt. Der Prozess wird weiterhin ausgeführt.  
  
  Z. B. Wenn Sie das Debuggen eines Prozesses aus Visual Studio-Projektmappe starten, Anfügen an einen anderen Prozess, der bereits ausgeführt wird, und wählen Sie dann **Debuggen beenden**, wird die Debugsitzung beendet wird, den Prozess, der in Visual Studio gestartet wurde wird beendet, während der Prozess, den von Ihnen angefügten gelassen wird ausgeführt. Sie können die folgenden Schritte ausführen, um die Methode zum Beenden des Debuggings festzulegen.  
  
> [!NOTE]
>  Die **alle Prozesse anhalten, wenn ein Prozess anhält** Option wirkt sich nicht darauf aus, beenden, Debuggen oder zu beenden und Abtrennen von Prozessen.  
  
 **So ändern, wie das Debuggen beenden einen einzelnen Prozess beeinflusst**  
  
-   Öffnen der **Prozesse** Fenster (Kontextmenü **Strg + Alt + Z**). Wählen Sie einen Prozess, und aktivieren bzw. Deaktivieren der **getrennt werden, wenn das Debuggen beendet** Kontrollkästchen.  
  
###  <a name="BKMK_Stop__terminate__and_detach_commands"></a> Beenden, beenden und Abtrennen von Befehlen  
  
|||  
|-|-|  
|**Befehl**|**Beschreibung**|  
|**Debuggen von** Menü:<br /><br /> -   **Beenden des Debuggens**|Es sei denn, das Verhalten von geändert wird **Prozesse** Fenster **nach Beenden des Debuggings trennen** Option:<br /><br /> 1.  Die vom Debugger gestarteten Prozesse werden beendet.<br />2.  Angefügte Prozesse werden vom Debugger getrennt.|  
|**Debuggen von** Menü:<br /><br /> -   **Alle beenden**|Alle Prozesse werden beendet.|  
|**Debuggen von** Menü:<br /><br /> -   **Alle trennen**|Der Debugger wird von allen Prozessen getrennt.|  
|**Prozesse** Kontext-Menü "Fenster":<br /><br /> -   **Trennen eines Prozesses**|Der Debugger wird vom ausgewählten Prozess getrennt.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|  
|**Prozesse** Kontext-Menü "Fenster":<br /><br /> -   **Prozess beenden**|Der ausgewählte Prozess wird beendet.<br /><br /> Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|  
|**Prozesse** Kontext-Menü "Fenster":<br /><br /> -   **Nach Beenden des Debuggings trennen**|Wechselt zwischen dem Verhalten von **Debuggen**, **Debuggen beenden** für den ausgewählten Prozess:<br /><br /> – Aktiviert: Der Debugger wird getrennt vom Prozess.<br />-Deaktiviert: Der Prozess beendet wird.|  
  
 ![Zurück zum Anfang](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Anhalten des Debuggings, beenden und Abtrennen von Prozessen](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
## <a name="see-also"></a>Siehe auch  
 [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Fügen an laufende Prozesse an](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md)   
 [Just-In-Time-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)



