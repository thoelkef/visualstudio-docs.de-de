---
title: "Legende der Kernansicht | Microsoft Docs"
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
  - "vs.cv.cores.legend"
helpviewer_keywords: 
  - "Concurrency Visualizer, Legende der Kernansicht"
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Legende der Kernansicht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Legende der Kernansicht ist jeder Thread mit Farbe und Namen angegeben.  Sie enthält Spalten ein, die Werte für kernübergreifende Kontextwechsel, gesamte Kontextwechsel und Prozentualer Anteil der Kontextwechsel, die durch Kerne verlaufen.  Zeilen in der Legende sind nach Anzahl der kernübergreifenden Kontextwechsel, in absteigender Reihenfolge sortiert.  
  
 Sie können Zeilen in der Legende auswählen, um die Threads zu filtern, die in der Zeitachse angezeigt werden.  Nur die ausgewählten Threads werden in der Zeitachse dargestellt.  Wenn keine Zeilen ausgewählt werden, werden alle Zeilen der Zeitachse dargestellt.  
  
 Kernübergreifende Kontextwechsel kosten mehr im Mehraufwand und Leistung als Schalter, die auf demselben logischen Kern nicht.  Während der Kontextwechsel werden die Prozessorregister gespeichert und wiederhergestellt, wird der Betriebssystemkernelcode ausgeführt, werden die Adressenumsetzpuffereinträge erneut geladen, und die Prozessorpipeline wird geleert.  Kernübergreifende Kontextwechsel können als andere Kontextwechsel sogar kostenintensiv sein, da die Cachedaten für den Thread auf einen anderen Kern ungültig sind.  Wenn ein Thread auf den Kern Kontext\-umgeschaltet wird, wurde er zuvor ausgeführt, ist es wahrscheinlich, dass die nützliche noch Daten im Cache.  Wenn kernübergreifende Kontextwechsel durch Versuche, zur Verwaltung der Threadaffinität erhöht wurden und die Leistung beeinträchtigt wird, überprüfen Sie, ob dieses Problem verweist.  Anfang, indem Threadaffinität beseitigt, und beachten dann auf das resultierende kernübergreifende Verhalten.  
  
 In der folgenden Tabelle sind die Legendenelemente beschrieben.  
  
|Element|Definition|  
|-------------|----------------|  
|Thread Name|Zeigt die Farbe des Threads auf der Zeitachse des vorherigen Kerns sowie den Namen des betreffenden Threads.|  
|Kernübergreifende Kontextwechsel|Die Anzahl der Kontextwechsel für einen Thread, bei denen auch von einem logischen Kern zu einem anderen gewechselt wurde.  Dabei wird nicht zwischen kernübergreifenden Kontextwechseln, bei denen von einem Prozessorwürfel zu anderen für die schneiden, die auf demselben Löschen bleiben.|  
|Gesamte Kontextwechsel|Die Gesamtzahl der Kontextwechsel für einen angegebenen Thread während des Samplingzeitraums.  Jedes Mal, wenn ein Thread den Kontext wechselt \(z. B. von der Ausführung zur Synchronisierung\), wird ein Kontextwechsel gezählt.|  
|Prozentualer Anteil der Kontextwechsel, die durch Kerne verlaufen|Wird als Prozentsatz berechnet, indem die Anzahl der kernübergreifenden Kontextwechsel durch die Anzahl der gesamten Kontextwechsel geteilt wird.  Je höher dieser Prozentsatz ist, desto größer sind die Gesamtauswirkungen des Mehraufwands durch kernübergreifende Kontextwechsel auf die Leistung des betreffenden Threads.|  
  
## Siehe auch  
 [Kernansicht](../profiling/cores-view.md)