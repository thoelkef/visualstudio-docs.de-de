---
title: "Tipps zum Debuggen von Threads in systemeigenem Code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen [Visual Studio], Threads"
  - "Threading [Visual Studio], Debuggen"
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Tipps zum Debuggen von Threads in systemeigenem Code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im Folgenden finden Sie einige Tipps, die beim Debuggen von Threads in systemeigenem Code hilfreich sein können:  
  
-   Sie können den Inhalt des Threadinformationsblocks anzeigen, indem Sie im **Überwachungsfenster** oder im Dialogfeld **Schnellüberwachung** `@TIB` eingeben.  
  
-   Sie können den letzten Fehlercode für den aktuellen Thread anzeigen, indem Sie im **Überwachungsfenster** oder im Dialogfeld **Schnellüberwachung** `@Err` eingeben.  
  
-   Funktionen der C\-Laufzeitbibliotheken \(CRT\) können hilfreich beim Debuggen von Multithreadanwendungen sein.  Weitere Informationen finden Sie unter [\_malloc\_dbg](/visual-cpp/c-runtime-library/reference/malloc-dbg).  
  
## Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debuggen von systemeigenem Code](../debugger/debugging-native-code.md)