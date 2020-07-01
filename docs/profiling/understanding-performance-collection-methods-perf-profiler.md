---
title: Grundlagen zu Leistungserfassungsmethoden | Microsoft-Dokumentation
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords: ''
helpviewer_keywords:
- Performance Profiler, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2017'
ms.workload:
- multiple
ms.openlocfilehash: 03a49763a682f6b98b02fe40ba957efa8f5483c8
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290870"
---
# <a name="understand-performance-collection-methods"></a>Grundlagen zu Leistungsauflistungsmethoden

In diesem Dokument werden die Datenerfassungsmethoden beschrieben, die von Tools im Visual Studio-Leistungsprofiler verwendet werden. 

## <a name="sampling"></a>Sampling

Bei Samplingmethoden für die Profilerstellung werden statistische Daten zu den Aufgaben erfasst, die während einer Profilerstellung von einer Anwendung ausgeführt wurden. Die Datenerfassung erfolgt durch das Sammeln von Informationen zur Anwendung in einem regelmäßigen Intervall oder mit einer Samplingfrequenz, z. B. jede Millisekunde. Anschließend werden diese Daten analysiert, um ein Modell des Zeitaufwands in der Anwendung zu erstellen. Die Samplingmethode ist schlank und wirkt sich kaum auf die Ausführung der Anwendung aus, für die ein Profil erstellt wird. Zu den Tools im Leistungs-Profiler, die die Samplingmethode verwenden, gehört das Tool [CPU-Auslastung](../profiling/cpu-usage.md).

## <a name="instrumentation"></a>Instrumentierung

Bei der Profilerstellung mit Instrumentierung werden detaillierte Informationen zu den Aufgaben gesammelt, die während einer Profilerstellung von einer Anwendung ausgeführt wurden. Die Datenerfassung erfolgt durch Tools, die entweder Code in eine Binärdatei einfügen, der Zeitinformationen erfasst, oder durch die Verwendung von Rückrufhooks, um während der Ausführung einer Anwendung exakte Informationen über die Zeit und Anzahl der Aufrufe zu erfassen und auszugeben. Im Vergleich zu Ansätzen, die auf Sampling basieren, hat die Instrumentierungsmethode einen hohen Aufwand. Zu den Tools im Leistungs-Profiler, die die Instrumentierung verwenden, gehört das Tool [.NET-Objektzuordnung](../profiling/dotnet-alloc-tool.md).