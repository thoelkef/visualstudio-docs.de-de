---
title: Schreiben von Hookfunktionen zum Debuggen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5761b0a32e7739a5611f2d3d07183f0c529fc60c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524721"
---
# <a name="debug-hook-function-writing"></a>Schreiben von Hookfunktionen zum Debuggen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Debug Hook-Funktion schreiben](https://docs.microsoft.com/visualstudio/debugger/debug-hook-function-writing).  
  
In diesem Abschnitt wird eine Reihe von benutzerdefinierten Hookfunktionen zum Debuggen beschrieben, mit denen Code an vordefinierten Punkten in die normalen Verarbeitungsschritte des Debuggers eingefügt werden kann.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Hookfunktionen für Clientblöcke](../debugger/client-block-hook-functions.md)  
 Enthält Anweisungen sowie einen Prototyp für das Schreiben von Funktionen, mit denen der Inhalt der Daten, die in _CLIENT_BLOCK-Blöcken gespeichert werden, überprüft oder dokumentiert wird.  
  
 [Hookfunktionen für Reservierungen](../debugger/allocation-hook-functions.md)  
 Enthält eine Beschreibung einer Reservierungshookfunktion und deren unterschiedlichen Verwendungen, Hinweise auf Beschränkungen sowie einen Prototyp.  
  
 [Reservierungshooks und CRT-Speicherbelegungen](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 In diesem Abschnitt wird die für Reservierungshookfunktionen anwendbare Beschränkung beschrieben, nach der `_CRT_BLOCK`-Blöcke explizit ignoriert werden, wenn sie C-Laufzeitbibliotheksfunktionen aufrufen, durch die interner Speicher belegt wird. Dieses Thema enthält auch die Konsequenzen, wenn der Reservierungshook nicht ignoriert wird `_CRT_BLOCK` Blöcke (einschließlich Beispielen) und ändern Sie die standardzuweisung Reservierungshookfunktion **CrtDefaultAllocHook**.  
  
 [Berichtshookfunktionen](../debugger/report-hook-functions.md)  
 Hier wird die `_CrtSetReportHook`-Funktion beschrieben, mit der Sie Berichte nach bestimmten Reservierungstypen filtern können. In diesem Thema finden Sie außerdem einen Prototyp.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [CRT-Debugverfahren](../debugger/crt-debugging-techniques.md)  
 Enthält Links zu Debugtechniken für die C-Laufzeitbibliothek, darunter Verwenden der CRT-Debugbibliothek, Makros für die Berichterstellung, Unterschiede zwischen `malloc` und `_malloc_dbg`, Schreiben von Hookfunktionen für das Debuggen und CRT-Debugheap.



