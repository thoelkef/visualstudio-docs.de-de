---
title: "Zeilenansicht | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.lines"
helpviewer_keywords: 
  - "Zeilenansicht"
  - "Berichte für Profilerstellungstools, Zeilenansicht"
  - "Profilerstellungstools, Zeilenansicht"
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Zeilenansicht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Zeilenansicht ist nur für Profilerdaten verfügbar, die mit der Samplingmethode erfasst wurden.  Die Ansicht ist nicht für Daten verfügbar, die mit der Instrumentation erfasst wurden.  
  
 Bei Samplingprofildaten kann in der Zeilenansicht die Anweisung in einer Funktion überprüft werden, die unmittelbar während der Datensammlung ausgeführt wurde.  Bei .NET\-Arbeitsspeicherdaten können in der Zeilenansicht die Anweisungen eingesehen werden, die Speicher belegen.  
  
 In einer Quelldatei kann eine Anweisung mehrere Zeilen umfassen, und eine einzelne Zeile kann mehr als eine Anweisung enthalten.  
  
 Eine Anweisung wird mit Folgendem identifiziert:  
  
-   Den Namen der Quelldatei, die diese Funktionsanweisung enthält.  
  
-   Die Funktion, die die Anweisung enthält.  
  
-   Die Quellzeile, in der die Anweisung beginnt.  
  
-   Das Zeichen in der Quellzeile, mit dem die Anweisung beginnt.  
  
-   Die Quellzeile, in der die Anweisung endet.  
  
-   Das Zeichen in der Quellzeile, mit dem die Anweisung endet.  
  
## Siehe auch  
 [Zeilenansicht](../profiling/lines-view-sampling-data.md)   
 [Zeilenansicht \- Sampling](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Zeilenansicht](../profiling/lines-view-contention-data.md)