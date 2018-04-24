---
title: Verwenden von Leistungsregeln zur Analyse von Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ce42343167173647d39dcc6f7db06bedcbc0236
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="using-performance-rules-to-analyze-data"></a>Verwenden von Leistungsregeln zur Analyse von Daten
Die Leistungswarnungen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools deuten auf Probleme in einer profilierten Anwendung hin, die die Programmausführung verlangsamen können. Warnungen können auch anzeigen, dass Sie möglicherweise die Sammlungsmethoden ändern müssen, um nützlichere Daten zu erfassen. Leistungswarnungen werden automatisch in einer Profilerstellungssitzung generiert. Die Warnungen werden im Fenster **Fehlerliste** angezeigt, wenn eine Datei mit Profilerstellungsdaten in Visual Studio geöffnet wird. Im Fenster **Fehlerliste** können Sie den Quellcode zu dem Problem suchen und ausführliche Informationen zu dem Fehler anzeigen, z.B. Informationen zur Problembehebung. Sie können außerdem Warnungen deaktivieren, die für Sie nicht relevant sind.  
  
> [!NOTE]
>  Leistungswarnungen des Profilers werden mithilfe der dynamischen Analyse bei der Programmausführung generiert; es besteht kein Zusammenhang mit Codeanalysewarnungen. Mit der Codeanalyse können auch Leistungswarnungen für verwalteten Code auf Grundlage der statischen Analyse des Quellcodes generiert werden. Weitere Informationen finden Sie unter [Analyzing Managed Code Quality (Analysieren der Qualität von verwaltetem Code)](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) und [Performance Warnings (Leistungswarnungen)](../code-quality/performance-warnings.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [How to: View Performance Warnings (Vorgehensweise: Anzeigen von Leistungswarnungen)](../profiling/how-to-view-performance-warnings.md)  
 Enthält Informationen zum Öffnen des Fensters **Fehlerliste**, um Leistungswarnungen des Profilers anzuzeigen.  
  
 [How to: Configure Performance Rules (Vorgehensweise: Konfigurieren der Leistungsregeln der Profilerstellungstools)](../profiling/how-to-configure-performance-rules.md)  
 Enthält Informationen zum Aktivieren und Deaktivieren von einzelnen Leistungswarnungen.  
  
 [Performance Rules Reference (Referenz zu den Leistungsregeln)](../profiling/performance-rules-reference.md)  
 Enthält ausführliche Informationen zu den Leistungswarnungen des Profilers.