---
title: "Gewusst wie: Ausw&#228;hlen von Sammlungsmethoden | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Leistungstools, Auswählen einer Auflistungsmethode"
  - "Profilerstellungstools, Auswählen einer Auflistungsmethode"
  - "Leistungsauflistungsmethoden"
ms.assetid: c87cfd3a-0fc7-49ae-9c05-d8480891cc63
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Ausw&#228;hlen von Sammlungsmethoden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools unterstützen drei Methoden, Leistungsdaten zu sammeln: Sampling, Instrumentation und Parallelität.  Zudem können Sie die Sampling\- oder die Instrumentationsmethode auch zum Sammeln von .NET\-Speicherbelegungs\- und Lebensdauerdaten verwenden.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Mithilfe der **Method**\-Eigenschaft der Leistungssitzung können Sie die für die Anwendung geeignete Sammlungsmethode angeben.  Sie können die Auflistungsmethode im Leistungs\-Assistenten, im Leistungs\-Explorer oder auf den Eigenschaftenseiten einer Leistungssitzung festlegen.  Bei Verwendung von Befehlszeilentools finden Sie im Abschnitt [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md) weitere Informationen.  
  
## Leistungs\-Assistent  
  
#### So wählen Sie eine Sammlungsmethode mit dem Leistungs\-Assistenten aus  
  
-   Auf der ersten Seite des Assistenten wählen Sie eine der folgenden Optionen aus:  
  
|Option|**Beschreibung**|  
|------------|----------------------|  
|**CPU\-Sampling**|Sammelt Anwendungsstatistiken, die für ursprüngliche Analyse und zum Analysieren von CPU\-Auslastungsproblemen nützlich sind.|  
|**Instrumentation**|Sammelt ausführliche Zeitsteuerungsdaten, die für fokussierte Analysen und zum Analysieren von Leistungsproblemen bei der Eingabe\/Ausgabe nützlich sind.|  
|**.NET\-Speicherbelegung**|Sammelt [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Speicherbelegungsdaten mit der Sampling\-Profilerstellungsmethode.|  
|**Parallelität**|Sammelt numerische Ressourcenkonfliktdaten.|  
  
## Leistungs\-Explorer  
  
#### So wählen Sie eine Erfassungsmethode mit dem Leistungs\-Explorer aus  
  
1.  Klicken Sie auf der Symbolleiste **Leistungs\-Explorer** auf den Pfeil neben der Dropdownliste **Methode**.  
  
2.  Klicken Sie auf die bevorzugte Sammlungsmethode.  
  
## Eigenschaftenseiten für Leistungssitzungen  
  
#### So wählen Sie die Sampling\- oder Instrumentationsmethode mit Leistungssitzungseigenschaften aus  
  
1.  Wählen Sie im **Leistungs\-Explorer** die Leistungssitzung aus.  
  
     Der Dateiname einer Leistungssitzung weist die Erweiterung .psess auf.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Klicken Sie auf den **Eigenschaftenseiten** auf **Allgemein**.  
  
4.  Klicken Sie auf die bevorzugte Sammlungsmethode.  
  
    -   Informationen zu den anderen Optionen, die beim Sammeln von Samplingdaten verfügbar sind, finden Sie unter [Sammeln von Leistungsstatistiken durch Sampling](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
    -   Informationen zu den anderen Optionen, die beim Sammeln von Samplingdaten verfügbar sind, finden Sie unter [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentation](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).  
  
#### So wählen Sie die .NET\-Speicherdatensammlung mit Leistungssitzungseigenschaften aus  
  
1.  Wählen Sie im **Leistungs\-Explorer** die Leistungssitzung aus.  
  
     Der Dateiname einer Leistungssitzung weist die Erweiterung .psess auf.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Klicken Sie auf den **Eigenschaftenseiten** auf **Allgemein**.  
  
4.  Klicken Sie auf **Sampling** oder **Instrumentation**.  
  
5.  Klicken Sie auf **.NET\-Objektzuordnungsinformationen auflisten**, um die Größe und Anzahl von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Objektzuordnungen zu sammeln.  
  
6.  \(Optional\) Klicken Sie auf **Lebensdauerinformationen für .NET\-Objekt auflisten**, um Daten über die Garbage Collection\-Generierungen zu sammeln, in denen der Objektarbeitsspeicher freigegeben wurde.  
  
     Informationen zu den anderen Optionen, die beim Sammeln von .NET\-Speicherdaten verfügbar sind, finden Sie unter [Sammeln von Daten zur .NET\-Speicherbelegung und Lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).  
  
#### So wählen Sie die Parallelitätsdatensammlung mit Leistungssitzungseigenschaften aus  
  
1.  Klicken Sie im **Leistungs\-Explorer** mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf den **Eigenschaftenseiten** auf **Allgemein**.  
  
3.  Klicken Sie auf **Parallelität**.  
  
## Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Grundlagen zu Samplingdatenwerten](../profiling/understanding-sampling-data-values.md)   
 [Eigenschaften von Leistungssitzungen](../profiling/performance-session-properties.md)