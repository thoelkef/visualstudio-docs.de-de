---
title: Zeilenansicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 433bcbc46814c49a30836d8a7f0d9ec10e571ea6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="lines-view"></a>Zeilenansicht
Die Zeilenansicht ist nur für Profilerdaten verfügbar, die mit der Samplingmethode gesammelt wurden. Die Ansicht ist nicht für Daten verfügbar, die mit der Instrumentationsmethode gesammelt wurden.  
  
 Für das Sampling von Profildaten identifiziert die Zeilenansicht die Anweisungen in einer Funktion, die direkt ausgeführt wurde, als das Sampling gesammelt wurde. Die Zeilenansicht identifiziert für .NET-Speicherdaten die Anweisungen, die Speicher zuweisen.  
  
 In einer Quelldatei kann eine Anweisung mehrere Zeilen umfassen, und eine einzelne Zeile kann mehr als eine Anweisung enthalten.  
  
 Eine Anweisung wird mit dem Folgenden identifiziert:  
  
-   Die Quelldatei, die die Funktionsanweisung enthält.  
  
-   Die Funktion, die die Anweisung enthält.  
  
-   Die Quellzeile, an der die Anweisung beginnt.  
  
-   Das Zeichen in der Quellzeile, an dem die Anweisung beginnt.  
  
-   Die Quellzeile, an der die Anweisung endet.  
  
-   Das Zeichen in der Quellzeile, an dem die Anweisung endet.  
  
## <a name="see-also"></a>Siehe auch  
 [Zeilenansicht](../profiling/lines-view-sampling-data.md)   
 [Zeilenansicht - Sampling](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Zeilenansicht](../profiling/lines-view-contention-data.md)