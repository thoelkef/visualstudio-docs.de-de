---
title: Reservierungshooks und Speicherreservierungen von C-Laufzeit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22856782fb8d0ad92a19f03c7c3a474763310a60
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273714"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Reservierungshooks und Speicherreservierungen von C-Laufzeitbibliotheken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine äußerst wichtige Einschränkung für Reservierungshookfunktionen besteht darin, dass `_CRT_BLOCK`-Blöcke (die von C-Laufzeitbibliotheken intern vorgenommenen Speicherbelegungen) ignoriert werden müssen, falls Aufrufe an C-Bibliotheksfunktionen gesendet werden, durch die interner Speicher belegt wird. Die `_CRT_BLOCK`-Blöcke können ignoriert werden, wenn Sie am Anfang der Reservierungshookfunktion z. B. folgenden Code einfügen:  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Werden `_CRT_BLOCK`-Blöcke nicht vom Reservierungshook ignoriert, kann es vorkommen, dass eine im Hook aufgerufene C-Laufzeitbibliotheksfunktion das Programm in eine Endlosschleife führt. Beispielsweise nimmt `printf` eine interne Reservierung vor. Wenn Sie den Hookcode `printf`, und klicken Sie dann die daraus resultierende Reservierung der Hook erneut aufgerufen wird wiederum führt **Printf** erneut aus, und so weiter bis ein Stapelüberlauf auftritt. Wenn Sie `_CRT_BLOCK`-Reservierungsoperationen in einem Bericht ausgeben möchten, können Sie diese Beschränkung umgehen, indem Sie für die Formatierung und die Ausgabe anstelle der C-Laufzeitfunktionen Windows-API-Funktionen verwenden. Da der Heap der C-Laufzeitbibliothek nicht von Windows-APIs verwendet wird, führen sie den Reservierungshook nicht in eine Endlosschleife.  
  
 Wenn Sie die Quelldateien der Laufzeitbibliothek untersuchen, sehen Sie, dass die standardmäßige Reservierungshookfunktion **CrtDefaultAllocHook** (gibt einfach **"true"**), befindet sich in einer separaten Datei mit ihren eigenen DBGHOOK. C. Wenn der Reservierungshook auch für die Zuordnungen, die von der Laufzeit-Startcode, die ausgeführt wird, bevor Sie Ihrer Anwendungsverzeichnis aufgerufen werden soll **main** -Funktion können Sie diese Standardfunktion durch eine eigene, anstelle von ersetzen Mithilfe von [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d).  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2-Beispiel](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



