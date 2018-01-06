---
title: Tipps zum Debuggen von Threads in systemeigenem Code | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fef2f2ab6ad1daf3b24adcda193dce5a3ce3ab17
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Tipps zum Debuggen von Threads in nativem Code
Im Folgenden finden Sie einige Tipps, die beim Debuggen von Threads in nativem Code hilfreich sein können:  
  
-   Sie können den Inhalt des Blocks Informationen Thread anzeigen, indem Sie Folgendes eingeben `@TIB` in der **Überwachen** Fenster oder **Schnellüberwachung** (Dialogfeld).  
  
-   Sie können den letzten Fehlercode für den aktuellen Thread anzeigen, indem Sie eingeben `@Err` in der **Überwachen** Fenster oder **Schnellüberwachung** (Dialogfeld).  
  
-   Funktionen der C-Laufzeitbibliotheken (CRT) können hilfreich beim Debuggen von Multithreadanwendungen sein. Weitere Informationen finden Sie unter [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)