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
ms.prod: visual-studio-dev15
ms.workload:
- multiple
ms.openlocfilehash: 174f78460e852d4ee82a5e8f84c031ace86b4360
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938827"
---
# <a name="automatic-feature-suspension"></a>Automatisches Anhalten von Features

Wenn Ihre verfügbaren Arbeitsspeicher des Systems auf 200 MB oder weniger fällt, zeigt Visual Studio die folgende Meldung im Code-Editor:

![Text der Warnung das Anhalten der vollständigen projektmappenanalyse](../code-quality/media/fsa_alert.png)

Wenn Visual Studio eine Bedingung nicht genügenden Arbeitsspeichers erkannt wird, hält es automatisch bestimmte erweiterte Features, damit er stabil bleiben können. Visual Studio wie vorher funktionieren auch weiterhin, aber die Leistung beeinträchtigt wird.

In einem wenig Arbeitsspeicher verfügbar werden die folgenden Aktionen ausgeführt:

- Vollständige projektmappenanalyse für Visual c# und Visual Basic ist deaktiviert.

- [Die automatische Speicherbereinigung](/dotnet/standard/garbage-collection/index) (GC) mit niedriger Latenz im Modus für visuelle C# und Visual Basic ist deaktiviert.

- Visual Studio-Caches werden geleert.

## <a name="improve-visual-studio-performance"></a>Verbessern der Leistung von Visual Studio

Tipps und Tricks zur Verbesserung von Visual Studio-Leistung beim Umgang mit großen Projektmappen oder niedriger Arbeitsspeicherstatus, finden Sie unter [Überlegungen zur Leistung bei großen Projektmappen](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Vollständige projektmappenanalyse angehalten

Standardmäßig ist die vollständige projektmappenanalyse für Visual Basic aktiviert und deaktiviert für Visual c#. Allerdings wird in ein wenig Arbeitsspeicher verfügbar, vollständige projektmappenanalyse automatisch für Visual Basic und Visual C#-, unabhängig von den Einstellungen im Dialogfeld "Optionen" deaktiviert. Allerdings können Sie vollständige projektmappenanalyse erneut aktivieren, indem Sie die Auswahl der **erneut aktivieren** Schaltfläche in der Info Balken-, wenn sie dazu angezeigt wird der **vollständige projektmappenanalyse aktivieren** Kontrollkästchen im Dialogfeld "Optionen" oder durch Visual Studio neu starten. Das Dialogfeld "Optionen" zeigt der aktuellen vollständige Projektmappe immer analyseeinstellungen. Weitere Informationen finden Sie unter [Vorgehensweise: Aktivieren und Deaktivieren der vollständigen Projektmappenanalyse](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC mit geringer Latenz deaktiviert

Starten Sie Visual Studio neu, um im Modus mit niedriger Latenz der GC wieder zu aktivieren. Standardmäßig kann Visual Studio mit geringer Latenz GC-Modus, wenn Sie eine Eingabe vornehmen, stellen Sie sicher, dass die Schreibweise keine GC-Vorgänge blockiert. Eine Bedingung nicht genügenden Arbeitsspeichers führt dazu, dass Visual Studio die automatische Unterbrechung Warnung anzeigen, ist jedoch GC mit niedriger Latenz im Modus für diese Sitzung deaktiviert. Das Standardverhalten für die GC Neustart von Visual Studio erneut aktiviert werden. Weitere Informationen finden Sie unter <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio-Caches geleert

Wenn Sie die aktuelle Sitzung für die Entwicklung weiterhin oder Visual Studio neu starten, werden sofort alle Visual Studio-Caches geleert, aber später allmählich neu auffüllen. Die Caches geleert umfassen Caches für die folgenden Features:

- Alle Verweise suchen

- Navigieren zu

- Fügen mit hinzu

Darüber hinaus sind für interne Visual Studio-Vorgänge verwendeten Caches ebenfalls gelöscht.

> [!NOTE]
> Die Funktion zum automatischen Unterbrechung Warnung tritt nur einmal auf einer Basis pro Lösung nicht auf einer Basis pro Sitzung. Dies bedeutet, wenn Sie von Visual Basic, Visual c# (oder umgekehrt) wechseln, und führen Sie in einem anderen nicht genügend Arbeitsspeicher verfügbar, Sie möglicherweise eine andere Funktion zum automatischen Warnung zu gesperrter abrufen können.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Aktivieren und Deaktivieren der vollständigen Projektmappenanalyse](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Grundlagen der Garbage Collection](/dotnet/standard/garbage-collection/fundamentals)
- [Überlegungen zur Leistung bei großen Projektmappen](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)