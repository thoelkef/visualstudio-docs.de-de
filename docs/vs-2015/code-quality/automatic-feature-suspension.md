---
title: Automatisches Anhalten von Features | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c2e6db11220c2cc7f14bc2f0f05912e7855646c1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045981"
---
# <a name="automatic-feature-suspension"></a>Automatisches Anhalten von Features
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Wenn Ihre verfügbaren Arbeitsspeicher des Systems auf 200 MB oder weniger fällt, zeigt Visual Studio die folgende Meldung im Code-Editor.

 ![Anhalten der vollständigen projektmappenanalyse Warntext](../code-quality/media/fsa-alert.png "FSA_Alert")

 Wenn Visual Studio eine Bedingung nicht genügenden Arbeitsspeichers erkannt wird, hält es automatisch bestimmte erweiterte Features, damit er stabil bleiben können. Wenn diese erweiterte Feature anhalten Warnung wird angezeigt, Visual Studio funktionieren weiterhin wie zuvor, aber die Leistung leicht beeinträchtigt werden.

 In einem wenig Arbeitsspeicher verfügbar ist tritt Folgendes auf:

- Vollständige projektmappenanalyse für Visual C# und Visual Basic ist deaktiviert.

- [Die automatische Speicherbereinigung](http://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9) (GC) mit niedriger Latenz im Modus für Visual c# und Visual Basic sind deaktiviert.

- Visual Studio-Caches werden geleert.

## <a name="improve-visual-studio-performance"></a>Verbessern der Leistung von Visual Studio
 Tipps und Tricks zur Verbesserung von Visual Studio-Leistung beim Umgang mit großen Projektmappen oder niedriger Arbeitsspeicherstatus, finden Sie unter [Überlegungen zur Leistung bei großen Projektmappen](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Vollständige projektmappenanalyse angehalten
 Standardmäßig ist die vollständige projektmappenanalyse für Visual Basic aktiviert und deaktiviert für Visual C#. Allerdings wird in ein wenig Arbeitsspeicher verfügbar, vollständige projektmappenanalyse automatisch für Visual Basic und Visual C#-, unabhängig von den Einstellungen im Dialogfeld "Optionen" deaktiviert. Allerdings können Sie vollständige projektmappenanalyse erneut aktivieren, indem Sie die Auswahl der **erneut aktivieren** Schaltfläche in der Info Balken-, wenn sie dazu angezeigt wird der **vollständige projektmappenanalyse aktivieren** Kontrollkästchen im Dialogfeld "Optionen" oder durch Visual Studio neu starten. Das Dialogfeld "Optionen" zeigt der aktuellen vollständige Projektmappe immer analyseeinstellungen. Weitere Informationen finden Sie unter [Vorgehensweise: Aktivieren und Deaktivieren der vollständigen Projektmappenanalyse](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC mit geringer Latenz deaktiviert
 Starten Sie Visual Studio neu, um im Modus mit niedriger Latenz der GC wieder zu aktivieren.  Standardmäßig kann Visual Studio mit geringer Latenz GC-Modus, wenn Sie eine Eingabe vornehmen, stellen Sie sicher, dass die Schreibweise keine GC-Vorgänge blockiert. Eine Bedingung nicht genügenden Arbeitsspeichers führt dazu, dass Visual Studio die automatische Unterbrechung Warnung anzeigen, ist jedoch GC mit niedriger Latenz im Modus für diese Sitzung deaktiviert. Neustart von Visual Studio wird das Standardverhalten der GC wieder aktiviert. Weitere Informationen finden Sie unter <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio-Caches geleert

Alle Visual Studio-Caches sind sofort geleert, aber neu auffüllen, wenn Sie Visual Studio neu starten oder die aktuellen Sitzung für die Entwicklung fortsetzen beginnt. Die Caches geleert enthalten Caches für die folgenden Features.

- Alle Verweise suchen

- Navigieren zu

- Fügen mit hinzu

Darüber hinaus sind für interne Visual Studio-Vorgänge verwendeten Caches ebenfalls gelöscht.

> [!NOTE]
> Die Funktion zum automatischen Unterbrechung Warnung tritt nur einmal auf einer Basis pro Lösung nicht auf einer Basis pro Sitzung. Dies bedeutet, wenn Sie von Visual Basic, Visual C# (oder umgekehrt) wechseln, und führen Sie in einem anderen nicht genügend Arbeitsspeicher verfügbar, Sie möglicherweise eine andere Funktion zum automatischen Warnung zu gesperrter abrufen können.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Aktivieren und Deaktivieren der vollständigen Projektmappenanalyse](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Grundlagen der Garbage Collection](http://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [Überlegungen zur Leistung bei großen Projektmappen](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)