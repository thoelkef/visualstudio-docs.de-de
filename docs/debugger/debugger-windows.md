---
title: Überprüfen von Daten mithilfe der Debuggerfenster | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 04/25/2018
ms.topic: conceptual
ms.assetid: 4c6fe8f1-b015-4989-bb31-72ebac390026
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e14f1864452edd00237164e14af74330e3c209f7
ms.sourcegitcommit: 91c7f1b525e0c22d938bc4080ba4ceac2483474f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67033008"
---
# <a name="inspect-data-using-debugger-windows-in-visual-studio"></a>Überprüfen von Daten mithilfe von Debuggerfenster in Visual Studio

Sie können die meisten Debuggerfenster beim Debuggen Ihres Programms öffnen. Zum Anzeigen einer Liste von Debuggerfenstern legen Sie einen Haltepunkt fest, und starten Sie das Debuggen. Klicken Sie auf **Debuggen > Fenster**, wenn Sie den Breakpoint erreichen und die Ausführung angehalten wird.

||||
|-|-|-|
|**Fenster**|**Hotkey**|**Siehe Thema**|
|Haltepunkte|STRG+ALT+B|[Verwenden von Haltepunkten](../debugger/using-breakpoints.md)|
|Ausnahmeeinstellungen|STRG+ALT+E|[Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)|
|Output|STRG+ALT+O|[Ausgabefenster](../ide/reference/output-window.md)|
|Überwachen|STRG+ALT+W, (1, 2, 3, 4)|[Fenster "Überwachen" und "Schnellüberwachung"](../debugger/watch-and-quickwatch-windows.md)|
|Schnellüberwachung|UMSCHALT+F9|[Fenster "Überwachen" und "Schnellüberwachung"](../debugger/watch-and-quickwatch-windows.md)|
|Autos|STRG+ALT+V, A|[Fenster „Auto“ und „Lokal“](../debugger/autos-and-locals-windows.md)|
|Locals|STRG+ALT+V, L|[Fenster „Auto“ und „Lokal“](../debugger/autos-and-locals-windows.md)|
|Aufruflisten|STRG+ALT+C|[Vorgehensweise: Use the Call Stack Window (Vorgehensweise: Verwenden des Fensters Aufrufliste)](../debugger/how-to-use-the-call-stack-window.md)|
|Direkt|STRG+ALT+I|[Direktfenster](../ide/reference/immediate-window.md)|
|Parallele Stapel|STRG+UMSCHALT+D, S|[Verwenden des Fensters "Parallele Stapel"](../debugger/using-the-parallel-stacks-window.md)|
|Parallele Überwachung|STRG+UMSCHALT+D, (1, 2, 3, 4)|[Get started Debugging Multithreaded Applications (Erste Schritte zum Debuggen von Multithreadanwendungen)](../debugger/get-started-debugging-multithreaded-apps.md)|
|Threads|STRG+ALT+H|[Debuggen mithilfe des Fensters „Threads“](../debugger/how-to-use-the-threads-window.md)|
|Module|STRG+ALT+U|[Vorgehensweise: Verwenden des Modulfensters](../debugger/how-to-use-the-modules-window.md)|
|GPU-Threads|-|[Vorgehensweise: Verwenden des Fensters „GPU-Threads“](../debugger/how-to-use-the-gpu-threads-window.md)|
|Aufgaben|STRG+UMSCHALT+D, K|[Verwenden des Fensters „Aufgaben“](../debugger/using-the-tasks-window.md)|
|Python Debug Interactive|UMSCHALT+ALT+I|[Interaktive Python-REPL](../python/python-interactive-repl-in-visual-studio.md)|
|JavaScript-Konsole|STRG+ALT+V, C|[Schnellstart: Debuggen von JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md)|
|DOM-Explorer|STRG+ALT+V, D|[Debuggen von Layout mithilfe von DOM Explorer](/visualstudio/debugger/quickstart-debug-html-and-css)|
|Visuelle Echtzeitstruktur|-|[Überprüfen von XAML-Eigenschaften beim Debuggen](../debugger/inspect-xaml-properties-while-debugging.md)|
|Echtzeit-Eigenschaften-Explorer|-|[Überprüfen von XAML-Eigenschaften beim Debuggen](../debugger/inspect-xaml-properties-while-debugging.md)|
|Prozesse|STRG+ALT+Z|[Debuggen von Threads und Prozessen](../debugger/debug-threads-and-processes.md)|
|Arbeitsspeicher|STRG+ALT+M, (1, 2, 3, 4)|[Fenster "Arbeitsspeicher"](../debugger/memory-windows.md)|
|Disassemblierung|STRG+ALT+D|[Vorgehensweise: Verwenden des Disassembierungsfensters](../debugger/how-to-use-the-disassembly-window.md)|
|Register|STRG+ALT+G|[Vorgehensweise: Verwenden des Fensters „Register“](../debugger/how-to-use-the-registers-window.md)|

## <a name="see-also"></a>Siehe auch

[Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)