---
title: Debuggen mehrerer Prozesse | Microsoft Docs
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 160e219b6fc2ab314f8d0dd91043c18101f2c3a5
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301182"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Debuggen mehrerer Prozesse (C-, Visual Basic-, C++-Prozesse)

Visual Studio kann eine Lösung mit mehreren Prozessen debuggen. Sie können Prozesse starten und zwischen Ihnen wechseln, die Quelle unterbrechen, fortsetzen und schrittweise durchlaufen, das Debuggen beenden und einzelne Prozesse beenden oder von ihnen trennen.

## <a name="start-debugging-with-multiple-processes"></a>Starten Sie das Debuggen mit mehreren Prozessen

Wenn mehr als ein Projekt in einer Visual Studio-Projektmappe unabhängig ausgeführt werden kann, können Sie auswählen, welches Projekt der Debugger startet. Das aktuelle Startprojekt wird im **Projektmappen-Explorer**fett angezeigt.

Um das Startprojekt zu ändern, klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf ein anderes Projekt, und wählen **Sie Als Startup-Projekt festlegen**aus.

Um mit dem Debuggen eines Projekts aus dem **Projektmappen-Explorer** zu beginnen, ohne es zum Startprojekt zu machen, klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Neue** > **Instanz starten** oder in eine neue **Instanz**springen aus.

**So legen Sie das Startprojekt oder mehrere Projekte aus Projektmappeneigenschaften fest:**

1. Wählen Sie die Projektmappe im **Projektmappen-Explorer** aus, und wählen Sie dann das **Eigenschaftensymbol** in der Symbolleiste aus, oder klicken Sie mit der rechten Maustaste auf die Projektmappe, und wählen Sie **Eigenschaften**aus.

1. Wählen Sie auf der Seite **Eigenschaften** die Option **Common Properties** > **Startup Project**aus.

   ![Starttyp wird für ein Projekt geändert](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. Wählen Sie **Aktuelle Auswahl**, **Einzelnes Startprojekt** und eine Projektdatei oder **Mehrere Startprojekte**aus.

   Wenn Sie **Mehrere Startprojekte**auswählen, können Sie die Startreihenfolge und -aktion für jedes Projekt ändern: **Start**, Start **ohne Debugging**oder **Keine**.

1. Wählen Sie **Anwenden**oder **OK** aus, um das Dialogfeld anzuwenden und zu schließen.

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a>An einen Prozess anfügen

Der Debugger kann auch an Apps *angefügt* werden, die in Prozessen außerhalb von Visual Studio ausgeführt werden, einschließlich auf Remotegeräten. Nachdem Sie an eine App angefügt haben, können Sie den Visual Studio-Debugger verwenden. Das Debuggen von Features ist möglicherweise eingeschränkt. Es hängt davon ab, ob die App mit Debuginformationen erstellt wurde, ob Sie Zugriff auf den Quellcode der App haben und ob der JIT-Compiler Debuginformationen nachverfolgt.

Weitere Informationen finden Sie [unter Anfügen an ausgeführte Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Anfügen an einen laufenden Prozess:**

1. Wenn die App ausgeführt wird, wählen Sie **Debug** > **Attach to Process**aus.

   ![An das Dialogfeld Prozess anfügen](../debugger/media/dbg_attachtoprocessdlg.png "Dialogfeld "An den Prozess anhängen"")

1. Wählen Sie im Dialogfeld **An Prozess anfügen** den Prozess aus der Liste **Verfügbare Prozesse** aus, und wählen Sie dann **Anfügen**aus.

>[!NOTE]
>Auch wenn sich das untergeordnete Projekt in derselben Projektmappe befindet, wird der Debugger nicht automatisch an einen untergeordneten Prozess angefügt, der durch einen debuggten Prozess gestartet wird. Um einen untergeordneten Prozess zu debuggen, fügen Sie entweder an den untergeordneten Prozess an, nachdem er gestartet wurde, oder konfigurieren Sie den Windows-Registrierungs-Editor, um den untergeordneten Prozess in einer neuen Debuggerinstanz zu starten.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Verwenden sie den Registrierungs-Editor, um einen Prozess im Debugger automatisch zu starten.

Manchmal müssen Sie möglicherweise den Startcode für eine App debuggen, die von einem anderen Prozess gestartet wird. Zu den Beispielen hierfür gehören Dienste und benutzerdefinierte Setupaktionen. Sie können den Debugger starten und automatisch an die App anfügen.

1. Starten Sie den Windows-Registrierungs-Editor, indem Sie *regedit.exe*ausführen.

1. Navigieren Sie im Registrierungs-Editor zu den Optionen für **die Ausführung von Dateien in der Registrierung HKEY_LOCAL_MACHINE.**

1. Wählen Sie den Ordner der Anwendung aus, die Sie im Debugger starten möchten.

   Wenn die App nicht als untergeordneter Ordner aufgeführt ist, klicken Sie mit der rechten Maustaste auf **Bilddateiausführungsoptionen**, wählen Sie **Neuen** > **Schlüssel**aus, und geben Sie den App-Namen ein. Oder klicken Sie mit der rechten Maustaste auf den neuen Schlüssel in der Struktur, wählen Sie **Umbenennen**aus, und geben Sie dann den App-Namen ein.

1. Klicken Sie mit der rechten Maustaste auf den neuen Schlüssel in der Struktur, und wählen Sie **Neuer** > **Zeichenfolgenwert**aus.

1. Ändern Sie den Namen des neuen `debugger`Werts von New Value **#1** in .

1. Klicken Sie mit der rechten Maustaste auf **debugger,** und wählen Sie **Ändern**aus.

   ![Dialogfeld "Zeichenfolge bearbeiten"](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "Dialogfeld "Zeichenfolge bearbeiten"")

1. Geben **Edit String** Sie `vsjitdebugger.exe` im Dialogfeld Zeichenfolge bearbeiten in das Feld **Wertdaten** ein, und wählen Sie dann **OK**aus.

   ![Eintrag für automatischen Debuggerstart in "regedit.exe"](../debugger/media/dbg_execution_automaticstart_result.png "Eintrag für automatischen Debuggerstart in "regedit.exe"")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Debuggen mit mehreren Prozessen
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Beim Debuggen einer App mit mehreren Prozessen wirken sich die Befehle zum Aufbrechen, Schrittweisen und Fortsetzen des Debuggers standardmäßig auf alle Prozesse aus. Wenn z. B. ein Prozess an einem Haltepunkt angehalten wird, wird auch die Ausführung aller anderen Prozesse angehalten. Sie können dieses Standardverhalten ändern, um mehr Kontrolle über die Ziele von Ausführungsbefehlen zu erhalten.

**So ändern Sie, ob alle Prozesse angehalten werden, wenn ein Prozess unterbrochen wird:**

- Aktivieren oder deaktivieren Sie unter **Tools** (oder **Debuggen**) > **Options** > **Debugging** > **General**, aktivieren oder deaktivieren Sie das Kontrollkästchen Alle Prozesse unterbrechen, wenn ein Prozess das Kontrollkästchen **aufteilt.**

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Befehle für Unterbrechen, Durchlaufen und Fortsetzen

In der folgenden Tabelle wird das Verhalten von Debugbefehlen beschrieben, wenn das Kontrollkästchen **Alle Prozesse unterbrechen, wenn ein Prozess unterbrochen** wird, aktiviert oder deaktiviert wird:

|**Befehl**|Aktiviert|Deaktiviert|
|-|-|-|
|**Debug**  > **Break Alle**|Alle Prozesse werden unterbrochen.|Alle Prozesse werden unterbrochen.|
|**Debuggen** > **Weiter**|Alle Prozesse werden fortgesetzt.|Alle angehaltenen Prozesse werden fortgesetzt.|
|**Debuggen Sie** > **Step Into**, Step **Over**oder Step **Out**|Alle Prozesse werden während der aktuellen Prozessschritte ausgeführt. <br />Anschließend werden alle Prozesse unterbrochen.|Aktuelle Prozessschritte. <br />Angehaltene Prozesse werden fortgesetzt. <br />Ausgeführte Prozesse werden fortgesetzt.|
|**DebugSchritt** > **in den aktuellen Prozess**, Schritt über aktuellen **Prozess**oder Schritt aus dem aktuellen **Prozess**|–|Aktuelle Prozessschritte.<br />Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|
|Quellfenster **Breakpoint**|Alle Prozesse werden unterbrochen.|Nur der Prozess im Quellcodefenster wird unterbrochen.|
|Quellfenster **Zum Cursor ausführen**<br />Das Quellcodefenster muss sich im aktuellen Prozess befinden.|Alle Prozesse werden ausgeführt, während der Prozess im Quellcodefenster bis zum Cursor ausgeführt und dann unterbrochen wird.<br />Anschließend werden alle anderen Prozesse unterbrochen.|Der Prozess im Quellcodefenster wird bis zum Cursor ausgeführt.<br />Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|
|**Prozessfenster** > **Unterbrechungsprozess**|–|Der ausgewählte Prozess wird angehalten.<br />Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|
|**Prozessfenster** > **Prozess fortsetzen**|–|Der ausgewählte Prozess wird fortgesetzt.<br />Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Suchen der Quell- und Symboldateien (.pdb)
Um im Quellcode eines Prozesses zu navigieren, benötigt der Debugger Zugriff auf seine Quelldateien und Symboldateien. Weitere Informationen finden Sie unter [Symbol (.pdb) und Quelldateien angeben](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Wenn Sie nicht auf die Dateien für einen Prozess zugreifen können, können Sie über das **Fenster Demontage** navigieren. Weitere Informationen finden Sie unter [Gewusst wie: Verwenden des Demontagefensters](../debugger/how-to-use-the-disassembly-window.md).

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Wechseln zwischen Prozessen

Sie können beim Debuggen an mehrere Prozesse anfügen, aber nur ein Prozess ist im Debugger zu einem bestimmten Zeitpunkt aktiv. Sie können den aktiven bzw. *aktuellen* Prozess auf der Symbolleiste **Debugspeicherort** oder im Fenster **Prozesse** festlegen. Um zwischen den Prozessen zu wechseln, müssen sich beide Prozesse im Unterbrechungsmodus befinden.

**So legen Sie den aktuellen Prozess über die Symbolleiste Debugspeicherort fest:**

1. Um die **Symbolleiste Debugspeicherort zu** öffnen, wählen Sie**Symbolleisten** > **Debugposition** **anzeigen** > aus.

1. Wählen Sie während des Debuggens auf der Symbolleiste **Debugspeicherort** den Prozess aus, den Sie als aktuellen Prozess festlegen möchten, aus der Dropdown-Liste **Prozess** aus.

   ![Wechsel zwischen Prozessen](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**So legen Sie den aktuellen Prozess aus dem Fenster Prozesse fest:**

1. Um das **Fenster Prozesse** zu öffnen, wählen Sie beim Debuggen Die Option**Windows** > **Windows-Prozesse** **debuggen** > aus.

1. Im Fenster **Prozesse** wird der aktuelle Prozess durch einen gelben Pfeil markiert. Doppelklicken Sie auf den Prozess, den Sie als aktuellen Prozess festlegen möchten.

   ![Prozessfenster](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Durch das Wechseln zu einem Prozess wird er als aktueller Prozess für Debugging-Zwecke festgelegt. Debuggerfenster zeigen den Status für den aktuellen Prozess an, und Schrittbefehle wirken sich nur auf den aktuellen Prozess aus.

## <a name="stop-debugging-with-multiple-processes"></a>Beenden des Debuggens mit mehreren Prozessen

Wenn Sie > **Debugstopp-Debuggen**auswählen, wird der Debugger standardmäßig von allen Prozessen beendet oder detausen. **Debug**

- Wenn der aktuelle Prozess im Debugger gestartet wurde, wird der Prozess beendet.

- Wenn der Debugger an den aktuellen Prozess angefügt wurde, wird er vom Prozess getrennt. Der Prozess wird weiterhin ausgeführt.

Wenn Sie mit dem Debuggen eines Prozesses aus einer Visual Studio-Lösung beginnen, fügen Sie ihn an einen anderen Prozess an, der bereits ausgeführt wird, und wählen Sie dann **Debuggen beenden**aus, die Debugsitzung wird beendet. Der Prozess, der in Visual Studio gestartet wurde, wird beendet, während der Prozess, den Sie an ihn angefügt haben, weiterhin ausgeführt wird.

Um zu steuern, wie sich das **Beenden des Debuggens** auf einen einzelnen Prozess auswirkt, klicken Sie im Fenster **Prozesse** mit der rechten Maustaste auf einen Prozess, und aktivieren oder deaktivieren Sie dann das Kontrollkästchen Trennen, wenn das **Debuggen beendet wird.**

>[!NOTE]
>Die Option Alle Prozesse unterbrechen, wenn ein Prozess die Debuggeroption **aufbricht,** wirkt sich nicht auf das Beenden, Beenden oder Trennen von Prozessen aus.

### <a name="stop-terminate-and-detach-commands"></a>Befehle für Anhalten, Beenden und Abtrennen

In der folgenden Tabelle wird das Verhalten der Befehle zum Beenden, Beenden und Trennen des Debuggers mit mehreren Prozessen beschrieben:

|**Befehl**|**Beschreibung**|
|-|-|
|**Debug** > **Debug-Stopp-Debuggen**|Sofern das Verhalten im **Fenster Prozesse** nicht geändert wird, werden vom Debugger gestartete Prozesse beendet, und angefügte Prozesse werden getrennt.|
|**Debug-Beenden** > **Aller**|Alle Prozesse werden beendet.|
|**Debug** > **Debug-Ablösen Von Allen**|Der Debugger wird von allen Prozessen getrennt.|
|**Prozesse** Fenster > **Trennen des Prozesses**|Der Debugger wird vom ausgewählten Prozess getrennt.<br />Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|
|**Prozessfenster** > **Prozess beenden**|Der ausgewählte Prozess wird beendet.<br />Andere Prozesse behalten ihren vorhandenen Zustand bei (angehaltener Zustand oder Ausführzustand).|
|**Verarbeitet** das Fenster > **Trennen, wenn das Debuggen beendet wird**|Wenn diese Option ausgewählt ist, löst sich das **Debuggen von** > **Debugstopp** vom ausgewählten Prozess. <br />Wenn diese Option nicht ausgewählt ist, beendet > **DebugStopp-Debuggen** den ausgewählten Prozess. **Debug** |

## <a name="see-also"></a>Weitere Informationen

- [Symbol (.pdb) und Quelldateien angeben](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [An laufende Prozesse anfügen](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Navigating through code with the debugger (Navigieren im Code mit dem Debugger)](../debugger/navigating-through-code-with-the-debugger.md)
- [Just-In-Time-Debugging](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)