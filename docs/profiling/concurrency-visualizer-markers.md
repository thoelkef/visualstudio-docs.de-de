---
title: "Parallelit&#228;tsschnellansichtsmarker | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.markersui"
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Parallelit&#228;tsschnellansichtsmarker
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Parallelitätsschnellansicht werden Markierungen Symbole, Ereignisse in einer App darstellen.  In der Regel generiert die App diese Ereignisse, um oder Phasen Vorkommen in einer Anwendung festlegen.  Die Ereignisse können durch die Anwendung oder in Bibliotheken und Laufzeiten generiert werden, die die App verwendet.  
  
## Arten von Markierungen  
 In der Parallelitätsschnellansicht werden drei Arten Markierung, um Anwendungsereignisse darzustellen: Flags, Meldungen und Spannen.  
  
1.  Verwenden Sie ein *Flag*, um einen interessanten Zeitpunkt auf der App angeben.  Beispielsweise können Sie ein Flag, um anzuzeigen, dass eines variablen Werts einen bestimmten Schwellenwert erreicht hat, oder dass eine Ausnahme ausgelöst wurde.  
  
2.  Eine *Meldung* als auch einen Zeitpunkt, Sie können es jedoch für ProtokollFormatablaufverfolgung verwenden.  Beispielsweise was in eine Protokolldatei gesichert werden können, können Sie in einem Meldungsaufruf jetzt umbrechen, damit Sie ihn aufzeichnen und in der Parallelitätsschnellansicht angezeigt werden können.  Sie können die Parallelitätsschnellansicht auch verwenden, um diese Daten in eine CSV\-Datei zu exportieren.  
  
3.  Eine *Spanne* stellt ein Intervall von Zeit in der App eine beispielsweise seiner Phasen dar.  
  
## Marker\-Bindung zu Threads  
 Jeder Thread, der Markierung generiert, verfügt über einen separaten Zeitachsenchannel.  Die ID des Threads, der zum Generieren der Markerereignisse zuständig ist, wird neben der Beschreibung des Markerchannels angezeigt.  Die ID, die auf der linken Seite des Markerchannels angezeigt wird, stimmt die ID eines anderen Threads im aktuellen Prozess ab.  
  
## Marker\-Bedeutung  
 Markierungen können eine von vier Wichtigkeitsstufen haben: niedrig, normal, hoch und wichtig.  Sie können die Ursache von Markern auf Grundlage Wichtigkeitsstufe filtern.  Wenn Sie beispielsweise ausschließlich Marker einer bestimmten Quelle anzeigen möchten, die bei normalen oder wichtige Bedeutung hat, können Sie den Filter im [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) Dialogfeld konfigurieren. Die Bedeutung eines Markers wird in der QuickInfo und [Markerbericht](../profiling/markers-report.md) angezeigt.  
  
## Marker\-Kategorie  
 Eine Markerkategorie gibt eine Gruppe Markerereignissen an, die von der gleichen Quelle stammen.  Die Nebenläufigkeitsschnellansichtsverwendungsfarbe, um von verschiedenen Kategorien von Flags und von Spannen zu unterscheiden.  Sie können die Parallelitätsschnellansicht konfigurieren, um Kategorien verwenden, um die von einem bestimmten Markerereignisse Ereignisanbieter zu filtern.  Verwenden Sie das Dialogfeld [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md), um den Filter zu konfigurieren.  
  
## Bekannte Quellen von Markierungen  
 Jeder kann ETW\-Anbieter Markierung generieren, solange der Anbieter bestimmte Einschränkungen unterliegt.  Sie können die Parallelitätsschnellansicht konfigurieren, um zu zusätzlichen Ereignisquellen für Markierung überwacht.  Standardmäßig überwacht sie diesen Ereignisquellen:  
  
-   [Parallelitätsschnellansichts\-SDK](../profiling/concurrency-visualizer-sdk.md)  
  
-   [Task Parallel Library \(TPL\)](../Topic/Task%20Parallel%20Library%20\(TPL\).md)  
  
-   [Datenfluss](../Topic/Dataflow%20\(Task%20Parallel%20Library\).md)  
  
-   [Parallel LINQ \(PLINQ\)](../Topic/Parallel%20LINQ%20\(PLINQ\).md)  
  
-   [Concurrency Runtime](/visual-cpp/parallel/concrt/concurrency-runtime)  
  
-   [Scenario Marker Support](http://msdn.microsoft.com/de-de/e3b55bc2-b451-4214-ae00-0c7f5a5baec8)  
  
-   [C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)](/visual-cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)  
  
 Sie können die Markerregisterkarte im Dialogfeld [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) verwenden, um zu steuern, ob Markierung aus verschiedenen Quellen in der Parallelitätsschnellansicht angezeigt werden und Sie für Marker auf Grundlage Bedeutung und Kategorie filtern können.  
  
## Markierung von EventSource  
 Die Parallelitätsschnellansicht kann EventSource\-Ereignisse auch anzeigen.  Weitere Informationen finden Sie unter [Visualisieren von EventSource\-Ereignissen als Marker](../profiling/visualizing-eventsource-events-as-markers.md).  
  
## Siehe auch  
 [Flag\-Marker](../profiling/flag-markers.md)   
 [Meldungsmarker](../profiling/message-markers.md)   
 [Bereichsmarker](../profiling/span-markers.md)   
 [Visualisieren von EventSource\-Ereignissen als Marker](../profiling/visualizing-eventsource-events-as-markers.md)