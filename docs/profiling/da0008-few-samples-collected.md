---
title: "DA0008: Es wurden nur wenige Beispiele aufgelistet | Microsoft Docs"
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
  - "vs.performance.rules.DATooFewSamples"
  - "vs.performance.8"
  - "vs.performance.DA0008"
  - "vs.performance.rules.DA0008"
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0008: Es wurden nur wenige Beispiele aufgelistet
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0008|  
|Kategorie \(Category\)|Verwendung der Profilerstellungstools|  
|Profilerstellungsmethode|Sampling|  
|Meldung|Es wurden nur wenige Samplings gesammelt.  Sie sollten eine längere Ausführung oder eine schnellere Samplingrate in Betracht ziehen, um aussagekräftigere Ergebnisse zu erzielen.|  
|Regeltyp|Information|  
  
## Ursache  
 Während der Profilerstellung wurden nur wenige Samplings gesammelt.  
  
## Regelbeschreibung  
 Wenn die Samplingmethode verwendet wird, sollten Sie eine statistisch signifikante Anzahl von Samplings sammeln, um sicherzustellen, dass die Daten für das tatsächliche Programmverhalten repräsentativ sind.  Um Samplingfehler zu minimieren, sollten Sie versuchen, mindestens 1.000 Samplings für Programmanweisungsausführungsverhalten zu sammeln.  Wenn Sie nicht genug Samplings sammeln, kann die Analyse der Profilerstellungsdaten irreführend sein.  
  
## Behandeln von Verstößen  
 Überlegen Sie, das Profil bei einer längeren Ausführung der Anwendung zu erstellen oder eine schnellere Samplingrate zu verwenden, um statistisch signifikante Ergebnisse zu erzielen.  Weitere Informationen zum Ändern der Samplingrate in der Visual Studio IDE finden Sie unter [Gewusst wie: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md).  Weitere Informationen zum Ändern der Samplingrate bei Verwendung der Profilerstellungstool\-Befehlszeile finden Sie unter [Zeitgeber](../profiling/timer.md) in der [VSPerfCmd](../profiling/vsperfcmd.md)\-Referenz.