---
title: "DA0004: Hohe Prozessorauslastung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAHighProcessorUsage"
  - "vs.performance.rules.DA0004"
  - "vs.performance.DA0004"
  - "vs.performance.4"
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# DA0004: Hohe Prozessorauslastung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0004|  
|Kategorie \(Category\)|Verwendung der Profilerstellungstools|  
|Profilerstellungsmethoden|Instrumentation<br /><br /> Sampling|  
|Meldung|Die Prozessorauslastung liegt permanent über 75%.  Sie sollten die Verwendung des Samplingmodus für CPU\-gebundene Anwendungen in Betracht ziehen.|  
|Regeltyp|Information|  
  
 Wenn Sie mit der Sampling\-, .NET\-Arbeitsspeicher\- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## Ursache  
 Die Prozessorauslastung \(CPU\) war in den Profilerstellungsdaten, die mithilfe der Instrumentationsmethode gesammelt wurden, sehr hoch.  Verwenden Sie bei der Profilerstellung für eine CPU\-gebundene Anwendung ggf. die Samplingmethode zur Profilerstellung.  
  
## Regelbeschreibung  
 Während dieser Profilerstellungsausführung ist der Prozessor \(oder die Prozessoren\) gleichbleibend stark ausgelastet.  Eine hohe CPU\-Auslastung kann auf eine CPU\-gebundene Anwendung hindeuten.  Instrumentierte Profile sind normalerweise nicht die effektivste Möglichkeit, CPU\-Verwendungsszenarien zu untersuchen.  Sampling ist normalerweise wirksamer, wenn Sie Anwendungen profilieren, die viel Zeit mit dem Ausführen von Anweisungen auf dem Prozessor verbringen.  
  
## Behandeln von Verstößen  
 Erwägen Sie die erneute Profilerstellung für die Anwendung mit der Samplingmethode statt der Instrumentationsmethode, außer wenn Sie Funktionszeitliche Steuerungen benötigen oder Sie sich mehr für ein Verständnis der Eingabe\/Ausgabe als für Prozessorengpässe interessieren.