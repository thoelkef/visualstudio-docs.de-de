---
title: Nebenläufigkeitsschnellansicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14e265562b325352b42741ca505233a64e0ac1af
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879342"
---
# <a name="concurrency-visualizer"></a>Parallelitätsschnellansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Concurrency Visualizer](https://docs.microsoft.com/visualstudio/profiling/concurrency-visualizer).  
  
HINWEIS]
>  Concurrency Visualizer ist eine optionale Erweiterung für Visual Studio. Laden Sie Concurrency Visualizer und die Concurrency Visualizer Collection Tools unter folgenden Links herunter:  
>   
>  -   Laden Sie die Erweiterung              [Concurrency Visualizer](https://visualstudiogallery.msdn.microsoft.com/a6c24ce9-beec-4545-9261-293061436ee9) herunter.  
> -   Laden Sie              [Concurrency Visualizer Collection Tools für Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=49103)herunter.  
>   
>      Mit dem [Befehlszeilenprogramm für die Nebenläufigkeitsschnellansicht (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) können Sie die Ablaufverfolgung aus der Befehlszeile sammeln und diese in Concurrency Visualizer für Visual Studio 2015 anzeigen. Das Tool kann auf Computern verwendet werden, auf denen Visual Studio nicht installiert ist.  
  
 Mit der Nebenläufigkeitsschnellansicht können Sie die Leistung einer Multithread-App überprüfen. Die Ansichten der Parallelitätsschnellansicht stellen Daten zu den temporären Beziehungen zwischen den Threads im Programm und dem System als Ganzem in grafischer, tabellarischer und textlicher Form bereit. Sie können die Parallelitätsschnellansicht verwenden, um Leistungsengpässe, CPU-Unterauslastungen, Threadkonflikte, kernübergreifende Threadmigration, Synchronisierungsverzögerungen, DirectX-Aktivitäten, Bereiche überlappender E/A und andere Informationen zu suchen. Die Ansichten stellen aktionsfähige Daten bereit, indem die grafische Ausgabe nach Möglichkeit mit Aufruflisten und Quellcode verknüpft wird.  
  
 Die Nebenläufigkeitsschnellansicht beruht auf den Funktionen der [Ereignisablaufverfolgung für Windows](http://go.microsoft.com/fwlink/?LinkId=234579) .  
  
> [!NOTE]
>  Die Nebenläufigkeitsschnellansicht unterstützt keine Webprojekte.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Auslastungsansicht](../profiling/utilization-view.md)|Beschreibt, wie Systemaktivitäten über alle Prozessoren hinweg angezeigt und analysiert werden.|  
|[Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)|Beschreibt, wie die Interaktionen zwischen Threads in Ihrem Programm analysiert werden.|  
|[Kernansicht](../profiling/cores-view.md)|Beschreibt, wie die Threadmigration über Kerne hinweg analysiert wird.|  
|[Common Patterns for Poorly-Behaved Multithreaded Applications (Häufige Muster von Multithreadanwendungen mit unerwünschtem Verhalten)](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Beschreibt einige allgemeine Muster und zeigt, wie diese in der Nebenläufigkeitsschnellansicht angezeigt werden.|  
|[Parallele Entwicklung in Visual Studio (Blog)](http://go.microsoft.com/fwlink/?LinkId=235385)|Bietet Tipps und empfohlene Vorgehensweisen für die Nebenläufigkeitsschnellansicht.|  
|[Performance Report Views (Leistungsberichtansichten)](../profiling/performance-report-views.md)|Enthält Referenzinformationen zu den Berichten und Ansichten der Visual Studio-Profilerstellungstools.|  
|[SDK der Nebenläufigkeitsschnellansicht](../profiling/concurrency-visualizer-sdk.md)|Beschreibt, wie Sie Ihren Quellcode instrumentieren, um zusätzliche Informationen in der Nebenläufigkeitsschnellansicht anzuzeigen.|  
|[Befehlszeilenprogramm für die Nebenläufigkeitsschnellansicht (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Beschreibt, wie das Befehlszeilenprogramm der Nebenläufigkeitsschnellansicht (CVCollectionCmd.exe) verwendet wird, um Ablaufverfolgungen auf Computern zu erfassen und zu verarbeiten, auf denen kein Visual Studio installiert ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Profilerstellungstools](../profiling/profiling-tools.md)



