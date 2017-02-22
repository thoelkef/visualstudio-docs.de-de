---
title: "DA0502: Maximale CPU-Auslastung durch den Prozess, f&#252;r den die Profilerstellung ausgef&#252;hrt wird | Microsoft Docs"
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
  - "vs.performance.rules.DA0502"
  - "vs.performance.DA0502"
  - "vs.performance.502"
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0502: Maximale CPU-Auslastung durch den Prozess, f&#252;r den die Profilerstellung ausgef&#252;hrt wird
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0502|  
|Kategorie \(Category\)|Ressourcenüberwachung|  
|Profilerstellungsmethode|Alle|  
|Meldung|Diese Regel dient nur als Information.  Der Leistungsindikator für die Process\(\)\\%\-Prozessorzeit dient zum Messen der CPU\-Auslastung des Prozesses, für den die Profilerstellung ausgeführt wird.  Bei dem gemeldeten Wert handelt es sich um den Maximalwert aus allen Messintervallen.|  
|Regeltyp|Information|  
  
 Wenn Sie mit der Sampling\-, .NET\-Arbeitsspeicher\- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## Regelbeschreibung  
 In dieser Meldung wird der maximale Prozentsatz der Zeit gemeldet, die ein Prozessor mit dem Ausführen von Anweisungen aus der Anwendung beschäftigt war.  Bei dem gemeldeten Wert handelt es sich um den Maximalwert aller Messintervalle, in denen der Prozess, dessen Profil erstellt wird, aktiv war.  Bei einem Computer mit mehreren Prozessoren kann der Prozentsatz 100 Prozent übersteigen.  
  
## Verwenden der Regeldaten  
 Mithilfe des Regelwerts können Sie die Leistung anderer Versionen oder Builds des Programms vergleichen oder die Leistung der Anwendung in unterschiedlichen Profilerstellungsszenarien nachvollziehen.