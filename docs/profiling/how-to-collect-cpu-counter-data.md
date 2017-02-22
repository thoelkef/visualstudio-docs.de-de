---
title: "Gewusst wie: Sammeln von CPU-Indikatordaten mit der Instrumentationsmethode | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.cpucounters"
helpviewer_keywords: 
  - "Profilerstellungstools, Verwenden von portablen CPU-Indikatoren"
  - "Leistungstools, portable CPU-Indikatoren"
ms.assetid: 102fb6ca-5fbf-4b05-925f-56912ce3f44b
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Sammeln von CPU-Indikatordaten mit der Instrumentationsmethode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ein CPU\-Ereigniszähler wird verwendet, um hardware\-spezifische Leistungsdaten zu erfassen.  Dieses Thema veranschaulicht, wie Ereigniszählerdaten erfasst, wenn Sie die Instrumentationsmethode zur Profilerstellung verwenden.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Zwei Typen von CPU\-Leistungsindikatorereignissen können auftreten:  
  
-   Portable Ereignisse – CPU\-Ereignisse, die unabhängig von der jeweiligen CPU erfasst werden können.  
  
-   Plattformereignisse – CPU\-Ereignisse, die mit einer bestimmten CPU verknüpft sind.  
  
 Portable Ereignisse umfassen allgemeine Ereignisse, z. B. zurückgezogene Anweisungen und nicht angehaltene Zyklen, CPU\-Puffereignisse, Verzweigungsereignisse und L2\-Cacheereignisse.  Die verfügbaren Plattformereigniszähler werden durch den Prozessorhersteller festgelegt.  
  
 Kategorien von Ereignissen können zwischen portablen Zählern und Plattformzählern gemeinsam genutzt werden.  Beispielsweise sind die folgenden Datenkategorien häufig beiden Typen gemeinsam:  
  
-   Speicherereignisse.  
  
-   Front\-End\-Ereignisse.  
  
-   Verzweigungsereignisse.  
  
 Sie haben zwei Möglichkeiten, um Leistungsindikatordaten im Profiler zusammenzustellen:  
  
-   Stellen Sie bei der Profilerstellung mit der Instrumentationsmethode Daten aus einem oder mehreren Zählern zusammen.  
  
-   Geben Sie bei der Profilerstellung mit der Samplingmethode ein Zählerereignis als Samplingintervall an.  Weitere Informationen finden Sie unter [Gewusst wie: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md).  
  
### So sammeln Sie bei der Profilerstellung mit der Instrumentationsmethode CPU\-Leistungsindikatordaten  
  
1.  Klicken Sie in den **Eigenschaftenseiten** der Leistungssitzung auf **CPU\-Indikatoren**.  
  
2.  Aktivieren Sie das Kontrollkästchen **CPU\-Indikatoren auflisten**.  
  
3.  Erweitern Sie die Struktur **Verfügbare Leistungsindikatoren**, bis Sie die Samplingereignisse gefunden haben, die Sie sammeln möchten.  
  
4.  Wählen Sie für jedes Ereignis, das Sie auflisten möchten, das Ereignis aus, und klicken Sie dann auf den Pfeil nach rechts, um das Ereignis der Liste **Ausgewählte Indikatoren** hinzuzufügen.  
  
    > [!NOTE]
    >  **Verfügbare Leistungsindikatoren** ist nur aktiviert, wenn Sie das Kontrollkästchen **CPU\-Indikatoren auflisten** aktivieren.  
  
## Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Eigenschaften von Leistungssitzungen](../profiling/performance-session-properties.md)   
 [CPU\- und Windows\-Indikatoren](../profiling/cpu-and-windows-counters.md)   
 [Gewusst wie: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md)