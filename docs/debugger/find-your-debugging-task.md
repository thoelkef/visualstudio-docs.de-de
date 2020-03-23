---
title: Finden der Debugaufgabe
description: Identifizieren der Debuggerfunktion, mit der Sie Ihre App debuggen können
ms.custom: ''
ms.date: 10/01/2019
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], find your feature
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 792b5e2d40f7299bf019fd3f9c86697bf008c391
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301146"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Suchen der Debugging-Aufgabe in Visual Studio

Wenn Sie Hilfe benötigen, um Ihre Debugaufgabe dem richtigen Feature des Visual Studio-Debuggers zuzuordnen, verwenden Sie die in diesem Artikel bereitgestellten Links. Die Liste der Aufgaben enthält hier allgemeine Aufgaben wie das Anhalten von Code zum Debuggen, das Überprüfen von Variablen und das Senden von Nachrichten an das **Ausgabefenster.** Wenn Sie eine Übersicht über Debugger-Features benötigen, finden Sie stattdessen einen [ersten Blick auf den Debugger.](debugger-feature-tour.md)

## <a name="pause-running-code"></a>Anhalten des ausgeführten Codes

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Anhalten des ausgeführten Codes, um eine Codezeile zu überprüfen, die einen Fehler enthalten kann

Festlegen eines Haltepunkts. Weitere Informationen finden Sie unter [Verwenden von Haltepunkten](using-breakpoints.md).

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Anhalten und überprüfen Sie Ihre App, wenn sie einen bestimmten Status erreicht

Versuchen Sie einen bedingten Haltepunkt, um zu steuern, wo und wann ein Haltepunkt mithilfe der bedingten Logik aktiviert wird. Weitere Informationen finden Sie unter [Breakpoint-Bedingungen](using-breakpoints.md#breakpoint-conditions).

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Anhalten von Code nur, wenn sich die Eigenschaft oder der Wert eines bestimmten Objekts ändert

Legen Sie für C++ einen [Datenhaltepunkt](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)fest. 
::: moniker range=">= vs-2019"
Für Apps, die .NET Core 3 verwenden, können Sie auch einen [Datenhaltepunkt](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed)festlegen.
::: moniker-end

Andernfalls können Sie [eine Objekt-ID mit einem bedingten Haltepunkt nachverfolgen.](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f)

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Pausecode in einer Schleife bei einer bestimmten Iteration

Legen Sie einen Haltepunkt mithilfe der **Trefferanzahl** als Bedingung fest. Weitere Informationen finden Sie unter [Trefferanzahl](using-breakpoints.md#set-a-hit-count-condition).

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>Pausecode am Anfang einer Funktion, wenn Sie den Funktionsnamen kennen, aber nicht seinen Speicherort

Sie können dies mit einem Funktionshaltepunkt tun. Weitere Informationen finden Sie unter [Festlegen von Funktionshaltepunkten](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>Pausencode am Anfang mehrerer Funktionen mit demselben Namen

Wenn Sie über mehrere Funktionen mit demselben Namen verfügen (überladene Funktionen oder Funktionen in verschiedenen Projekten), können Sie einen [Funktionshaltepunkt](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)verwenden.

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Verwalten und verfolgen Sie Ihre Haltepunkte

Verwenden Sie das **Fenster Haltepunkte.** Weitere Informationen finden Sie unter Verwalten von [Haltepunkten](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Pausecode und Debuggen, wenn eine bestimmte behandelte oder nicht behandelte Ausnahme ausgelöst wird

Obwohl der Ausnahmehilfspunkt zeigt, wo ein Fehler aufgetreten ist, können Sie, wenn Sie den bestimmten Fehler anhalten und debuggen möchten, [den Debugger anweisen, zu unterbrechen, wenn eine Ausnahme ausgelöst wird.](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown)

### <a name="set-a-breakpoint-from-the-call-stack"></a>Festlegen eines Haltepunkts aus der Aufrufliste

Wenn Sie Code anhalten und debuggen möchten, während Sie den Ausführungsfluss oder die Anzeige von Funktionen in den **Aufruflistenfenstern** untersuchen, finden Sie weitere Informationen unter [Festlegen eines Haltepunkts im Fenster Aufruflisten](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Pausencode an einer bestimmten Assemblyanweisung

Sie können dies tun, indem [Sie einen Haltepunkt aus dem Demontagefenster festlegen.](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)

## <a name="execute-code"></a>Ausführen von Code

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Lernen Sie die Befehle zum Durchlaufen des Codes beim Debuggen

Weitere Informationen finden Sie unter [Navigieren von Code mit dem Debugger](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Überprüfen von Daten

### <a name="check-the-value-of-variables-while-running-your-app"></a>Überprüfen Sie den Wert von Variablen beim Ausführen Ihrer App

Zeigen Sie mit der Maus auf Variablen, indem Sie [Datentipps verwenden,](view-data-values-in-data-tips-in-the-code-editor.md) oder [überprüfen Sie Variablen im Fenster Autos und Locals](autos-and-locals-windows.md).

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Beobachten des änderungsweisen Wertes einer bestimmten Variablen

Legen Sie eine Uhr auf die Variable fest. Weitere Informationen finden Sie unter [Festlegen einer Uhr für Variablen](watch-and-quickwatch-windows.md).

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Anzeigen von Zeichenfolgen, die für das Debuggerfenster zu lang sind

Öffnen Sie die integrierte [Zeichenfolgenvisualisierung](view-strings-visualizer.md) während des Debuggens.

## <a name="configure-debugging"></a>Konfigurieren des Debuggens

### <a name="customize-information-shown-in-the-debugger"></a>Anpassen der im Debugger angezeigten Informationen

Möglicherweise möchten Sie andere Informationen als den Objekttyp als Wert in verschiedenen Debuggerfenstern anzeigen. Verwenden Sie das [DebuggerDisplay-Attribut](using-the-debuggerdisplay-attribute.md) für den Code "C", "Visual Basic", "F" und "C++/CLI". Für erweiterte Optionen können Sie die Benutzeroberfläche auch anpassen, indem Sie eine [benutzerdefinierte Visualisierung](create-custom-visualizers-of-data.md)erstellen.

Verwenden Sie für systemeigene C++ das [NatVis-Framework](create-custom-views-of-native-objects.md).

### <a name="configure-debugger-settings"></a>Konfigurieren von Debuggereinstellungen

Informationen zum Konfigurieren von Debuggeroptionen und Debuggerprojekteinstellungen finden Sie unter [Debuggereinstellungen und Vorbereitung](debugger-settings-and-preparation.md).

## <a name="additional-tasks"></a>Zusätzliche Aufgaben

### <a name="fix-an-exception"></a>Fix einer Ausnahme

Siehe [Fix a exception](write-better-code-with-visual-studio.md#fix-an-exception).

### <a name="edit-code-during-a-debugging-session"></a>Bearbeiten von Code während einer Debugsitzung

Verwenden Sie [Bearbeiten und fortfahren](edit-and-continue.md)Sie . Verwenden Sie für XAML [XAML Hot Reload](../xaml-tools/xaml-hot-reload.md).

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Senden von Nachrichten an das Ausgabefenster, ohne Code zu ändern

Legen Sie einen Ablaufverfolgungspunkt fest. Weitere Informationen finden Sie unter [Verwenden von Ablaufverfolgungspunkten](using-tracepoints.md).

## <a name="view-the-order-in-which-functions-are-called"></a>Anzeigen der Reihenfolge, in der Funktionen aufgerufen werden

Weitere Informationen finden Sie unter [Anzeigen der Aufrufliste](how-to-use-the-call-stack-window.md).

### <a name="debug-on-remote-machines"></a>Debuggen auf Remotecomputern

Weitere Informationen finden Sie unter [Remote debugging (Remotedebuggen)](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Debuggen einer App, die bereits ausgeführt wird

Weitere Informationen finden [Sie unter Anfügen an einen laufenden Prozess](attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="debug-multithreaded-applications"></a>Debuggen von Multithreadanwendungen

Siehe [Debug-Multithreadanwendungen](debug-multithreaded-applications-in-visual-studio.md).

### <a name="fix-performance-issues"></a>Beheben der Leistungsprobleme

Siehe [Erster Blick auf die Profilerstellungstools](../profiling/profiling-feature-tour.md)