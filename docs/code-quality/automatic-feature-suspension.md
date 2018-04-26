---
title: Funktion zum automatischen Unterbrechung im Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: d75c02bf6b817d03492a15b1f827f94eaaf3e306
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="automatic-feature-suspension"></a>Funktion zum automatischen anhalten

Wenn Ihre verfügbaren Systemarbeitsspeicher auf 200 MB oder weniger fällt, zeigt Visual Studio die folgende Meldung im Code-Editor:

![Text der Warnung das vollständige projektmappenanalyse anhalten](../code-quality/media/fsa_alert.png)

Wenn Visual Studio eine Bedingung nicht genügenden Arbeitsspeichers erkennt, hält es automatisch bestimmte erweiterten Funktionen, um es stabil bleiben kann. Visual Studio weiterhin funktionstüchtig, aber die Leistung beeinträchtigt wird.

In einer nicht genügend Arbeitsspeicher verfügbar erfolgen die folgenden Aktionen:

- Vollständige projektmappenanalyse für Visual c# und Visual Basic ist deaktiviert.

- [Garbagecollection](/dotnet/standard/garbage-collection/index) (GC) mit niedriger Latenz Modus für Visual c# und Visual Basic ist deaktiviert.

- Visual Studio-Caches geleert werden.

## <a name="improve-visual-studio-performance"></a>Visual Studio zur Leistungssteigerung

Tipps und Tricks zum Visual Studio-Leistung zu verbessern, bei der Arbeit mit großen Projektmappen oder niedriger Arbeitsspeicherstatus finden Sie unter [Überlegungen zur Leistung bei großen Projektmappen](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Vollständige projektmappenanalyse angehalten

Standardmäßig wird vollständige projektmappenanalyse für Visual Basic aktiviert und deaktiviert für Visual c#. Allerdings wird in einer nicht genügend Arbeitsspeicher verfügbar, vollständige projektmappenanalyse automatisch für Visual Basic und Visual C#-, unabhängig von den Einstellungen im Dialogfeld Optionen deaktiviert. Allerdings können Sie vollständige projektmappenanalyse erneut aktivieren, indem Sie auswählen der **reaktivieren** Schaltfläche in der Info Balken-, wenn sie dazu angezeigt wird der **vollständige projektmappenanalyse aktivieren** Kontrollkästchen im Dialogfeld "Optionen" oder durch Visual Studio neu starten. Das Dialogfeld "Optionen" zeigt der aktuelle, vollständigen Lösung immer analyseeinstellungen. Weitere Informationen finden Sie unter [How to: Enable and Disable Full Solution Analysis](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC latenzarmen deaktiviert

Um GC mit geringer Latenz Modus wieder zu aktivieren, starten Sie Visual Studio neu. Standardmäßig kann Visual Studio GC mit geringer Latenz Modus aus, wenn Sie eingeben, um sicherzustellen, dass Ihre Eingabe keine GC-Vorgänge blockiert wird. Wenn eine Bedingung nicht genügenden Arbeitsspeichers führt dazu, Visual Studio die automatische Aufhebung Warnung anzeigen dass, ist GC mit geringer Latenz Modus für diese Sitzung deaktiviert. Das Standardverhalten der GC Neustart von Visual Studio erneut aktiviert werden. Weitere Informationen finden Sie unter <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio-Caches geleert

Wenn Sie die aktuelle Sitzung für die Entwicklung weiterhin oder Visual Studio neu starten, werden sofort alle Visual Studio-Caches geleert, jedoch beginnen neu auffüllen. Die Caches geleert gehören Caches für die folgenden Funktionen:

- "Suchen Sie alle Verweise"

- Navigieren zu

- Fügen mit hinzu

Darüber hinaus sind Caches für interne Vorgänge für Visual Studio verwendet, ebenfalls gelöscht.

> [!NOTE]
> Die Funktion zum automatischen Unterbrechung Warnung tritt nur einmal auf der Grundlage einer pro-Projektmappe nicht auf einer sitzungsbasis. Dies bedeutet, dass wenn Sie aus Visual Basic, Visual c# (oder umgekehrt) wechseln, und führen Sie in einem anderen nicht genügend Arbeitsspeicher verfügbar, können Sie eine andere Funktion zum automatischen Unterbrechung Warnung möglicherweise erhalten.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Aktivieren und deaktivieren Sie die vollständige Projektmappenanalyse](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Grundlagen der Garbage Collection](/dotnet/standard/garbage-collection/fundamentals)
- [Überlegungen zur Leistung bei großen Projektmappen](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)