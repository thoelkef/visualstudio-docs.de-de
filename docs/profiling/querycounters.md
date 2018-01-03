---
title: QueryCounters | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9a05fbb94d818868dbd13ae1c7f1b0c64d68b749
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="querycounters"></a>QueryCounters
Die Option **QueryCounters** listet die CPU-Leistungsindikatoren (Hardware) auf, die auf dem Computer verfügbar sind.  
  
 **QueryCounters** muss die einzige Option in der Befehlszeile sein.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>Parameter  
 Keiner  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie die Instrumentierungsmethode verwenden, kann der Profiler die Werte von mindestens einem CPU-Leistungsindikator für jedes Datensammlungsereignis erfassen. Wenn Sie die Sampling-Profilerstellungsmethode verwenden, können Sie ein Indikatorereignis angeben und festlegen, wie oft ein Ereignis auftreten muss. Mithilfe dieser Angaben wird das Samplingintervall festgelegt.  
  
 Prozessoren, die sich voneinander unterscheiden, stellen auch verschiedene CPU-Leistungsindikatoren zur Verfügung. Der Profiler definiert mehrere generische Indikatoren, die für beinahe alle Prozessoren verwendet werden können. Die Option **QueryCounters** listet sowohl die Namen der generischen Indikatoren als auch die für den Prozessor spezifischen Indikatoren auf.  
  
## <a name="see-also"></a>Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Erstellen von Dienstprofilen](../profiling/command-line-profiling-of-services.md)