---
title: Reservierungshooks und Speicherreservierungen von C-Laufzeit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 7e4c631b72ae9b12f77daf2ddd49919651c0b3e5
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433105"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Reservierungshooks und Speicherreservierungen von C-Laufzeitbibliotheken
Eine äußerst wichtige Einschränkung für Reservierungshookfunktionen ist, dass sie explizit ignoriert werden `_CRT_BLOCK` Blöcke. Diese Blöcke sind, die intern vorgenommenen speicherbelegungen von C-Laufzeitbibliotheksfunktionen, wenn sie alle Aufrufe von Funktionen der C-Laufzeitbibliothek ausmachen, die interner Speicher belegt wird. Sie können ignorieren `_CRT_BLOCK` Blöcke durch Einschließen des folgende Codes an den Anfang der Reservierungshookfunktion:  
  
```cpp
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Wenn der Reservierungshook ignoriert nicht `_CRT_BLOCK` blockiert wird, und klicken Sie dann alle im Hook aufgerufene C-Laufzeitbibliothek-Funktion, die Anwendung in einer Endlosschleife Auffangen kann. Beispielsweise nimmt `printf` eine interne Reservierung vor. Wenn Sie den Hookcode `printf`, und klicken Sie dann die daraus resultierende Reservierung der Hook erneut aufgerufen wird wiederum führt **Printf** erneut aus, und so weiter, bis ein Stapelüberlauf auftritt. Wenn Sie `_CRT_BLOCK`-Reservierungsoperationen in einem Bericht ausgeben möchten, können Sie diese Beschränkung umgehen, indem Sie für die Formatierung und die Ausgabe anstelle der C-Laufzeitfunktionen Windows-API-Funktionen verwenden. Da die Windows-APIs den C-Laufzeitbibliothek Heap nicht verwenden, werden sie nicht der Reservierungshook in einer Endlosschleife überfüllt.  
  
 Wenn Sie die Quelldateien der Laufzeitbibliothek untersuchen, sehen Sie, dass die standardmäßige Reservierungshookfunktion **CrtDefaultAllocHook** (gibt einfach **"true"**), befindet sich in einer separaten Datei mit ihren eigenen DBGHOOK. C. Wenn der Reservierungshook auch für die Zuordnungen, die von der Laufzeit-Startcode, die ausgeführt wird, bevor Sie Ihrer Anwendungsverzeichnis aufgerufen werden soll **main** -Funktion können Sie diese Standardfunktion durch eine eigene, anstelle von ersetzen Mithilfe von [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)   
