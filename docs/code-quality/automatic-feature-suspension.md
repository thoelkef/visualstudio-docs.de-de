---
title: Automatisches Anhalten von Features
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b79588ea3ad67d717066535392b6789e2c0d1ae
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448651"
---
# <a name="automatic-feature-suspension"></a>Automatisches Anhalten von Features

Wenn Ihr verfügbarer System Arbeitsspeicher auf 200 MB oder weniger fällt, zeigt Visual Studio im Code-Editor die folgende Meldung an:

![Warnungs Text zum Anhalten der vollständigen Lösungs Analyse](../code-quality/media/fsa_alert.png)

Wenn Visual Studio eine nicht genügend Arbeitsspeicher Bedingung erkennt, werden bestimmte erweiterte Funktionen automatisch angehalten, damit Sie stabil bleiben. Visual Studio funktioniert weiterhin wie zuvor, aber seine Leistung ist beeinträchtigt.

Bei einem Mangel an Arbeitsspeicher erfolgen die folgenden Aktionen:

- Die vollständige projektmappenanalyse für Visual C# und Visual Basic ist deaktiviert.

- Der Modus für die [Garbage Collection](/dotnet/standard/garbage-collection/index) (GC) mit niedriger C# Latenz für Visual und Visual Basic ist deaktiviert.

- Visual Studio-Caches werden geleert.

## <a name="improve-visual-studio-performance"></a>Verbessern der Leistung von Visual Studio

Tipps und Tricks zum Verbessern der Leistung von Visual Studio beim Umgang mit großen Lösungen oder Bedingungen mit geringem Arbeitsspeicher finden Sie unter [Überlegungen zur Leistung für große Lösungen](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Vollständige Lösungs Analyse angehalten

Standardmäßig ist die vollständige projektmappenanalyse für Visual Basic aktiviert und C#für das visuelle Element deaktiviert. Bei einem Mangel an Arbeitsspeicher wird die vollständige projektmappenanalyse für Visual Basic und Visual C#automatisch deaktiviert, unabhängig von den Einstellungen im Dialogfeld Optionen. Sie können jedoch die vollständige projektmappenanalyse erneut aktivieren, indem Sie die Schaltfläche **erneut aktivieren** auf der Info Leiste auswählen, wenn Sie angezeigt wird, indem Sie das Kontrollkästchen **vollständige projektmappenanalyse aktivieren** im Dialogfeld Optionen aktivieren oder Visual Studio neu starten. Im Dialogfeld Optionen werden immer die aktuellen vollständigen projektmappenanalyse-Einstellungen angezeigt. Weitere Informationen finden Sie unter Gewusst [wie: Aktivieren und Deaktivieren der vollständigen projektmappenanalyse](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC mit geringer Latenzzeit deaktiviert

Starten Sie Visual Studio neu, um den GC-Modus mit niedriger Latenz wieder zu aktivieren. Standardmäßig ermöglicht Visual Studio den GC-Modus mit niedriger Latenz, wenn Sie eingeben, um sicherzustellen, dass Ihre Typisierung keine GC-Vorgänge blockiert. Wenn in Visual Studio jedoch aufgrund von geringem Arbeitsspeicher die automatische anhaltewarnung angezeigt wird, ist der GC-Modus mit niedriger Latenzzeit für diese Sitzung deaktiviert. Wenn Sie Visual Studio neu starten, wird das standardmäßige GC-Verhalten erneut aktiviert. Weitere Informationen finden Sie unter <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>In Visual Studio geleerte Caches

Wenn Sie die aktuelle Entwicklungs Sitzung fortsetzen oder Visual Studio neu starten, werden alle Visual Studio-Caches sofort geleert, aber mit dem erneuten Auffüllen begonnen. Die geleerten Caches enthalten Caches für die folgenden Features:

- Alle Verweise suchen

- Navigieren zu

- Hinzufügen mithilfe von

Außerdem werden Caches, die für interne Visual Studio-Vorgänge verwendet werden, ebenfalls gelöscht.

> [!NOTE]
> Die automatische Merkmals Unterbrechungs Warnung tritt nur einmal pro Lösung auf, nicht pro Sitzung. Dies bedeutet Folgendes: Wenn Sie von Visual Basic zu Visual C# wechseln (oder umgekehrt) und auf einen anderen Arbeitsspeicher Mangel stoßen, können Sie möglicherweise eine weitere Warnung zur automatischen Funktions Unterbrechung erhalten.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Aktivieren und Deaktivieren der vollständigen Projektmappenanalyse](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Grundlagen der Garbage Collection](/dotnet/standard/garbage-collection/fundamentals)
- [Überlegungen zur Leistung für große Lösungen](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
