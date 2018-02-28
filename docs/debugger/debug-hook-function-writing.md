---
title: Schreiben von Hookfunktionen Debuggen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b5071e2fd7c8114cb13697eef4a4ddfa32d95718
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="debug-hook-function-writing"></a>Schreiben von Hookfunktionen zum Debuggen
In diesem Abschnitt wird eine Reihe von benutzerdefinierten Hookfunktionen zum Debuggen beschrieben, mit denen Code an vordefinierten Punkten in die normalen Verarbeitungsschritte des Debuggers eingefügt werden kann.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Hookfunktionen für Clientblöcke](../debugger/client-block-hook-functions.md)  
 Enthält Anweisungen sowie einen Prototyp für das Schreiben von Funktionen, mit denen der Inhalt der Daten, die in _CLIENT_BLOCK-Blöcken gespeichert werden, überprüft oder dokumentiert wird.  
  
 [Hookfunktionen für Reservierungen](../debugger/allocation-hook-functions.md)  
 Enthält eine Beschreibung einer Reservierungshookfunktion und deren unterschiedlichen Verwendungen, Hinweise auf Beschränkungen sowie einen Prototyp.  
  
 [Reservierungshooks und CRT-Speicherbelegungen](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 In diesem Abschnitt wird die für Reservierungshookfunktionen anwendbare Beschränkung beschrieben, nach der `_CRT_BLOCK`-Blöcke explizit ignoriert werden, wenn sie C-Laufzeitbibliotheksfunktionen aufrufen, durch die interner Speicher belegt wird. Dieses Thema enthält auch die Konsequenzen, wenn Reservierungshook nicht ignoriert `_CRT_BLOCK` Blöcke (mit Beispielen) und wie Sie die standardzuordnung ändern die Hookfunktion, **CrtDefaultAllocHook**.  
  
 [Berichtshookfunktionen](../debugger/report-hook-functions.md)  
 Hier wird die `_CrtSetReportHook`-Funktion beschrieben, mit der Sie Berichte nach bestimmten Reservierungstypen filtern können. In diesem Thema finden Sie außerdem einen Prototyp.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [CRT-Debugverfahren](../debugger/crt-debugging-techniques.md)  
 Enthält Links zu Debugtechniken für die C-Laufzeitbibliothek, darunter Verwenden der CRT-Debugbibliothek, Makros für die Berichterstellung, Unterschiede zwischen `malloc` und `_malloc_dbg`, Schreiben von Hookfunktionen für das Debuggen und CRT-Debugheap.