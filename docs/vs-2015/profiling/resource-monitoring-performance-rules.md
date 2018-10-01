---
title: Leistungsregeln für die Ressourcenüberwachung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b2bd11b8b18e5dd4e3f6625b1b269d104a6fd5a5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521216"
---
# <a name="resource-monitoring-performance-rules"></a>Leistungsregeln für die Ressourcenüberwachung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Resource Monitoring Leistungsregeln](https://docs.microsoft.com/visualstudio/profiling/resource-monitoring-performance-rules).  
  
Über Leistungsmeldungen in der Kategorie „Ressourcenüberwachung“ erhalten Sie zusätzliche Informationen zur Leistung Ihrer Anwendung. Sie können diese Daten verwenden, um Probleme mit der Leistung zu analysieren. Diese Regeln haben einen informativen Charakter und werden bei jeder Profilerstellung angezeigt.  
  
|||  
|-|-|  
|[DA0501: Durchschnittliche CPU-Auslastung durch den Prozess, für den die Profilerstellung ausgeführt wird.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|In dieser Meldung wird der Prozentsatz der Zeit angegeben, die ein Prozessor mit dem Ausführen von Anweisungen aus der Anwendung beschäftigt war. Bei dem gemeldeten Wert handelt es sich um den Durchschnittswert aller Messintervalle, in denen der Prozess, dessen Profil erstellt wird, aktiv war.|  
|[DA0502: Maximale CPU-Auslastung durch den Prozess, für den die Profilerstellung ausgeführt wird](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|In dieser Meldung wird der maximale Prozentsatz der Zeit angegeben, die ein Prozessor mit dem Ausführen von Anweisungen aus der Anwendung beschäftigt war. Bei dem gemeldeten Wert handelt es sich um den Maximalwert aller Messintervalle, in denen der Prozess, dessen Profil erstellt wird, aktiv war.|  
|[DA0503: Durchschnittliche Arbeitsseite in Bytes für den Prozess, für den die Profilerstellung ausgeführt wird](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Diese Meldung gibt Aufschluss über die durchschnittliche Menge an physischem Speicher (in Bytes), der von dem Prozess bei der Profilerstellung belegt wurde. Diese Einheit für den physischen Speicher ist unter der Bezeichnung „Arbeitssatz“ bekannt.|  
|[DA0504: Maximale Arbeitsseite in Bytes für den Prozess, für den die Profilerstellung ausgeführt wird](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|In dieser Meldung wird die maximale Menge an physischem Arbeitsspeicher (in Bytes) angegeben, der von dem Prozess bei der Profilerstellung belegt wurde.|  
|[DA0505: Durchschnittliche private Bytes, die für den Prozess zugeordnet sind, für den die Profilerstellung ausgeführt wird](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|In dieser Meldung wird die durchschnittliche Menge an virtuellem Arbeitsspeicher in Bytes angegeben, der von dem Prozess bei der Profilerstellung belegt wurde. Diese Einheit für den virtuellen Speicher ist unter der Bezeichnung *private Bytes* bekannt. Private Bytes stellen virtuelle Speicherorte dar, die durch den Prozess belegt wurden und auf die nur von im Prozess ausgeführten Threads zugegriffen werden kann.|  
|[DA0506: Maximale private Bytes, die für den Prozess zugeordnet sind, für den die Profilerstellung ausgeführt wird](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|In dieser Meldung wird die maximale Menge an virtuellem Arbeitsspeicher in privaten Bytes angegeben, der von dem Prozess bei der Profilerstellung belegt wurde.|



