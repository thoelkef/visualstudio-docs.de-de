---
title: Analysieren der Speicherauslastung in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: aac1c901f98d63b8cf77b41a165548cccede4f21
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2018
---
# <a name="analyze-memory-usage"></a>Analysieren der Speicherauslastung
Verwenden Sie das Diagnosetool für die **Speicherauslastung** mit integriertem Debugger, um Arbeitsspeicherverluste und nicht effiziente Speicherauslastung zu ermitteln. Mit dem Speicherauslastungstool können Sie einen oder mehrere *Momentaufnahmen* des verwalteten und systemeigenen Momentaufnahme-Heaps machen. Sie können Momentaufnahmen von .NET-Apps, systemeigenen Apps und Apps in gemischtem Modus (.Net und systemeigen) erfassen.  
  
-   Sie können eine einzelne Momentaufnahme analysieren, um die relativen Auswirkungen der Objekttypen auf die Arbeitsspeichernutzung zu verstehen und Code in der App zu suchen, die Arbeitsspeicher auf ineffiziente Weise verwendet.  
  
-   Sie können auch einen Vergleich zweier Momentaufnahmen einer App vornehmen, um Bereiche im Code aufzuspüren, die dazu führen, dass die Arbeitsspeichernutzung im Zeitverlauf zunimmt.  

Weitere Informationen finden Sie im Tutorial [Analysieren der Speicherauslastung](../profiling/memory-usage.md). Informationen zum Analysieren der Speicherauslastung ohne den Debugger anzufügen finden Sie unter [Memory usage without the debugger (Speicherauslastung ohne Debugger)](memory-usage-without-debugging2.md).
  
## <a name="blogs-and-videos"></a>Blogs und Videos  

|         |         |
|---------|---------|
|  ![Kamerasymbol für video](../install/media/video-icon.png "Video ansehen")  |    [Sehen Sie sich ein Video an](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171), in dem die Diagnosetools erläutert werden, mit denen Sie die CPU-Auslastung und die Speicherauslastung in Visual Studio 2017 analysieren können. |

 [Analyze CPU and Memory While Debugging (Analysieren der CPU und des Arbeitsspeichers beim Debuggen)](https://blogs.msdn.microsoft.com/visualstudio/2016/02/15/analyze-cpu-memory-while-debugging/)  
  
 [Visual C++ Blog: Memory Profiling in Visual C++ 2015 (Visual C++-Blog: Profilerstellung für den Arbeitsspeicher in Visual C++ 2015)](https://blogs.msdn.microsoft.com/vcblog/2015/10/21/memory-profiling-in-visual-c-2015/)  

## <a name="see-also"></a>Siehe auch
 [Profilerstellung in Visual Studio](../profiling/index.md)  
 [Tour zur Profilerstellungsfunktion](../profiling/profiling-feature-tour.md)