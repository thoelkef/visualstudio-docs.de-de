---
title: "DA0002: „VSPerfCorProf.dll“ fehlt | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 348fe328caed15da059ae5d3e9dec3b9b334e4dd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: VSPerfCorProf.dll fehlt
|||  
|-|-|  
|Regel-ID|DA0002|  
|Kategorie|Verwendung der Profilerstellungstools|  
|Profilerstellungsmethoden|Profilerstellung mithilfe der Befehlszeilentools VSPerfCmd und VSPerfASPNETCmd|  
|Meldung|Anscheinend wurden bei der Dateierfassung die Umgebungsvariablen mit „VSPerfCLREnv.cmd“ nicht korrekt eingerichtet. Die Symbole für verwaltete Binärdateien können möglicherweise nicht aufgelöst werden.|  
|Regeltyp|Information|  
  
## <a name="cause"></a>Ursache  
 Der Profiler konnte „VSPerfCorProf.dll“ während der Profilerstellung nicht finden. Diese Warnung tritt auf, wenn Befehlszeilentools für die Erfassung von Profilerdaten nicht zusammen mit dem Tool „VSPerfCLREnv.cmd“ verwendet werden, um die nötigen Umgebungsvariablen zu initialisieren. Die Warnung kann auch ausgelöst werden, wenn ein anderer Profiler beim Start der Profilerstellungstools ausgeführt wird.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Vor der Profilerstellung müssen bestimmte Umgebungsvariablen festgelegt werden, damit der Profiler die Symbole in .NET Framework-Binärdateien auflösen kann. In der Warnung wird darauf hingewiesen, dass das Tool „VSPerfCLREnv.cmd“ nicht vor der Erfassung der Profilerstellungsdaten ausgeführt wurde. Die Symbole für verwaltete Binärdateien können möglicherweise nicht aufgelöst werden. Weitere Informationen finden Sie unter [Verwenden der Profilerstellungstools über die Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md).  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Wenn Sie für verwaltete Anwendungen mithilfe der Befehlszeilentools in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools Profile erstellen, führen Sie das Befehlszeilentool [VSPerfCLREnv](../profiling/vsperfclrenv.md) aus, bevor Sie mit dem Erfassen von Daten beginnen.