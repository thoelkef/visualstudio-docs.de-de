---
title: Neuerungen bei der Profilerstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec85de208c7761b69a73cc17a72bdb4a59fe6bb4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="whats-new-in-profiling-tools-in-includevsdev15miscincludesvsdev15mdmd"></a>Neuerungen bei den Profilerstellungstools in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]
Die Diagnosetools enthalten neue Visualisierungen, um Ihnen bei der Identifizierung von Problemen in Ihrer App zu helfen, die behoben werden müssen. Die Diagnosetools umfassen jetzt Unterstützung für ASP.NET-Apps.

Weitere Informationen finden Sie in den [Anmerkungen zu [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag).

Zu den Tools wurde eine Registerkarte **Zusammenfassung** hinzugefügt, die Ihnen dabei hilft, den Fokus für Ihre Leistungsanalyse auf die Hauptbereiche zu legen. Diese Registerkarte zeigt, wie viele Ereignisse aufgetreten sind, lässt Sie Momentaufnahmen des Heaps machen und schnell die Datensammlung für die CPU-Auslastung aktivieren. In dieser Ansicht werden alle Ereignisse von [Application Insights](https://azure.microsoft.com/en-us/documentation/articles/app-insights-visual-studio/) oder der [Analyse der Benutzeroberfläche](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#UIAnalysis) gezeigt. Darüber hinaus werden in dieser Ansicht auch IntelliTrace-Ereignisse für Visual Studio Enterprise gezeigt.

![Diagnosetools-Registerkarte Zusammenfassung](../profiling/media/DiagToolsSummaryTab-2.png "DiagToolsZusammenfassungRegisterkarte")

Das Tool für die CPU-Auslastung verfügt über [neue Visualisierungen](../profiling/Beginners-Guide-to-Performance-Profiling.md), um Ihnen beim Identifizieren der Funktionen zu helfen, die am wahrscheinlichsten Leistungsprobleme verursachen. Die neue Ansicht **Aufrufer/Aufgerufener** können Sie zum Untersuchen der Kosten von Funktionsaufrufen verwenden, die an eine und von einer ausgewählten Funktion erfolgen.

![Diagnosetools Ansicht Aufrufer/Aufgerufener](../profiling/media/DiagToolsCallerCallee.png "DiagToolsAufrufer/Aufgerufener")
  
## <a name="see-also"></a>Siehe auch  
 [Profilerstellung in Visual Studio](../profiling/index.md)  
 [Tour zur Profilerstellungsfunktion](../profiling/profiling-feature-tour.md)