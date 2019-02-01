---
title: Tipps zum Debuggen von Threads in nativem Code | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 363e42700188c931c8be84d456a21112142925c8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54968843"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Tipps zum Debuggen von Threads in nativem Code
Im Folgenden finden Sie einige Tipps, die beim Debuggen von Threads in nativem Code hilfreich sein können:  
  
-   Sie können den Inhalt des Threadinformationsblocks anzeigen, indem Sie `@TIB` im **Überwachungsfenster** oder im Dialogfeld **Schnellüberwachung** eingeben.  
  
-   Sie können den letzten Fehlercode für den aktuellen Thread anzeigen, indem Sie `@Err` im **Überwachungsfenster** oder im Dialogfeld **Schnellüberwachung** eingeben.  
  
-   Funktionen der C-Laufzeitbibliotheken (CRT) können hilfreich beim Debuggen von Multithreadanwendungen sein. Weitere Informationen finden Sie unter [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)