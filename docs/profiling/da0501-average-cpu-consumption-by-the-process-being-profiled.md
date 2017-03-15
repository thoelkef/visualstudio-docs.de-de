---
title: "DA0501: Durchschnittliche CPU-Auslastung durch den Prozess, f&#252;r den die Profilerstellung ausgef&#252;hrt wird. | Microsoft Docs"
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
  - "vs.performance.rules.DA0501"
  - "vs.performance.DA0501"
  - "vs.performance.501"
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0501: Durchschnittliche CPU-Auslastung durch den Prozess, f&#252;r den die Profilerstellung ausgef&#252;hrt wird.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA501|  
|Kategorie \(Category\)|Ressourcenüberwachung|  
|Profilerstellungsmethode|Alle|  
|Meldung|Durchschnittliche CPU\-Auslastung durch den Prozess, für den die Profilerstellung ausgeführt wird.|  
|Regeltyp|Information|  
  
 Wenn Sie mit der Sampling\-, .NET\-Arbeitsspeicher\- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## Regelbeschreibung  
 In dieser Meldung wird der Prozentsatz der Zeit gemeldet, die ein Prozessor mit dem Ausführen von Anweisungen aus der Anwendung beschäftigt war.  Bei dem gemeldeten Wert handelt es sich um den Durchschnittswert aller Messintervalle, in denen der Prozess, dessen Profil erstellt wird, aktiv war.  Bei einem Computer mit mehreren Prozessoren kann der Wert 100 Prozent übersteigen.  
  
## Verwenden von Regeldaten  
 Mithilfe des Regelwerts können Sie die Leistung anderer Versionen oder Builds des Programms vergleichen oder die Leistung der Anwendung in unterschiedlichen Testszenarien nachvollziehen.