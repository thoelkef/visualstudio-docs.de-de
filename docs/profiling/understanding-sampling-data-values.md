---
title: "Grundlagen zu Samplingdatenwerten in Profilerstellungstools | Microsoft Docs"
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
  - "Sampling-Profilerstellungsmethode"
  - "Profilerstellungstools, Sampling"
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Grundlagen zu Samplingdatenwerten in Profilerstellungstools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die *Samplingmethode* zur Profilerstellung der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools unterbricht den Computerprozessor in festgelegten Intervallen und erfasst die Funktionsaufrufliste.  Eine *Aufrufliste* ist eine dynamische Struktur, die Informationen über die Funktionen speichert, die auf dem Prozessor ausgeführt werden.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Die Profileranalyse ermittelt, ob der Prozessor Code im Zielprozess ausführt.  Wenn der Prozessor keinen Code im Zielprozess ausführt, wird das Sampling verworfen.  
  
 Wenn der Prozessor den Zielcode ausführt, erhöht der Profiler die Samplinganzahl für jede Funktion in der Aufrufliste.  Während der Erfassung des Samplings führt nur eine Funktion in der Aufrufliste Code aus.  Bei den anderen Funktionen in der Liste handelt es sich um übergeordnete Elemente in der Hierarchie von Funktionsaufrufen, die auf den Abschluss der Ausführung ihrer untergeordneten Elemente warten.  
  
 Für das Samplingereignis erhöht der Profiler die *exklusive* Samplinganzahl der Funktion, die ihre Anweisungen gerade ausführt.  Da ein exklusives Sampling auch Teil der gesamten \(*inklusiven*\) Samplings für die Funktion ist, wird die inklusive Samplinganzahl der aktuell aktiven Funktion auch erhöht.  
  
 Der Profiler inkrementiert die inklusive Samplinganzahl aller anderen Funktionen in der Aufrufliste.  
  
## Inclusive Samplings  
 Die Gesamtzahl der Samplings, die während der Ausführung der Zielfunktion erfasst werden.  
  
 Dies umfasst Samplings, die während der direkten Ausführung des Funktionscodes erfasst werden, und Samples, die während der Ausführung von untergeordneten Funktionen erfasst werden, die von der Zielfunktion aufgerufen werden.  
  
## Exclusive Samplings  
 Die Anzahl der Samplings, die während der direkten Ausführung der Anweisungen der Zielfunktion erfasst werden.  
  
 Exklusive Samplings beinhalten keine Samplings, die während der Ausführung von Funktionen erfasst werden, die von der Zielfunktion aufgerufen werden.  
  
## Inclusive Percent  
 Der Prozentsatz der Gesamtanzahl inklusiver Samplings in der Profilerstellungsausführung, die inklusive Samplings der Funktion oder des Datenbereichs sind.  
  
## Exclusive Percent  
 Der Prozentsatz der Gesamtanzahl exklusiver Samplings in der Profilerstellungsausführung, die exklusive Samplings der Funktion oder des Datenbereichs sind.  
  
## Siehe auch  
 [Gewusst wie: Auswählen von Sammlungsmethoden](../profiling/how-to-choose-collection-methods.md)   
 [Analysieren der durch Profilerstellungstools erstellten Daten](../profiling/analyzing-performance-tools-data.md)