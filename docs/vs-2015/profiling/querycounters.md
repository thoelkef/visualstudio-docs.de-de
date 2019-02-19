---
title: QueryCounters | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cdd2707a6af2b9d03e73c696884dc12413437b04
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54760124"
---
# <a name="querycounters"></a>QueryCounters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Option **QueryCounters** listet die CPU-Leistungsindikatoren (Hardware) auf, die auf dem Computer verfügbar sind.  
  
 **QueryCounters** muss die einzige Option in der Befehlszeile sein.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>Parameter  
 Keine  
  
## <a name="remarks"></a>Anmerkungen  
 Wenn Sie die Instrumentierungsmethode verwenden, kann der Profiler die Werte von mindestens einem CPU-Leistungsindikator für jedes Datensammlungsereignis erfassen. Wenn Sie die Sampling-Profilerstellungsmethode verwenden, können Sie ein Indikatorereignis angeben und festlegen, wie oft ein Ereignis auftreten muss. Mithilfe dieser Angaben wird das Samplingintervall festgelegt.  
  
 Prozessoren, die sich voneinander unterscheiden, stellen auch verschiedene CPU-Leistungsindikatoren zur Verfügung. Der Profiler definiert mehrere generische Indikatoren, die für beinahe alle Prozessoren verwendet werden können. Die Option **QueryCounters** listet sowohl die Namen der generischen Indikatoren als auch die für den Prozessor spezifischen Indikatoren auf.  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Erstellen von Dienstprofilen](../profiling/command-line-profiling-of-services.md)
