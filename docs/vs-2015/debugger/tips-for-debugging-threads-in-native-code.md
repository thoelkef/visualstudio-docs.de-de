---
title: Tipps zum Debuggen von Threads in nativem Code | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4a0a72f9846add13f2f57581a0b836a9f57f8150
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946911"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Tipps zum Debuggen von Threads in systemeigenem Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im Folgenden finden Sie einige Tipps, die beim Debuggen von Threads in systemeigenem Code hilfreich sein können:  
  
-   Sie können den Inhalt des Threadinformationsblocks anzeigen, indem Sie `@TIB` im **Überwachungsfenster** oder im Dialogfeld **Schnellüberwachung** eingeben.  
  
-   Sie können den letzten Fehlercode für den aktuellen Thread anzeigen, indem Sie `@Err` im **Überwachungsfenster** oder im Dialogfeld **Schnellüberwachung** eingeben.  
  
-   Funktionen der C-Laufzeitbibliotheken (CRT) können hilfreich beim Debuggen von Multithreadanwendungen sein. Weitere Informationen finden Sie unter [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)
