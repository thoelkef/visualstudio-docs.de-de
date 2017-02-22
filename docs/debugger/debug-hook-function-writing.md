---
title: "Schreiben von Hookfunktionen zum Debuggen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Debughookfunktionen"
  - "Debuggen [C++], CRT-Debugunterstützung"
  - "Debuggen [CRT], Debughookfunktionen"
  - "Hooks"
  - "Hooks, Debug"
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Schreiben von Hookfunktionen zum Debuggen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Abschnitt wird eine Reihe von benutzerdefinierten Hookfunktionen zum Debuggen beschrieben, mit denen Code an vordefinierten Punkten in die normalen Verarbeitungsschritte des Debuggers eingefügt werden kann.  
  
## In diesem Abschnitt  
 [Hookfunktionen für Clientblöcke](../debugger/client-block-hook-functions.md)  
 Enthält Anweisungen sowie einen Prototyp für das Schreiben von Funktionen, mit denen der Inhalt der Daten, die in \_CLIENT\_BLOCK\-Blöcken gespeichert werden, überprüft oder dokumentiert wird.  
  
 [Hookfunktionen für Reservierungen](../debugger/allocation-hook-functions.md)  
 Enthält eine Beschreibung einer Reservierungshookfunktion und deren unterschiedlichen Verwendungen, Hinweise auf Beschränkungen sowie einen Prototyp.  
  
 [Reservierungshooks und CRT\-Speicherbelegungen](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 In diesem Abschnitt wird die für Reservierungshookfunktionen anwendbare Beschränkung beschrieben, nach der `_CRT_BLOCK`\-Blöcke explizit ignoriert werden, wenn sie C\-Laufzeitbibliotheksfunktionen aufrufen, durch die interner Speicher belegt wird.  Hier wird außerdem beschrieben, welche Konsequenzen es hat, wenn der Reservierungshook `_CRT_BLOCK`\-Blöcke nichtignoriert \(einschließlich Beispielen\), und wie Sie die standardmäßige **CrtDefaultAllocHook**\-Reservierungshookfunktion ändern.  
  
 [Hookfunktionen für Berichte](../debugger/report-hook-functions.md)  
 Hier wird die `_CrtSetReportHook`\-Funktion beschrieben, mit der Sie Berichte nach bestimmten Reservierungstypen filtern können.  In diesem Thema finden Sie außerdem einen Prototyp.  
  
## Verwandte Abschnitte  
 [CRT\-Debugverfahren](../debugger/crt-debugging-techniques.md)  
 Enthält Links zu Debugtechniken für die C\-Laufzeitbibliothek, darunter Verwenden der CRT\-Debugbibliothek, Makros für die Berichterstellung, Unterschiede zwischen `malloc` und `_malloc_dbg`, Schreiben von Hookfunktionen für das Debuggen und CRT\-Debugheap.