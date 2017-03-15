---
title: "Kan&#228;le (Threadansicht) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.channelnames"
helpviewer_keywords: 
  - "Nebenläufigkeitsschnellansicht, Kanäle (Threadansicht)"
ms.assetid: 2f798c17-2363-42a4-be94-a5751d208eac
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Kan&#228;le (Threadansicht)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Parallelitätsschnellansicht zeigt vier Arten Kanal an: Datenträgerchannels Kanal, den gewünschten Thread, Markerchannel und GPU\-Channel.  
  
## Threadchannels  
 In einem Threadchannel wird der Threadzustand nach Farbe für nur einen Thread angezeigt.  Wenn Sie mit den Mauszeiger auf dem Channelnamen ruhen lassen, wird die Startfunktion für den angegebenen Thread angezeigt.  Von der Parallelitätsschnellansicht werden mehrere Arten von Threads erkannt.  Die am häufigsten verwendeten Arten werden in der folgenden Tabelle angezeigt.  
  
|||  
|-|-|  
|Hauptthread|Der Thread, der die App gestartet wurde.|  
|Arbeitsthread|Ein Thread, der vom Anwendungshauptthread erstellt wurde.|  
|CLR\-Arbeitsthread|Ein Arbeitsthread, der von der Common Language Runtime \(CLR\) erstellt wurde.|  
|Debuggerhilfe|Ein Arbeitsthread, der vom Visual Studio\-Debugger erstellt wurde.|  
|ConcRT\-Thread|Ein Thread, der von der Microsoft Concurrency Runtime erstellt wurde.|  
|GDI\-Thread|Ein Thread, der von GDIPlus erstellt wurde.|  
|OLE\/RPC\-Thread|Ein Thread, der als RPC\-Arbeitsthread erstellt wurde.|  
|RPC\-Thread|Ein Thread, der als RPC\-Thread erstellt wurde.|  
|Winsock\-Thread|Ein Thread, der als Winsock\-Thread erstellt wurde.|  
|Threadpool|Ein Thread, der vom CLR\-Threadpool erstellt wurde.|  
  
## Datenträgerchannels  
 Datenträgerchannels entsprechen physischen Laufwerken auf dem Computer.  Da für jedes physische Laufwerk im System eigene Channels für Lese\- und Schreibvorgänge vorhanden sind, weist jedes Laufwerk zwei Channels auf.  Die Datenträgernummern entsprechen Kernelgerätenamen.  Ein Datenträgerchannels wird nur angezeigt, wenn es Aktivität auf dem Datenträger vorhanden waren.  
  
## Marker\-Channel  
 Markerchannel entsprechen den Ereignissen, die durch die App und Bibliotheken, die sie verwendet, generiert werden.  Zum Beispiel generieren die Task Parallel Library, Parallel Patterns Library und AMP Ereignisse, die als Markierung angezeigt werden.  Jeder Markerchannel ist einer Thread\-ID zugeordnet, die neben der Beschreibung des Kanals angezeigt wird.  Die ID identifiziert den Thread, der das Ereignis generiert hat.  Die Beschreibung des Kanals enthält den Namen der Ereignisablaufverfolgung für Anbieter Windows \(ETW\), der die Ereignisse generiert.  Wenn die Channelanzeigenereignisse von [Parallelitätsschnellansichts\-SDK](../profiling/concurrency-visualizer-sdk.md), der Reihenname auch angezeigt wird.  
  
## GPU\-Channel  
 GPU\-Channelanzeigeninformationen zum DirectX 11\-Aktivität im System.  Jedes DirectX\-Modul, das der Grafikkarte zugeordnet wird, gelten separate Kanal.  Die einzelnen Segmente stellt die Zeit dar, die ein DMA\-Paket Verarbeitung entfällt.  
  
## Siehe auch  
 [Threadansicht](../profiling/threads-view-parallel-performance.md)