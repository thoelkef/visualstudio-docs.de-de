---
title: "Verwendungsregeln f&#252;r Profilerstellungstools | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Verwendungsregeln f&#252;r Profilerstellungstools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Leistungsregeln in der Kategorie Verwendung der Profilerstellungstools bieten Hinweise für die Datensammlung mit dem Profiler.  
  
|||  
|-|-|  
|[DA0002: VSPerfCorProf.dll fehlt](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|Die Profilerstellung in der Befehlszeile kann unvollständige Daten für [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Binärdateien enthalten.  Der Grund dafür kann darin bestehen, dass nicht die richtigen Umgebungsvariablen festgelegt wurden.|  
|[DA0003: Zahlreiche Kernelbeispiele](../profiling/da0003-many-kernel-samples.md)|Viele der bei der Profilerstellung aufgezeichneten Samplings sind außerhalb der Ausführung der Zielbinärdatei aufgetreten.  Erwägen Sie die Verwendung der Instrumentationsmethode, um genauere Daten zu sammeln.|  
|[DA0004: Hohe Prozessorauslastung](../profiling/da0004-high-processor-usage.md)|Die Profilerstellungsdaten deuten darauf hin, dass die Prozessoren während der Profilerstellung durchgehend ausgelastet waren.  Erwägen Sie die Verwendung der Samplingmethode, um genauere Daten zu sammeln.|  
|[DA0008: Es wurden nur wenige Beispiele aufgelistet](../profiling/da0008-few-samples-collected.md)|Die Anzahl der bei der Profilerstellung gesammelten Samplings war nicht hoch genug, um statistisch signifikant zu sein.  Erwägen Sie eine erneute Profilerstellung und eine längere Ausführung der Anwendung.  Zudem können Sie die Datensammlung mit der Instrumentationsmethode erwägen.|  
|[DA0026: Übermäßige CPU\-Zeit für die Kernelverarbeitung](../profiling/da0026-excessive-kernel-cpu-time-processing.md)|Eine erhebliche Menge Zeit wurde bei der Profilerstellung im Prozessorkernelmodus verbracht.  Erwägen Sie, als Metrik beim Sampling Systemaufrufe statt der Zeit zu verwenden.|  
|[DA0029: Nicht unterstützte CLR\-Version](../profiling/da0029-unsupported-clr-version.md)|Für die Binärdatei, für die Sie ein Profil erstellt haben, wird eine Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] verwendet, die vom Profiler nicht unterstützt wird.  Von den Profilerberichten können keine Symbolnamen aufgelöst werden.|  
|[DA0030: Sammeln Sie Ebeneninteraktions\-Messdaten für Datenbankprojekte.](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|Es wurde eine erhebliche Anzahl von Aufrufen von Methoden im <xref:System.Data?displayProperty=fullName>\-Namespace gesammelt.  Um Daten zu den Datenbankaufrufen einzuschließen, erwägen Sie, bei der Profilerstellung Ebeneninteraktionsdaten zu sammeln.|