---
title: "Leistungsregeln f&#252;r die Ressourcen&#252;berwachung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Leistungsregeln f&#252;r die Ressourcen&#252;berwachung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Leistungsmeldungen in der Kategorie Ressourcenüberwachung enthalten zusätzliche Daten zur Leistung der Anwendung.  Mithilfe dieser Daten können Sie Leistungsprobleme analysieren.  Diese Regeln sind zu Informationszwecken gedacht und werden für jede Profilerstellungsausführung gemeldet.  
  
|||  
|-|-|  
|[DA0501: Durchschnittliche CPU\-Auslastung durch den Prozess, für den die Profilerstellung ausgeführt wird.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|In dieser Meldung wird der Prozentsatz der Zeit gemeldet, die ein Prozessor mit dem Ausführen von Anweisungen aus der Anwendung beschäftigt war.  Bei dem gemeldeten Wert handelt es sich um den Durchschnittswert aller Messintervalle, in denen der Prozess, dessen Profil erstellt wird, aktiv war.|  
|[DA0502: Maximale CPU\-Auslastung durch den Prozess, für den die Profilerstellung ausgeführt wird](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|In dieser Meldung wird der maximale Prozentsatz der Zeit gemeldet, die ein Prozessor mit dem Ausführen von Anweisungen aus der Anwendung beschäftigt war.  Bei dem gemeldeten Wert handelt es sich um den Maximalwert aller Messintervalle, in denen der Prozess, dessen Profil erstellt wird, aktiv war.|  
|[DA0503: Durchschnittliche Arbeitsseite in Bytes für den Prozess, für den die Profilerstellung ausgeführt wird](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Diese Meldung gibt Aufschluss über die durchschnittliche Menge physischen Speichers \(in Byte\), die vom Prozess verwendet wurde, während die Profilerstellung aktiv war.  Dieses Measure des physischen Speichers wird als Workingset bezeichnet.|  
|[DA0504: Maximale Arbeitsseite in Bytes für den Prozess, für den die Profilerstellung ausgeführt wird](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Diese Meldung gibt Aufschluss über die maximale Menge physischen Speichers \(in Byte\), die vom Prozess verwendet wurde, während die Profilerstellung aktiv war.|  
|[DA0505: Durchschnittliche private Bytes, die für den Prozess zugeordnet sind, für den die Profilerstellung ausgeführt wird](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Diese Meldung gibt Aufschluss über die durchschnittliche Menge virtuellen Speichers \(in Bytes\), die vom Prozess belegt wurde, während die Profilerstellung aktiv war.  Dieses Measure des virtuellen Arbeitsspeichers wird als *private Bytes* bezeichnet.  Private Bytes stellen virtuelle Speicherorte dar, die durch den Prozess belegt wurden und auf die nur von im Prozess ausgeführten Threads zugegriffen werden kann.|  
|[DA0506: Maximale private Bytes, die für den Prozess zugeordnet sind, für den die Profilerstellung ausgeführt wird](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Diese Meldung gibt Aufschluss über die maximale Menge virtuellen Speichers \(in privaten Bytes\), die vom Prozess belegt wurde, während die Profilerstellung aktiv war.|