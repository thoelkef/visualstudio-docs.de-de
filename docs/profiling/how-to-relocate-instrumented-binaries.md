---
title: "Gewusst wie: Verschieben instrumentierter Bin&#228;rdateien | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.binaries"
helpviewer_keywords: 
  - "Binärdateien, Instrumentiert"
  - "Instrumentation, Instrumentierte Binärdateien"
  - "Instrumentierte Binärdateien und Verschieben"
  - "Profilerstellungstools, Instrumentierte Binärdateien"
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Gewusst wie: Verschieben instrumentierter Bin&#228;rdateien
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Während der Instrumentation werden Sonden in die Binärdatei eingeführt, um die Anwendungsleistung zu messen. Wenn Sie sich entscheiden, die instrumentierte Binärdatei an einem anderen Ort zu speichern, wird eine Kopie der ursprünglichen Binärdatei instrumentiert und am entsprechenden Speicherort abgelegt. Diese Option ist nützlich, wenn Sie vermeiden möchten, dass der Profiler Ihre ursprüngliche Binärdatei umbenennt. Wenn die Binärdatei nicht an einen anderen Speicherort ausgelagert wird, wird die ursprüngliche Version der Binärdatei überschrieben.  
  
 **Anforderungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### Verschieben von gemessenen Binärdateien  
  
1.  Klicken Sie im **Leistungs\-Explorer** mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf den **Eigenschaftenseiten** auf die Eigenschaften von **Binärdateien**.  
  
3.  Aktivieren Sie das Kontrollkästchen **Gemessene Binärdateien verschieben**.  
  
4.  Geben Sie den Speicherort für die instrumentierte Binärdatei an.  
  
## Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)