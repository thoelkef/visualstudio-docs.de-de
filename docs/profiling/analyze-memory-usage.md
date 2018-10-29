---
title: Analysieren der Speicherauslastung in Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8971f26881e522c81f2c111098f09a94133072d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948914"
---
# <a name="analyze-memory-usage"></a>Analysieren der Speicherauslastung
Verwenden Sie das Diagnosetool für die **Speicherauslastung** mit integriertem Debugger, um Arbeitsspeicherverluste und nicht effiziente Speicherauslastung zu ermitteln. Mit dem Speicherauslastungstool können Sie einen oder mehrere *Momentaufnahmen* des verwalteten und systemeigenen Momentaufnahme-Heaps machen. Sie können Momentaufnahmen von .NET-Apps, ASP.NET-Apps, nativen Apps und Apps im gemischten Modus (.NET und nativ) erfassen.  
  
-   Sie können eine einzelne Momentaufnahme analysieren, um die relativen Auswirkungen der Objekttypen auf die Arbeitsspeichernutzung zu verstehen und Code in der App zu suchen, die Arbeitsspeicher auf ineffiziente Weise verwendet.  
  
-   Sie können auch einen Vergleich zweier Momentaufnahmen einer App vornehmen, um Bereiche im Code aufzuspüren, die dazu führen, dass die Arbeitsspeichernutzung im Zeitverlauf zunimmt.  

Weitere Informationen finden Sie im Tutorial [Analysieren der Speicherauslastung](../profiling/memory-usage.md).  Um den Speicherverbrauch für eine.NET Core-Anwendung zu messen, müssen Sie derzeit das Tool mit dem angefügten Debugger verwenden. Für andere verwaltete und native Apps können Sie das Tool entweder mit oder ohne angefügten Debugger verwenden.

Unter Windows 7 und höher können Sie die Profilerstellungstools ohne den Debugger verwenden. Windows 8 und höher ist erforderlich, um die Profilerstellungstools mit dem Debugger auszuführen (Fenster **Diagnosetools**).
  
## <a name="blogs-and-videos"></a>Blogs und Videos  

| | |
|---------|---------|
| ![Kamerasymbol für Video](../install/media/video-icon.png "Video ansehen") | [Sehen Sie sich ein Video an](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171), in dem die Diagnosetools erläutert werden, mit denen Sie die CPU-Auslastung und die Speicherauslastung in Visual Studio 2017 analysieren können. |

 [Analyze CPU and Memory While Debugging (Analysieren der CPU und des Arbeitsspeichers beim Debuggen)](https://blogs.msdn.microsoft.com/visualstudio/2016/02/15/analyze-cpu-memory-while-debugging/)  
  
 [Visual C++ Blog: Memory Profiling in Visual C++ 2015 (Visual C++-Blog: Profilerstellung für den Arbeitsspeicher in Visual C++ 2015)](https://blogs.msdn.microsoft.com/vcblog/2015/10/21/memory-profiling-in-visual-c-2015/)  

## <a name="see-also"></a>Siehe auch
 [Profilerstellung in Visual Studio](../profiling/index.md)  
 [Einführung in Profilerstellungstools](../profiling/profiling-feature-tour.md)