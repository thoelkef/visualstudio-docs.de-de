---
title: Analysieren der Speicherauslastung
ms.custom: seodec18
ms.date: 01/02/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ddb082bf2451759be239d5c16404e82bcd84733
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578161"
---
# <a name="analyze-memory-usage"></a>Analysieren der Speicherauslastung

Zum Ermitteln von Arbeitsspeicherverlusten und ineffizienter Arbeitsspeichernutzung können Sie Tools wie das im Debugger integrierte Speicherauslastungs-Diagnosetool oder die Tools im Leistungs-Profiler verwenden, z. B. das .NET-Objektzuordnungstool und das Speicherauslastungs-Nachbereitungstool. Mit dem Speicherauslastungstool können Sie einen oder mehrere *Momentaufnahmen* des verwalteten und systemeigenen Momentaufnahme-Heaps machen. Sie können Momentaufnahmen von .NET-Apps, ASP.NET-Apps, nativen Apps und Apps im gemischten Modus (.NET und nativ) erfassen. 

Das **Speicherauslastungstool** kann für ein geöffnetes Visual Studio-Projekt oder eine installierte Microsoft Store-App ausgeführt oder an eine ausgeführte App bzw. einen Prozess angefügt werden. Sie können das Tool auf lokalen Computern oder Remotecomputern sowie auf einem Simulator oder Emulator ausführen. Weitere Informationen finden Sie unter [Ausführen von Profilerstellungstools mit oder ohne Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Sie können das **Speicherauslastungstool** mit oder ohne Debuggen ausführen. Im Debugger können Sie die Arbeitsspeicher-Profilerstellung aktivieren bzw. deaktivieren und eine objektspezifische Aufschlüsselung der Arbeitsspeicherauslastung anzeigen. Sie können die Ergebnisse der Arbeitsspeicherauslastung anzeigen, wenn die Ausführung pausiert ist, z. B. an einem Breakpoint.

Das **.NET-Tool für die Objektzuordnung** kann nur zur Nachbereitung ausgeführt werden.

Ausführliche Anweisungen zur Verwendung der Arbeitsspeicheranalyse-Tools finden Sie im Tutorial [Analysieren der Arbeitsspeicherauslastung](../profiling/memory-usage.md) und im Artikel [Analysieren der Speicherauslastung mithilfe des .NET-Tools für die Objektzuordnung](../profiling/dotnet-alloc-tool.md).

Unter Windows 7 und höher können Sie die Profilerstellungstools ohne den Debugger verwenden. Windows 8 und höher ist erforderlich, um die Profilerstellungstools mit dem Debugger auszuführen (Fenster **Diagnosetools**).

## <a name="blogs-and-videos"></a>Blogs und Videos

[Analyze CPU and Memory While Debugging (Analysieren der CPU und des Arbeitsspeichers beim Debuggen)](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ Team Blog: Memory Profiling in Visual C++ 2015 (Visual C++-Teamblog: Speicherprofilerstellung in Visual C++ 2015)](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Siehe auch

- [Profilerstellung in Visual Studio](../profiling/index.yml)
- [Einführung in Profilerstellungstools](../profiling/profiling-feature-tour.md)
- [Analysieren der Speicherauslastung ohne den Debugger](../profiling/memory-usage-without-debugging2.md)
