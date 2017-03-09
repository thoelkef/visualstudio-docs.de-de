---
title: "DA0023: Hohe GC-CPU-Zeit | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0023"
  - "vs.performance.23"
  - "vs.performance.rules.DA0023"
ms.assetid: aba875fe-9cbc-418d-a2c4-6eb47519a5bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0023: Hohe GC-CPU-Zeit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel-ID|DA0023|  
|Kategorie|.NET Framework-Verwendung|  
|Profilerstellungsmethode|Alle|  
|Meldung|GC-Zeitdauer in ist relativ hoch. Diese Angabe der übermäßigen Mehraufwand Garbage Collection kann die Reaktionsfähigkeit der Anwendung beeinträchtigen, werden. Sie können .NET Speicher Zuordnung Daten- und Lebensdauerinformationen erfassen um das Muster der speicherbelegung zu verstehen, die Ihre Anwendung besser verwendet.|  
|Regeltyp|Information|  
  
 Wenn Sie ein Profil mithilfe der Sampling, .NET Speicher oder Ressourcen Konflikte Methoden erstellen, müssen Sie mindestens 10 Beispiele zum Auslösen von dieser Regel sammeln.  
  
## <a name="cause"></a>Ursache  
 System-Leistungsdaten, die während der profilerstellung gesammelt werden gibt an, dass die Zeitspanne, die Garbagecollection aufgewendet wird erhebliche verglichen mit der gesamten Verarbeitung.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Der Microsoft .NET common Language Runtime (CLR) bietet einen Mechanismus zur Verwaltung von automatischen Speicher, der einen Garbage Collector verwendet zum Freigeben von Speicher von Objekten, die die Anwendung nicht mehr verwendet. Der Garbage Collector ist Generation orientiert, basierend auf der Annahme, dass viele Zuordnungen kurzlebig sind. Lokale Variablen, sollten beispielsweise kurzlebig sein. Starten Sie die neu erstellte Objekte in Generation 0 (Gen 0), und werden auf Generation 1 sie Überleben bei einer Ausführung der Garbagecollection und schließlich zu Generation 2 an, wenn die Anwendung weiterhin verwendet.  
  
 Objekte in Generation 0 werden häufig und i. d. r. äußerst effizient gesammelt. Objekte in Generation 1 werden weniger häufig und weniger effizient gesammelt. Schließlich sollten langlebige Objekte in Generation 2 noch seltener gesammelt werden. Collection der Generation 2, die eine vollständige Garbagecollection ausgeführt wird, ist auch der aufwändigste Vorgang.  
  
 Diese Regel wird ausgelöst, wenn die Zeitspanne, die Garbagecollection aufgewendet wird erhebliche Zeit verglichen mit der gesamten Verarbeitung.  
  
> [!NOTE]
>  Wenn der Anteil der Zeit, die Garbagecollection aufgewendet wird eine übermäßige verglichen mit der gesamten Verarbeitung, die [DA0024: Übermäßige GC-CPU-Zeit](../profiling/da0024-excessive-gc-cpu-time.md) Warnung ausgelöst wird, anstatt diese Regel.  
  
## <a name="how-to-investigate-a-warning"></a>Eine Warnung untersuchen.  
 Doppelklicken Sie auf die Meldung im Fenster Fehlerliste zum Navigieren der [Markierungsansicht](../profiling/marks-view.md) der Profilerstellungsdaten. Suchen Sie die **.NET CLR-Speicher\\% GC-Zeitdauer in** Spalte. Bestimmen Sie, ob bestimmte Phasen der Ausführung des Programms, in dem die verwalteten Arbeitsspeicher-Garbagecollection schwerer als andere Phasen ist. Vergleichen Sie die Werte des GC-Zeitdauer in der Garbagecollection-Rate Wert gemeldet wird, der **Auflistungsanzahl der Generation 0**, **Auflistungsanzahl der Generation 1**, **Auflistungsanzahl der Generation 2** Werte.  
  
 Die Zeit im GC-Wert % versucht, die Zeit gemeldet, die eine Anwendung ausführen Garbagecollection proportional zu den Gesamtbetrag der Verarbeitung benötigt. Denken Sie daran, dass es gibt Situationen, wenn die Zeit im GC-Wert % einen sehr hohen Wert melden kann, jedoch nicht aufgrund übermäßiger Garbagecollection. Weitere Informationen darüber, wie die % Zeit in GC-Wert berechnet wird, finden Sie unter der [Unterschied zwischen Perf Data Reported by Different Tools – 4](http://go.microsoft.com/fwlink/?LinkId=177863) Eintrag des **Maonis Weblog** auf MSDN. Seitenfehler auftreten, oder die Anwendung wird während der Garbagecollection durch andere höhere Priorität arbeiten auf dem Computer belegt, wird die % Zeit in GC-Indikator diese zusätzlichen Verzögerungen wider.