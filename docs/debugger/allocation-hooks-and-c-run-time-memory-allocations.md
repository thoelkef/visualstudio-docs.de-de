---
title: Zuordnungs Hooks und C-Laufzeitspeicher Belegungen | Microsoft-Dokumentation
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79e55ec521de098a7ae0339c4460502dde3d482d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745795"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Reservierungshooks und Speicherreservierungen von C-Laufzeitbibliotheken
Eine sehr wichtige Einschränkung bei Zuordnungs-Hook-Funktionen besteht darin, dass Sie `_CRT_BLOCK` Blöcke explizit ignorieren müssen. Diese Blöcke sind die Speicher Belegungen, die intern durch c-Lauf Zeit Bibliotheksfunktionen erstellt werden, wenn Sie Aufrufe an c-Lauf Zeit Bibliotheksfunktionen durchführen, die internen Arbeitsspeicher zuordnen. Sie können `_CRT_BLOCK` Blöcke ignorieren, indem Sie den folgenden Code am Anfang der Zuordnungs-Hook-Funktion einschließen:

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

Wenn der zuordnungshook `_CRT_BLOCK` Blöcke nicht ignoriert, kann jede C-Lauf Zeit Bibliotheksfunktion, die in Ihrem Hook aufgerufen wird, das Programm in einer Endlosschleife abfangen. Beispielsweise nimmt `printf` eine interne Reservierung vor. Wenn durch den Hookcode `printf` aufgerufen wird, bewirkt die daraus resultierende Zuweisung, dass der Hook erneut aufgerufen wird, wodurch wiederum **printf** aufgerufen wird usw., bis ein Stapelüberlauf auftritt. Wenn Sie `_CRT_BLOCK`-Reservierungsoperationen in einem Bericht ausgeben möchten, können Sie diese Beschränkung umgehen, indem Sie für die Formatierung und die Ausgabe anstelle der C-Laufzeitfunktionen Windows-API-Funktionen verwenden. Da der C-Lauf Zeit Bibliotheks Heap von den Windows-APIs nicht verwendet wird, wird der Zuordnungs Hook nicht in einer Endlosschleife abgefangen.

Wenn Sie die Quelldateien der Laufzeitbibliothek untersuchen, werden Sie feststellen, dass sich die standardmäßige Zuweisungshookfunktion **CrtDefaultAllocHook** (die einfach **TRUE** zurückgibt) in einer separaten Datei namens „DBGHOOK.C“ befindet. Wenn der Zuweisungshook auch für die Zuweisungen aufgerufen werden soll, die vom Laufzeitstartcode vorgenommen wurden, der vor der **main**-Funktion der Anwendung ausgeführt wird, können Sie diese Standardfunktion durch eine eigene Funktion ersetzen, anstatt [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) zu verwenden.

## <a name="see-also"></a>Siehe auch
- [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)
