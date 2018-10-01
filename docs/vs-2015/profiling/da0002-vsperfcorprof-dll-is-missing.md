---
title: 'DA0002: „VSPerfCorProf.dll“ fehlt | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54c43143fae898b5a8177d4710bd335e2b8919f2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522486"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: VSPerfCorProf.dll fehlt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [DA0002: VSPerfCorProf.dll fehlt](https://docs.microsoft.com/visualstudio/profiling/da0002-vsperfcorprof-dll-is-missing).  
  
Regel-Id | DA0002 |  
| Kategorie | Verwendung der Profilerstellungstools |  
| Profilerstellungsmethoden | Profilerstellung mithilfe der Befehlszeilentools VSPerfCmd und VSPerfASPNETCmd |  
| Nachricht | Offenbar wurde die Datei ohne ordnungsgemäße Festlegen der Umgebungsvariablen mit "VSPerfCLREnv.cmd" erfasst. Symbole für verwaltete Binärdateien können nicht aufgelöst werden. |  
| Regeltyp | Informationen |  
  
## <a name="cause"></a>Ursache  
 Der Profiler konnte „VSPerfCorProf.dll“ während der Profilerstellung nicht finden. Diese Warnung tritt auf, wenn Befehlszeilentools für die Erfassung von Profilerdaten nicht zusammen mit dem Tool „VSPerfCLREnv.cmd“ verwendet werden, um die nötigen Umgebungsvariablen zu initialisieren. Die Warnung kann auch ausgelöst werden, wenn ein anderer Profiler beim Start der Profilerstellungstools ausgeführt wird.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Vor der Profilerstellung müssen bestimmte Umgebungsvariablen festgelegt werden, damit der Profiler die Symbole in .NET Framework-Binärdateien auflösen kann. In der Warnung wird darauf hingewiesen, dass das Tool „VSPerfCLREnv.cmd“ nicht vor der Erfassung der Profilerstellungsdaten ausgeführt wurde. Die Symbole für verwaltete Binärdateien können möglicherweise nicht aufgelöst werden. Weitere Informationen finden Sie unter [Verwenden der Profilerstellungstools über die Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md).  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Wenn Sie für verwaltete Anwendungen mithilfe der Befehlszeilentools in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools Profile erstellen, führen Sie das Befehlszeilentool [VSPerfCLREnv](../profiling/vsperfclrenv.md) aus, bevor Sie mit dem Erfassen von Daten beginnen.



