---
title: "DA0002: VSPerfCorProf.dll fehlt | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0002"
  - "vs.performance.2"
  - "vs.performance.rules.DAVsPerfCorProfMissing"
  - "vs.performance.rules.DA0002"
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0002: VSPerfCorProf.dll fehlt
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0002|  
|Kategorie \(Category\)|Verwendung der Profilerstellungstools|  
|Profilerstellungsmethoden|Profilerstellung mit den Befehlszeilentools VSPerfCmd und VSPerfASPNETCmd|  
|Meldung|Es scheint, als wurde die Datei aufgelistet, ohne die Umgebungsvariablen mit "VSPerfCLREnv.cmd" ordnungsgemäß festzulegen.  Symbole für verwaltete Binärdateien können möglicherweise nicht aufgelöst werden.|  
|Regeltyp|Information|  
  
## Ursache  
 "VSPerfCorProf.dll" wurde während der Profilerstellung nicht gefunden.  Diese Warnung wird ausgegeben, wenn für die Auflistung der Profilerdaten Befehlszeilentools ohne das Tool "VSPerfCLREnv.cmd" verwendet werden, das zum Initialisieren der erforderlichen Umgebungsvariablen dient.  Die Warnung kann auch ausgelöst werden, wenn ein anderer Profiler ausgeführt wird, wenn die Profilerstellungstools gestartet werden.  
  
## Regelbeschreibung  
 Bestimmte Umgebungsvariablen müssen vor einer Profilerstellungsausführung festgelegt werden, damit der Profiler die Symbole in .NET Framework\-Binärdateien auflöst.  In der Warnung wird vorgeschlagen, dass das Tool "VSPerfCLREnv.cmd" nicht ausgeführt wurde, bevor die Profilerstellungsdaten erfasst wurden.  Symbole für verwaltete Binärdateien werden möglicherweise nicht aufgelöst.  Weitere Informationen zum Verwenden der Profilerstellungstools von der Befehlszeile aus finden Sie unter [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md).  
  
## Behandeln von Verstößen  
 Wenn Sie die Profilerstellung für verwaltete Anwendungen mit den Befehlszeilentools in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools ausführen, führen Sie das Befehlszeilentool [VSPerfCLREnv](../profiling/vsperfclrenv.md) aus, bevor Sie die Datenerfassung starten.