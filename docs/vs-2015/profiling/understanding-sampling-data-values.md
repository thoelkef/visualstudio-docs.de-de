---
title: Grundlagen zu Samplingdatenwerten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 91a4a50ecc745c0b56167d6a5dbb1932af7ed2bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145425"
---
# <a name="understanding-sampling-data-values"></a>Grundlagen zu Samplingdatenwerten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die *Samplingmethode* zur Profilerstellung der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools unterbricht den Computerprozessor in festgelegten Intervallen und erfasst die Funktionsaufrufliste. Eine *Aufrufliste* ist eine dynamische Struktur, die Informationen über die Funktionen speichert, die auf dem Prozessor ausgeführt werden.  
  
 **Anforderungen**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Die Profileranalyse ermittelt, ob der Prozessor Code im Zielprozess ausführt. Wenn der Prozessor keinen Code im Zielprozess ausführt, wird das Sampling verworfen.  
  
  Wenn der Prozessor den Zielcode ausführt, erhöht der Profiler die Samplinganzahl für jede Funktion in der Aufrufliste. Während der Erfassung des Samplings führt nur eine Funktion in der Aufrufliste Code aus. Die anderen Funktionen in der Liste sind übergeordnete Elemente in der Hierarchie von Funktionsaufrufen, die auf den Abschluss ihrer untergeordneten Elemente warten.  
  
  Für das Samplingereignis erhöht der Profiler die *exklusive* Samplinganzahl der Funktion, die gerade die Anweisungen ausführt. Da ein exklusives Sampling auch Teil der gesamten (*inklusiven*) Samplings der Funktion ist, wird die inklusive Samplinganzahl der aktuell aktiven Funktion auch erhöht.  
  
  Der Profiler erhöht die inklusive Samplinganzahl aller anderen Funktionen in der Aufrufliste.  
  
## <a name="inclusive-samples"></a>Inklusive Samplinganzahl  
 Die Gesamtanzahl der Samplings, die während der Ausführung der Zielfunktion erfasst werden.  
  
 Dies umfasst Samplings, die während der direkten Ausführung des Funktionscodes erfasst werden, und Samples, die während der Ausführung von untergeordneten Funktionen erfasst werden, die von der Zielfunktion aufgerufen werden.  
  
## <a name="exclusive-samples"></a>Exklusive Samplinganzahl  
 Die Anzahl der Samplings, die während der direkten Ausführung der Anweisungen der Zielfunktion erfasst werden.  
  
 Exklusive Samplings beinhalten keine Samplings, die während der Ausführung von Funktionen erfasst werden, die von der Zielfunktion aufgerufen werden.  
  
## <a name="inclusive-percent"></a>Inklusive Samplings in Prozent  
 Der prozentuale Anteil der Gesamtanzahl inklusiver Samplings in der Profilerstellungsausführung, die inklusive Samplings der Funktion oder des Datenbereichs sind.  
  
## <a name="exclusive-percent"></a>Exklusive Samplings in Prozent  
 Der prozentuale Anteil der Gesamtanzahl exklusiver Samplings in der Profilerstellungsausführung, die exklusive Samplings der Funktion oder des Datenbereichs sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorgehensweise: Auswählen von Sammlungs Methoden](../profiling/how-to-choose-collection-methods.md)   
 [Analysieren von Leistungs Tool Daten](../profiling/analyzing-performance-tools-data.md)
