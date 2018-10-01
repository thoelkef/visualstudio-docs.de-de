---
title: 'Vorgehensweise: Auswählen von Sammlungsmethoden | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
ms.assetid: c87cfd3a-0fc7-49ae-9c05-d8480891cc63
caps.latest.revision: 39
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0aaa4c13509d02deacd719a52c2ac6514d4c0827
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510239"
---
# <a name="how-to-choose-collection-methods"></a>Gewusst wie: Auswählen von Sammlungsmethoden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Auswählen von Sammlungsmethoden](https://docs.microsoft.com/visualstudio/profiling/how-to-choose-collection-methods).  
  
Die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools unterstützen drei Methoden zum Sammeln von Leistungsdaten: Sampling, Instrumentierung und Parallelität. Sie können zum Sammeln von Daten zur .NET-Speicherbelegung und Lebensdauerdaten entweder die Sampling- oder Instrumentierungsmethode verwenden.  
  
 **Anforderungen**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
 Sie können die die Eigenschaft **Methode** der Leistungssitzung verwenden, um die geeignetste Sammlungsmethode für Ihre Anwendung anzugeben. Sie können die Sammelmethode vom Leistungs-Assistent, Leistungs-Explorer oder von den Eigenschaftenseiten der Leistungssitzung festlegen. Wenn Sie die Befehlszeilentools verwenden, finden Sie weitere Informationen unter [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md).  
  
## <a name="performance-wizard"></a>Leistungs-Assistent  
  
#### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>So wählen Sie eine Sammlungsmethode mithilfe des Leistungs-Assistent aus  
  
-   Wählen Sie auf der ersten Seite des Assistenten eine der folgenden Optionen aus:  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**CPU-Sampling**|Sammelt Anwendungsstatistiken, die für die erste Analyse und zum Analysieren von CPU-Auslastungsproblemen nützlich sind.|  
|**Instrumentation**|Sammelt ausführliche Zeitsteuerungsdaten, die zur gezielten Analyse und zur Analyse von Eingabe/Ausgabe-Leistungsproblemen nützlich sind.|  
|**.NET-Speicherbelegung**|Sammelt [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Speicherbelegungsdaten mithilfe der Sampling-Profilerstellungsmethode.|  
|**Parallelität**|Sammelt numerischen Ressourcenkonfliktdaten.|  
  
## <a name="performance-explorer"></a>Leistungs-Explorer  
  
#### <a name="to-select-a-collection-method-using-performance-explorer"></a>So wählen Sie eine Sammelmethode mithilfe des Leistungs-Explorers aus  
  
1.  Klicken Sie auf der Symbolleiste **Leistungs-Explorer** auf den Pfeil neben der Dropdownliste **Methode**  
  
2.  Klicken Sie auf die Sammlungsmethode, die Sie bevorzugen.  
  
## <a name="performance-session-property-pages"></a>Eigenschaftenseiten der Leistungssitzung  
  
#### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>So wählen Sie die Sampling- und Instrumentationsmethode mithilfe den Eigenschaften der Leistungssitzung aus  
  
1.  Klicken Sie im **Leistungs-Explorer** auf die Leistungssitzung.  
  
     Ein Dateiname einer Leistungssitzung hat die Dateiendung „.psess“.  
  
2.  Klicken Sie im mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Klicken Sie in den **Eigenschaftenseiten** auf **Allgemein**.  
  
4.  Klicken Sie auf die Sammlungsmethode, die Sie bevorzugen.  
  
    -   Informationen zu den anderen Optionen, die beim Sammeln von Samplingdaten verfügbar sind, finden Sie unter [Sammeln von Leistungsstatistiken durch Sampling](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
    -   Informationen zu den anderen Optionen, die beim Sammeln von Samplingdaten verfügbar sind, finden Sie unter [Sammeln von ausführlichen Zeitsteuerdaten durch Instrumentation](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)  
  
#### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>So wählen Sie die Datensammlung des .NET-Speichers mithilfe der Eigenschaften der Leistungssitzung aus.  
  
1.  Klicken Sie im **Leistungs-Explorer** auf die Leistungssitzung.  
  
     Ein Dateiname einer Leistungssitzung hat die Dateiendung „.psess“.  
  
2.  Klicken Sie im mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Klicken Sie in den **Eigenschaftenseiten** auf **Allgemein**.  
  
4.  Klicken Sie auf **Sampling** oder **Instrumentation**.  
  
5.  Klicken Sie zum Sammeln von der Größe und Anzahl von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Objektzuweisungen auf **.NET-Objektzuweisungsinformationen auflisten**.  
  
6.  (Optional) Klicken Sie auf **Lebensdauerinformation für .NET-Objekte auflisten** zum Sammeln von Daten über die Generierung der automatische Speicherbereinigung, in dem der Objektspeicher freigegeben wurde.  
  
     Informationen zu den anderen Optionen, die beim Sammeln von .NET-Speicherdaten verfügbar sind, finden Sie unter [Sammeln von Daten zur .NET-Speicherbelegung und Lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).  
  
#### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>So wählen Sie die Sammlung von Parallelitätsdaten mithilfe der Eigenschaften der Leistungssitzung aus.  
  
1.  Klicken Sie im **Leistungs-Explorer**mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie in den **Eigenschaftenseiten** auf **Allgemein**.  
  
3.  Klicken Sie auf **Parallelität**.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Grundlagen zu Samplingdatenwerten](../profiling/understanding-sampling-data-values.md)   
 [Eigenschaften von Leistungssitzungen](../profiling/performance-session-properties.md)



