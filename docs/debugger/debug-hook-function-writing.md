---
title: Schreiben von Hookfunktionen zum Debuggen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82145d39adc519bfd1324cc36805cea7b97b1664
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62563372"
---
# <a name="debug-hook-function-writing"></a>Schreiben von Hookfunktionen zum Debuggen
In diesem Abschnitt wird eine Reihe von benutzerdefinierten Hookfunktionen zum Debuggen beschrieben, mit denen Code an vordefinierten Punkten in die normalen Verarbeitungsschritte des Debuggers eingefügt werden kann.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Clientblöcke](../debugger/client-block-hook-functions.md) bietet Anweisungen sowie einen Prototyp für das Schreiben von Funktionen, die überprüfen, oder melden den Inhalt der Daten, die in _CLIENT_BLOCK-Blöcken gespeichert.

 [Hookfunktionen](../debugger/allocation-hook-functions.md) eine Reservierungshookfunktion definiert, deren unterschiedlichen Verwendungen, betont, Einschränkungen und stellt einen Prototyp.

 [Reservierungshooks und CRT-Speicherbelegungen](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) beschreibt die Einschränkung für Reservierungshookfunktionen explizit ignoriert `_CRT_BLOCK` blockiert, wenn sie C-Laufzeitbibliotheksfunktionen aufrufen, die interner Speicher belegt. Hier wird außerdem beschrieben, welche Konsequenzen es hat, wenn der Zuweisungshook `_CRT_BLOCK`-Blöcke nicht ignoriert (einschließlich Beispielen), und wie Sie die standardmäßige Zuweisungshookfunktion **CrtDefaultAllocHook** ändern.

 [Melden Sie Hook Functions](../debugger/report-hook-functions.md) erläutert `_CrtSetReportHook`, die Sie verwenden können, zum Filtern von Berichten in bestimmte Typen von Zuordnungen zu konzentrieren. In diesem Thema finden Sie außerdem einen Prototyp.

## <a name="related-sections"></a>Verwandte Abschnitte

- [CRT-Debugverfahren](../debugger/crt-debugging-techniques.md) – enthält Links zu Debugtechniken für die C-Laufzeitbibliothek, einschließlich der Verwendung der CRT-Debugbibliothek, Makros für die berichterstellung, Unterschiede zwischen `malloc` und `_malloc_dbg`, Schreiben von Hookfunktionen und der CRT -Debugheap.