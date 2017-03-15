---
title: "Verwalten von Kan&#228;len | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.tools.managechannels"
helpviewer_keywords: 
  - "Nebenläufigkeitsschnellansicht, Verwalten von Kanälen"
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Verwalten von Kan&#228;len
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In **Threadansicht** in der Parallelitätsschnellansicht, können Sie den aktuellen Channels für den Prozess verwalten, damit Sie bestimmte Muster erkennen können.  Sie können sie sortieren, Channels aufwärts und abwärts verschieben und sie anzeigen oder ausblenden.  
  
## Sortieren nach  
 Sie können die Sortiervorgänge nach Steuerelement verwenden, um die Threads nach unterschiedlichen Kriterien, auf Grundlage der aktuellen Zoomstufe zu sortieren.  Dies ist besonders nützlich, wenn Sie nach einem bestimmten Muster suchen.  Sie können durch diese Kriterien sortieren:  
  
|Kriterien|Definition|  
|---------------|----------------|  
|Startzeit|Sortiert Threads nach ihrer Startzeit.  Dies ist die Standardsortierreihenfolge.|  
|Endzeit|Sortiert Threads nach ihrer Beendigungszeit.|  
|Ausführung|Sortiert Threads nach dem Prozentsatz der Zeitspanne, die für die Ausführung aufgebracht wurde.|  
|Synchronisierung|Sortiert Threads nach dem Prozentsatz der Zeit, die in die Synchronisierung aufgebracht wurde.|  
|E\/A|Sortiert Threads nach dem Prozentsatz der Zeit, die in der E\/A entfällt \(das Lesen und Schreiben von Daten\).|  
|Sleep|Sortiert Threads nach dem Prozentsatz der Zeitspanne, die im Standbymodus verbracht wurde.|  
|Paging|Sortiert Threads nach dem Prozentsatz der Zeit, die Auslagerung.|  
|Vorzeitige Entfernung|Sortiert Threads nach dem Prozentsatz der Zeit, die vorzeitige Entfernung.|  
|Benutzeroberflächenverarbeitung|Sortiert Threads nach dem Prozentsatz der Zeit, die beim Benutzeroberflächenverarbeiten entfällt.|  
  
## Verschiebung ausgewählter Kanal auf oder ab  
 Sie können diese Steuerelemente verwenden, um eines Kanals in der Liste oben oder unten zu verschieben.  Beispielsweise können Sie verwandte Kanal nebeneinander anordnen, um Ihnen helfen, ein bestimmtes Muster oder eine bestimmte Beziehung zu überprüfen.  
  
## Verschiebung ausgewählter Channel zu überschreiten an den Anfang verschieben oder  
 Sie können ausgewählte Kanal an den Anfang oder das Ende der Liste verschieben, dass Sie ein bestimmtes Muster überprüfen können, oder verschieben einige Kanäle, wenn Sie andere überprüfen.  
  
## Ausblenden ausgewählte Kanal  
 Aktivieren Sie dieses Steuerelement, wenn Sie Channels ausblenden möchten.  Wenn ein Thread eine für die Lebensdauer des verwalteten Prozesses zu ist, können Sie sie ausblenden, während Sie andere Threads analysieren.  
  
> [!NOTE]
>  Durch das Ausblenden eines Threads wird, dieser auch aus der berechneten Zeit entfernt, die in der aktiven Legende und in den Profilberichten angezeigt wird.  
  
## Alle Kanäle anzeigen  
 Dieses Steuerelement ist aktiv, wenn mindestens Kanal ausgeblendet werden.  Wenn Sie sie auswählen, werden alle ausgeblendeten Elemente angezeigt und werden mit den Berechnungen der Zeit zurückgegeben.  
  
## Marker nach oben verschieben  
 Wenn eine Ablaufverfolgung Markerereignisse enthält, können Sie diesen Befehl verwenden, die Markerchannel auf die obere der Zeitachse zu verschieben.  Die relative Position wird beibehalten.  
  
## Gruppen\-Marker nach Thread  
 Wenn eine Ablaufverfolgung Markerereignisse enthält, können Sie diesen Befehl verwenden, Markerchannel unter dem Thread zu gruppieren, der die Markerereignisse generierte.  Die Datenträgerchannels werden auf den Anfang der Channelliste verschoben und GPU\-Channel werden auf den unteren Rand verschoben.  
  
## Siehe auch  
 [Zoomsteuerelement \(Threadansicht\)](../profiling/zoom-control-threads-view.md)   
 [Messmodus aktivieren\/deaktivieren](../profiling/measure-mode-on-off.md)   
 [Threadansicht](../profiling/threads-view-parallel-performance.md)