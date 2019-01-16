---
title: Reservierungshooks und Speicherreservierungen von C-Laufzeit | Microsoft-Dokumentation
ms.date: 11/04/2016
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
ms.openlocfilehash: a654c2d86ed0eb598a963b56cd6e3ef16ad91f19
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154094"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Reservierungshooks und Speicherreservierungen von C-Laufzeitbibliotheken
Eine äußerst wichtige Einschränkung für Reservierungshookfunktionen ist, dass sie explizit ignoriert werden `_CRT_BLOCK` Blöcke. Diese Blöcke sind, die intern vorgenommenen speicherbelegungen von C-Laufzeitbibliotheksfunktionen, wenn sie alle Aufrufe von Funktionen der C-Laufzeitbibliothek ausmachen, die interner Speicher belegt wird. Sie können ignorieren `_CRT_BLOCK` Blöcke dazu den folgenden Code am Anfang Ihrer Zuweisung die Hookfunktion:  
  
```cpp
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Wenn der Reservierungshook ignoriert nicht `_CRT_BLOCK` blockiert wird, und klicken Sie dann alle im Hook aufgerufene C-Laufzeitbibliothek-Funktion, die Anwendung in einer Endlosschleife Auffangen kann. Beispielsweise nimmt `printf` eine interne Reservierung vor. Wenn durch den Hookcode `printf` aufgerufen wird, bewirkt die daraus resultierende Zuweisung, dass der Hook erneut aufgerufen wird, wodurch wiederum **printf** aufgerufen wird usw., bis ein Stapelüberlauf auftritt. Wenn Sie `_CRT_BLOCK`-Reservierungsoperationen in einem Bericht ausgeben möchten, können Sie diese Beschränkung umgehen, indem Sie für die Formatierung und die Ausgabe anstelle der C-Laufzeitfunktionen Windows-API-Funktionen verwenden. Da die Windows-APIs den C-Laufzeitbibliothek Heap nicht verwenden, werden sie nicht der Reservierungshook in einer Endlosschleife überfüllt.  
  
 Wenn Sie die Quelldateien der Laufzeitbibliothek untersuchen, werden Sie feststellen, dass sich die standardmäßige Zuweisungshookfunktion **CrtDefaultAllocHook** (die einfach **TRUE** zurückgibt) in einer separaten Datei namens „DBGHOOK.C“ befindet. Wenn der Zuweisungshook auch für die Zuweisungen aufgerufen werden soll, die vom Laufzeitstartcode vorgenommen wurden, der vor der **main**-Funktion der Anwendung ausgeführt wird, können Sie diese Standardfunktion durch eine eigene Funktion ersetzen, anstatt [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) zu verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)   
