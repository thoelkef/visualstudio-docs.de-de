---
title: 'DA0002: „VSPerfCorProf.dll“ fehlt | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5723506415a0ddbf816b896e23e93eaa706bf7e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158728"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: „VSPerfCorProf.dll“ fehlt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regel-ID | DA0002 |  
| Kategorie | Profilerstellungstools Verwendung |  
| Profil Erstellungs Methoden | Profilerstellung mithilfe der Befehlszeilen Tools VSPerfCmd und vsperfaspnetcmd |  
| Meldung | Es scheint, als die Datei gesammelt wurde, ohne dass die Umgebungsvariablen ordnungsgemäß mit "VSPerfCLREnv. cmd" festgelegt wurden. Die Symbole für verwaltete Binärdateien können möglicherweise nicht aufgelöst werden.|  
| Regeltyp | Informationen |  
  
## <a name="cause"></a>Ursache  
 Der Profiler konnte „VSPerfCorProf.dll“ während der Profilerstellung nicht finden. Diese Warnung tritt auf, wenn Befehlszeilentools für die Erfassung von Profilerdaten nicht zusammen mit dem Tool „VSPerfCLREnv.cmd“ verwendet werden, um die nötigen Umgebungsvariablen zu initialisieren. Die Warnung kann auch ausgelöst werden, wenn ein anderer Profiler beim Start der Profilerstellungstools ausgeführt wird.  
  
## <a name="rule-description"></a>Beschreibung der Regel  
 Vor der Profilerstellung müssen bestimmte Umgebungsvariablen festgelegt werden, damit der Profiler die Symbole in .NET Framework-Binärdateien auflösen kann. In der Warnung wird darauf hingewiesen, dass das Tool „VSPerfCLREnv.cmd“ nicht vor der Erfassung der Profilerstellungsdaten ausgeführt wurde. Die Symbole für verwaltete Binärdateien können möglicherweise nicht aufgelöst werden. Weitere Informationen zum Verwenden der Profilerstellungstools über die Befehlszeile finden Sie unter [Profilerstellung über die Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md) .  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Wenn Sie für verwaltete Anwendungen mithilfe der Befehlszeilentools in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools Profile erstellen, führen Sie das Befehlszeilentool [VSPerfCLREnv](../profiling/vsperfclrenv.md) aus, bevor Sie mit dem Erfassen von Daten beginnen.
