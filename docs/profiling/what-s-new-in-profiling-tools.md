---
title: Neuerungen bei den Profilerstellungstools | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
caps.latest.revision: 42
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 1dae0fddd8f3608089b67f571e152ed5a0f56c61
ms.openlocfilehash: 888c5c996df6558fc4c409704ad003f9c25a733b
ms.lasthandoff: 02/22/2017

---
# <a name="whats-new-in-profiling-tools-in-includevsdev15miscincludesvsdev15mdmd"></a>Neuerungen bei den Profilerstellungstools in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]
Die Diagnosetools enthalten neue Visualisierungen, um Ihnen bei der Identifizierung von Problemen in Ihrer App zu helfen, die behoben werden müssen. Die Diagnosetools umfassen jetzt Unterstützung für ASP.NET-Apps.

Weitere Informationen finden Sie in den [Anmerkungen zu [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]] (https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag).

Zu den Tools wurde eine Registerkarte **Zusammenfassung** hinzugefügt, die Ihnen dabei hilft, den Fokus für Ihre Leistungsanalyse auf die Hauptbereiche zu legen. Diese Registerkarte zeigt, wie viele Ereignisse aufgetreten sind, lässt Sie Momentaufnahmen des Heaps machen und schnell die Datensammlung für die CPU-Auslastung aktivieren. In dieser Ansicht werden alle Ereignisse von [Application Insights](https://azure.microsoft.com/en-us/documentation/articles/app-insights-visual-studio/) oder der [Analyse der Benutzeroberfläche](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#UIAnalysis) gezeigt. Darüber hinaus werden in dieser Ansicht auch IntelliTrace-Ereignisse für Visual Studio Enterprise gezeigt.

![Diagnosetools-Registerkarte Zusammenfassung](../profiling/media/DiagToolsSummaryTab-2.png "DiagToolsZusammenfassungRegisterkarte")

Das Tool für die CPU-Auslastung verfügt über [neue Visualisierungen](../profiling/Beginners-Guide-to-Performance-Profiling.md), um Ihnen beim Identifizieren der Funktionen zu helfen, die am wahrscheinlichsten Leistungsprobleme verursachen. Die neue Ansicht **Aufrufer/Aufgerufener** können Sie zum Untersuchen der Kosten von Funktionsaufrufen verwenden, die an eine und von einer ausgewählten Funktion erfolgen.

![Diagnosetools Ansicht Aufrufer/Aufgerufener](../profiling/media/DiagToolsCallerCallee.png "DiagToolsAufrufer/Aufgerufener")
  
## <a name="see-also"></a>Siehe auch  
 [Profilerstellungstools](../profiling/profiling-tools.md)
