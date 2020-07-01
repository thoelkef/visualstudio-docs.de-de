---
title: Gleichzeitiges Verwenden mehrerer Profilertools | Microsoft-Dokumentation
ms.date: 4/29/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, multiple tools
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: f72757d46496c3990c0a0d4205753d185078eac7
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332035"
---
# <a name="using-multiple-profiler-tools-simultaneously"></a>Gleichzeitiges Verwenden mehrerer Profilertools

Der Leistungs-Profiler wurde in der Absicht entwickelt, mehrere Tools in derselben Sitzung einzusetzen, um Leistungsprobleme besser zu verstehen. Die meisten Tools im Leistungs-Profiler unterstützen die gleichzeitige Ausführung, wie z. B. die Tools [CPU-Auslastung](../profiling/cpu-usage.md), [.NET Async](../profiling/analyze-async.md) und [Datenbank](../profiling/analyze-database.md). Um Tools gleichzeitig in derselben Diagnosesitzung auszuführen, aktivieren Sie das Kontrollkästchen neben den Tools, und starten Sie dann die Diagnosesitzung.

![Diagnosehub mit allen ausgewählten Tools](../profiling/media/diaghuballtoolsselected.png "Diagnosehub mit allen ausgewählten Tools")

>[!NOTE]
>Bestimmte Tools wie das [.NET-Objektzuordnung](../profiling/dotnet-alloc-tool.md) können aufgrund ihres hohen Aufwands oder anderer technischer Einschränkungen nicht zusammen mit anderen Tools ausgeführt werden.

## <a name="time-filtering"></a>Zeitfilterung 

Während der Analyse werden Zeitfilterungsvorgänge toolübergreifend angewendet, sodass Sie Informationen in einem Tool nutzen können, um einen Zeitbereich einzugrenzen und Daten in einem anderen Tool zu filtern. Dieses Feature hilft, die Analyse auf bestimmte Punkte in einer Ablaufverfolgung zu lenken und den Zustand der Anwendung zu verstehen.

![Diagnosehub mit Zeitfilterung](../profiling/media/diaghubtimefiltering.png "Diagnosehub mit Zeitfilterung")

## <a name="see-also"></a>Siehe auch

- [Optimieren der Profilereinstellungen](../profiling/optimize-profiler-settings.md)
- [Ausführen von Profilerstellungstools mit oder ohne den Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Grundlegendes zu Leistungsauflistungsmethoden](../profiling/understanding-performance-collection-methods-perf-profiler.md)
