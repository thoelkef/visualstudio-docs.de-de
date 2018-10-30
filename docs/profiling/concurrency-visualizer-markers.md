---
title: Marker für die Nebenläufigkeitsschnellansicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf0cd52e94ecd3765dd580d437a227f5c11c149d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884783"
---
# <a name="concurrency-visualizer-markers"></a>Parallelitätsschnellansichtsmarker
Marker sind in der Nebenläufigkeitsschnellansicht Symbole zur Darstellung der Ereignisse in einer App.  In der Regel generiert die App diese Ereignisse, um Phasen oder Vorkommen in einer Anwendung zu bestimmen.  Die Ereignisse können von der App oder von Bibliotheken und Laufzeiten generiert werden, die die App verwendet.  
  
## <a name="kinds-of-markers"></a>Arten von Markern  
 In der Nebenläufigkeitsschnellansicht werden drei Arten von Markern benutzt, um Anwendungsereignisse darzustellen: Kennzeichen, Meldungen und Spannen.  
  
1.  Verwenden Sie ein *Kennzeichen*, um auf einen wichtigen Zeitpunkt in Ihrer App hinzuweisen.  Sie können z.B. ein Kennzeichen verwenden, um darzustellen, dass ein variabler Wert einen bestimmten Schwellenwert erreicht hat oder dass eine Ausnahme ausgelöst wurde.  
  
2.  Eine *Mitteilung* weist ebenfalls auf einen Zeitpunkt hin, den Sie jedoch für eine Ablaufverfolgung in Form eines Protokolls verwenden können.  So können Sie beispielsweise ungeordnete Elemente in der Protokolldatei in einem Meldungsaufruf umschließen und sie dadurch in der Nebenläufigkeitsschnellansicht verfolgen und anzeigen. Mit der Nebenläufigkeitsschnellansicht lassen sich diese Daten außerdem in eine CSV-Datei exportieren.  
  
3.  Eine *Spanne* stelle ein Zeitintervall in Ihrer App dar, z.B. eine ihrer Phasen.  
  
## <a name="marker-linkage-to-threads"></a>Markerverknüpfung mit Threads  
 Jeder Thread, der Marker generiert, verfügt über einen separaten Zeitachsenkanal.  Die ID des Threads, der für das Generieren der Markerereignisse zuständig ist, wird neben der Beschreibung des Markerkanals angezeigt.  Die ID, die auf der linken Seite des Markerkanals angezeigt wird, entspricht der ID eines anderen Threads im aktuellen Prozess.  
  
## <a name="marker-importance"></a>Bedeutung der Marker  
 Marker können vier Bedeutungsebenen aufweisen: niedrig, normal, hoch und kritisch.  Sie können die Quellen der Marker anhand ihrer Wichtigkeitsstufe filtern.  Wenn Sie beispielsweise nur Marker einer bestimmten Quelle anzeigen möchten, die eine normale oder kritische Wichtigkeitsstufe hat, können Sie den Filter im Dialogfeld [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) konfigurieren. Die Bedeutung eines Markers wird in der QuickInfo und im [Markerbericht](../profiling/markers-report.md) angezeigt.  
  
## <a name="marker-category"></a>Markerkategorie  
 Die Markerkategorie weist auf eine Gruppe von Markerereignissen hin, die aus derselben Quelle stammen.  Die Nebenläufigkeitsschnellansicht verwendet Farben, um zwischen unterschiedlichen Kategorien von Kennzeichen und Spannen zu unterscheiden. Konfigurieren Sie die Nebenläufigkeitsschnellansicht so, dass Sie anhand von Kategorien die Marker eines bestimmten Ereignisanbieters herausfiltern können.  Verwenden Sie das Dialogfeld [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md), um den Filter entsprechend zu konfigurieren.  
  
## <a name="known-sources-of-markers"></a>Bekannte Markerquellen  
 Jeder ETW-Anbieter kann Marken generieren, solange der Anbieter bestimmte Einschränkungen berücksichtigt. Konfigurieren Sie die Nebenläufigkeitsschnellansicht entsprechend, um zusätzliche Ereignisquellen für Marker zu überwachen. Standardmäßig werden folgende Ereignisquellen überwacht:  
  
- [SDK der Nebenläufigkeitsschnellansicht](../profiling/concurrency-visualizer-sdk.md)  
  
- [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)  
  
- [Dataflow (Datenfluss)](/dotnet/standard/parallel-programming/dataflow-task-parallel-library)  
  
- [Parallel LINQ (PLINQ) (Paralleles LINQ (PLINQ))](/dotnet/standard/parallel-programming/parallel-linq-plinq)  
  
- [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime)  
  
- [Scenario Marker Support (Unterstützung für Szenariomarker)](http://msdn.microsoft.com/en-us/e3b55bc2-b451-4214-ae00-0c7f5a5baec8)  
  
- [C++ AMP (C++ Accelerated Massive Parallelism)](/cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)  
  
  Über die Registerkarte „Marker“ im Dialogfeld [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) können Sie steuern,, ob Marker aus verschiedenen Quellen in der Nebenläufigkeitsschnellansicht angezeigt werden. Außerdem können Sie nach Markern anhand der Wichtigkeit und der Kategorie filtern.  
  
## <a name="markers-from-eventsource"></a>Marker aus EventSource  
 Die Nebenläufigkeitsschnellansicht zeigt auch EventSource-Ereignisse an.  Weitere Informationen finden Sie unter [Visualisieren von EventSource-Ereignissen als Marker](../profiling/visualizing-eventsource-events-as-markers.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Flag-Marker](../profiling/flag-markers.md)   
 [Meldungsmarker](../profiling/message-markers.md)   
 [Bereichsmarker](../profiling/span-markers.md)   
 [Visualisieren von EventSource-Ereignissen als Marker](../profiling/visualizing-eventsource-events-as-markers.md)