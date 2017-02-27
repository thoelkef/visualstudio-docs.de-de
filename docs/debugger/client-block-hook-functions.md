---
title: "Hookfunktionen f&#252;r Clientbl&#246;cke | Microsoft Docs"
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
  - "_CrtSetDumpClient-Funktion"
  - "Clientblöcke, Hookfunktionen"
  - "Clientblöcke, Validieren und Berichten von Daten"
  - "Debuggen [C++], Hookfunktionen"
  - "Hooks, Clientblock"
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Hookfunktionen f&#252;r Clientbl&#246;cke
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie die in `_CLIENT_BLOCK`\-Blöcken gespeicherten Daten überprüfen oder als Bericht ausgeben möchten, können Sie speziell für diesen Zweck eine Funktion schreiben.  Der Prototyp dieser Funktion muss etwa wie der folgende, in **CRTDBG.H** definierte Prototyp aussehen:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 Das bedeutet, dass die Hookfunktion einen **void**\-Zeiger auf den Anfang des Reservierungsblocks sowie einen Wert vom Typ **size\_t**, der die Reservierungsgröße angibt, akzeptieren und `void` zurückgeben muss.  Der restliche Inhalt dieser Funktion ist Ihnen freigestellt.  
  
 Nachdem Sie die Hookfunktion mithilfe von [\_CrtSetDumpClient](/visual-cpp/c-runtime-library/reference/crtsetdumpclient) installiert haben, wird sie bei jedem Dump eines `_CLIENT_BLOCK`\-Blocks aufgerufen.  Mithilfe von [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype) können Sie anschließend Informationen zum Typ oder Untertyp der im Dump ausgegebenen Blöcke abrufen.  
  
 Der Zeiger auf die Funktion, den Sie an `_CrtSetDumpClient` übergeben, ist vom Typ **\_CRT\_DUMP\_CLIENT**, wie in **Crtdbg.h** definiert:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## Siehe auch  
 [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/de-de/21e1346a-6a17-4f57-b275-c76813089167)   
 [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype)