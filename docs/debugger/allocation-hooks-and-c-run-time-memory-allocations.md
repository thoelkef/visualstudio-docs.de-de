---
title: Reservierungshooks und Speicherbelegungen für C Run-Time | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 932beab91e5f98023196e3feff2dec11e6a8b179
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Reservierungshooks und Speicherreservierungen von C-Laufzeitbibliotheken
Eine äußerst wichtige Einschränkung für Reservierungshookfunktionen besteht darin, dass `_CRT_BLOCK`-Blöcke (die von C-Laufzeitbibliotheken intern vorgenommenen Speicherbelegungen) ignoriert werden müssen, falls Aufrufe an C-Bibliotheksfunktionen gesendet werden, durch die interner Speicher belegt wird. Die `_CRT_BLOCK`-Blöcke können ignoriert werden, wenn Sie am Anfang der Reservierungshookfunktion z. B. folgenden Code einfügen:  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Werden `_CRT_BLOCK`-Blöcke nicht vom Reservierungshook ignoriert, kann es vorkommen, dass eine im Hook aufgerufene C-Laufzeitbibliotheksfunktion das Programm in eine Endlosschleife führt. Beispielsweise nimmt `printf` eine interne Reservierung vor. Wenn Hookcode aufruft `printf`, und klicken Sie dann die daraus resultierende Reservierung Hook erneut aufgerufen werden bewirkt aufgerufen wird **Printf** erneut, und so weiter bis ein Stapelüberlauf auftritt. Wenn Sie `_CRT_BLOCK`-Reservierungsoperationen in einem Bericht ausgeben möchten, können Sie diese Beschränkung umgehen, indem Sie für die Formatierung und die Ausgabe anstelle der C-Laufzeitfunktionen Windows-API-Funktionen verwenden. Da der Heap der C-Laufzeitbibliothek nicht von Windows-APIs verwendet wird, führen sie den Reservierungshook nicht in eine Endlosschleife.  
  
 Wenn Sie die Quelldateien der Laufzeitbibliothek untersuchen, sehen Sie, dass die standardmäßige Reservierungshookfunktion, **CrtDefaultAllocHook** (welche gibt einfach **"true"**), befindet sich in einer separaten Datei selbst, DBGHOOK. C. Wenn Sie möchten die Hookfunktion aufgerufen werden, dies gilt auch für die Zuweisung vorgenommen, durch den Laufzeit-Startcode, die vor der Anwendungsverzeichnis ausgeführt wird **main** -Funktion können Sie durch ein eigenes, statt diese Funktion standardmäßig ersetzen mit [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)   
