---
title: "CA2003: Fibers nicht als Threads behandeln | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2003"
  - "DoNotTreatFibersAsThreads"
helpviewer_keywords: 
  - "CA2003"
  - "DoNotTreatFibersAsThreads"
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2003: Fibers nicht als Threads behandeln
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotTreatFibersAsThreads|  
|CheckId|CA2003|  
|Kategorie \(Category\)|Microsoft.Reliability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein verwalteter Thread wird als Win32\-Thread behandelt.  
  
## Regelbeschreibung  
 Es kann nicht davon ausgegangen werden, dass ein verwalteter Thread ein Win32\-Thread ist.  Es handelt sich um ein Fiber.  Die Common Language Runtime \(CLR\) führt verwaltete Threads als Fibers im Kontext von realen Threads aus, die SQL besitzt.  Diese Threads können im SQL Server\-Prozess über die AppDomains und sogar über die Datenbanken hinweg freigegeben.  Das Verwenden von verwaltetem lokalem Threadspeicher funktioniert zwar, doch es wird möglicherweise kein nicht verwalteter lokaler Threadspeicher verwendet, oder es wird möglicherweise nicht angenommen, dass der Code wieder auf dem aktuellen Betriebssystemthread ausgeführt wird.  Ändern Sie keine Einstellungen z. B. das Gebietsschema des Threads.  Rufen Sie nicht CreateCriticalSection oder CreateMutex über P\/Invoke auf, da diese erfordern, dass der Thread, der eine Sperre eingibt, die Sperre auch wieder aufhebt.  Da dies beim Verwenden von Fibers nicht der Fall ist, werden wichtige Win32\-Abschnitte und Mutexe in SQL nutzlos.  Die meisten Zustände eines verwalteten System.Thread\-Objekts können Sie gefahrlos verwenden.  Schließt verwalteten lokalen Threadspeicher und die aktuelle Benutzeroberflächenkultur des Threads ein.  Aufgrund des Programmiermodells können Sie jedoch die aktuelle Kultur eines Threads beim Verwenden von SQL jedoch nicht ändern. Dies wird durch eine neue Berechtigung erzwungen.  
  
## Behandeln von Verstößen  
 Untersuchen Sie die Verwendung von Threads, und ändern Sie den Code entsprechend.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Diese Regel sollte nicht unterdrückt werden.