---
title: "DebugBreak und &quot;_debugbreak&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DebugBreak"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Haltepunkte, DebugBreak-Funktion"
  - "DebugBreak-Funktion"
  - "Debuggen [C++], DebugBreak-Funktion"
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# DebugBreak und &quot;_debugbreak&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Win32\-Funktion "DebugBreak" oder die systeminterne Funktion [\_\_debugbreak](/visual-cpp/intrinsics/debugbreak) kann an einer beliebigen Stelle im Code aufgerufen werden.  `DebugBreak` und `__debugbreak` haben dieselben Auswirkungen wie das Festlegen eines Haltepunkts an dieser Stelle.  
  
 Da durch `DebugBreak` eine Systemfunktion aufgerufen wird, müssen Systemdebugsymbole installiert werden, um sicherzustellen, dass nach dem Abbrechen die richtigen Aufruflisteninformationen angezeigt werden.  Andernfalls sind die vom Debugger angezeigten Aufruflisteninformationen möglicherweise um einen Rahmen verschoben sind.  Wenn Sie `__debugbreak` verwenden, sind keine Symbole erforderlich.  
  
## Siehe auch  
 [Intrinsische Compilerfunktionen](/visual-cpp/intrinsics/compiler-intrinsics)   
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debuggen von systemeigenem Code](../debugger/debugging-native-code.md)   
 [Angeben von Symbol\(PDB\)\- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)