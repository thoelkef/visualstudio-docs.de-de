---
title: Automatisches Anhalten von Features
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8480eb57a08905c2a593adbab519ae793638888
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431240"
---
# <a name="automatic-feature-suspension"></a>Automatisches Anhalten von Features

Wenn der verfügbare Systemspeicher auf 200 MB oder weniger fällt, zeigt Visual Studio die folgende Meldung im Code-Editor an:

![Warnungstext, der die vollständige Lösungsanalyse aussetzt](../code-quality/media/fsa_alert.png)

Wenn Visual Studio einen Speicherzustand mit geringem Arbeitsspeicher erkennt, werden bestimmte erweiterte Funktionen automatisch angehalten, damit es stabil bleibt. Visual Studio funktioniert weiterhin wie bisher, aber seine Leistung wird beeinträchtigt.

In einem Zustand mit geringem Arbeitsspeicher werden die folgenden Aktionen ausgeführt:

- Die Livecodeanalyse für Visual C- und Visual Basic wird auf einen minimalen Umfang reduziert.

- Der Gc-Modus mit niedriger Latenz [(Garbage Collection)](/dotnet/standard/garbage-collection/index) für Visual C- und Visual Basic ist deaktiviert.

- Visual Studio-Caches werden geleert.

## <a name="improve-visual-studio-performance"></a>Verbessern der Visual Studio-Leistung

Tipps und Tricks zur Verbesserung der Visual Studio-Leistung im Umgang mit großen Lösungen oder Speicherarmen finden Sie unter [Leistungsüberlegungen für große Lösungen](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>Live-Code-Analyse wird auf minimalen Umfang reduziert

Standardmäßig wird die Livecodeanalyse für geöffnete Dokumente und Projekte ausgeführt. Sie können diesen Analysebereich anpassen, um auf das aktuelle Dokument reduziert oder auf die gesamte Lösung erweitert zu werden. Weitere Informationen finden Sie unter [Gewusst wie: Konfigurieren des Livecodeanalysebereichs für verwalteten Code](./configure-live-code-analysis-scope-managed-code.md). In einem Zustand mit geringem Arbeitsspeicher erzwingt Visual Studio, dass der Liveanalysebereich auf das aktuelle Dokument reduziert wird. Sie können jedoch den bevorzugten Analysebereich erneut aktivieren, indem Sie die Schaltfläche **Erneut aktivieren** in der Infoleiste auswählen, wenn er angezeigt wird, oder indem Sie Visual Studio neu starten. Im Dialogfeld Optionen werden immer die aktuellen Einstellungen für die Livecodeanalyse angezeigt.

## <a name="gc-low-latency-disabled"></a>GC-Niedrige Latenz deaktiviert

Um den GC-Modus mit niedriger Latenz wieder zu aktivieren, starten Sie Visual Studio neu. Standardmäßig aktiviert Visual Studio den GC-Modus mit niedriger Latenz, wenn Sie eingeben, um sicherzustellen, dass ihre Eingabe keine GC-Vorgänge blockiert. Wenn jedoch ein Zustand mit geringem Arbeitsspeicher dazu führt, dass Visual Studio die automatische Sperrungswarnung anzeigt, ist der GC-Modus mit niedriger Latenz für diese Sitzung deaktiviert. Durch den Neustart von Visual Studio wird das standardmäßige GC-Verhalten erneut aktiviert. Weitere Informationen finden Sie unter <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio-Caches geleert

Wenn Sie die aktuelle Entwicklungssitzung fortsetzen oder Visual Studio neu starten, werden alle Visual Studio-Caches sofort geleert, beginnen jedoch mit dem erneuten Auffüllen. Die geleerten Caches umfassen Caches für die folgenden Features:

- Alle Verweise suchen

- Navigieren zu

- Hinzufügen von Verwendung

Darüber hinaus werden Caches, die für interne Visual Studio-Vorgänge verwendet werden, ebenfalls gelöscht.

> [!NOTE]
> Die automatische Feature-Suspension-Warnung erfolgt nur einmal pro Lösung, nicht pro Sitzung. Dies bedeutet, dass Sie möglicherweise eine weitere automatische Feature-Suspensionswarnung erhalten können, wenn Sie von Visual Basic zu Visual C-Funktion (oder umgekehrt) wechseln und in einem anderen Zustand mit niedrigem Arbeitsspeicher ausgeführt werden.

## <a name="see-also"></a>Weitere Informationen

- [Gewusst wie: Konfigurieren des Livecodeanalysebereichs für verwalteten Code](./configure-live-code-analysis-scope-managed-code.md)
- [Grundlagen der Garbage Collection](/dotnet/standard/garbage-collection/fundamentals)
- [Leistungsüberlegungen für große Lösungen](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
