---
title: Tipps zum Debuggen von Threads in nativem Code | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06e8690583794c23ce95fb52ef6cab3ab6667afe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184924"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Tipps zum Debuggen von Threads in nativem Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im Folgenden finden Sie einige Tipps, die beim Debuggen von Threads in nativem Code hilfreich sein können:  
  
-   Sie können den Inhalt des Blocks Thread Informationen anzeigen, indem Sie die Eingabe `@TIB` in der **Watch** Fenster oder **Schnellüberwachung** im Dialogfeld.  
  
-   Sie können den letzten Fehlercode für den aktuellen Thread anzeigen, indem Sie eingeben `@Err` in die **Watch** Fenster oder **Schnellüberwachung** Dialogfeld.  
  
-   Funktionen der C-Laufzeitbibliotheken (CRT) können hilfreich beim Debuggen von Multithreadanwendungen sein. Weitere Informationen finden Sie unter [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)



