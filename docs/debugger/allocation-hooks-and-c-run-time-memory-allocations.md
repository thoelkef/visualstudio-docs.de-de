---
title: "Reservierungshooks und Speicherreservierungen von C-Laufzeitbibliotheken | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Reservierungshooks"
  - "Debuggen [C++], Hookfunktionen"
  - "Hooks, Reservierung"
  - "Speicherreservierung, Problembehandlung bei Reservierungshooks"
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Reservierungshooks und Speicherreservierungen von C-Laufzeitbibliotheken
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine äußerst wichtige Einschränkung für Reservierungshookfunktionen besteht darin, dass `_CRT_BLOCK`\-Blöcke \(die von C\-Laufzeitbibliotheken intern vorgenommenen Speicherbelegungen\) ignoriert werden müssen, falls Aufrufe an C\-Bibliotheksfunktionen gesendet werden, durch die interner Speicher belegt wird.  Die `_CRT_BLOCK`\-Blöcke können ignoriert werden, wenn Sie am Anfang der Reservierungshookfunktion z. B. folgenden Code einfügen:  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Werden `_CRT_BLOCK`\-Blöcke nicht vom Reservierungshook ignoriert, kann es vorkommen, dass eine im Hook aufgerufene C\-Laufzeitbibliotheksfunktion das Programm in eine Endlosschleife führt.  Beispielsweise nimmt `printf` eine interne Reservierung vor.  Wenn durch den Hookcode `printf` aufgerufen wird, bewirkt die daraus resultierende Reservierung, dass der Hook erneut aufgerufen wird, wodurch wiederum  aufgerufen wird usw., bis ein Stapelüberlauf auftritt.  Wenn Sie `_CRT_BLOCK`\-Reservierungsoperationen in einem Bericht ausgeben möchten, können Sie diese Beschränkung umgehen, indem Sie für die Formatierung und die Ausgabe anstelle der C\-Laufzeitfunktionen Windows\-API\-Funktionen verwenden.  Da der Heap der C\-Laufzeitbibliothek nicht von Windows\-APIs verwendet wird, führen sie den Reservierungshook nicht in eine Endlosschleife.  
  
 Wenn Sie die Quelldateien der Laufzeitbibliothek untersuchen, werden Sie feststellen, dass sich die standardmäßige Reservierungshookfunktion **CrtDefaultAllocHook** \(die einfach **TRUE** zurückgibt\) in einer separaten Datei namens DBGHOOK.C befindet.  Wenn der Reservierungshook auch für die Zuordnungen aufgerufen werden soll, die vom Laufzeitstartcode vorgenommen wurden, der vor der **main**\-Funktion der Anwendung ausgeführt wird, können Sie diese Standardfunktion durch eine eigene Funktion ersetzen, anstatt [\_CrtSetAllocHook](/visual-cpp/c-runtime-library/reference/crtsetallochook) zu verwenden.  
  
## Siehe auch  
 [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/de-de/21e1346a-6a17-4f57-b275-c76813089167)