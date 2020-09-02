---
title: Zeilenansicht | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ccdb211312a6f53e7f519b7fac0e3ac28aab2429
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145626"
---
# <a name="lines-view"></a>Zeilenansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Zeilenansicht ist nur für Profilerdaten verfügbar, die mit der Samplingmethode gesammelt wurden. Die Ansicht ist nicht für Daten verfügbar, die mit der Instrumentationsmethode gesammelt wurden.  
  
 Für das Sampling von Profildaten identifiziert die Zeilenansicht die Anweisungen in einer Funktion, die direkt ausgeführt wurde, als das Sampling gesammelt wurde. Die Zeilenansicht identifiziert für .NET-Speicherdaten die Anweisungen, die Speicher zuweisen.  
  
 In einer Quelldatei kann eine Anweisung mehrere Zeilen umfassen, und eine einzelne Zeile kann mehr als eine Anweisung enthalten.  
  
 Eine Anweisung wird mit dem Folgenden identifiziert:  
  
- Die Quelldatei, die die Funktionsanweisung enthält.  
  
- Die Funktion, die die Anweisung enthält.  
  
- Die Quellzeile, an der die Anweisung beginnt.  
  
- Das Zeichen in der Quellzeile, an dem die Anweisung beginnt.  
  
- Die Quellzeile, an der die Anweisung endet.  
  
- Das Zeichen in der Quellzeile, an dem die Anweisung endet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zeilen Ansicht](../profiling/lines-view-sampling-data.md)   
 [Zeilen Ansicht-Sampling](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Zeilenansicht](../profiling/lines-view-contention-data.md)
