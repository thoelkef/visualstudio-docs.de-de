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
ms.openlocfilehash: 8f76a6ea66396a8c5780731945cad87eab94b8ee
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717597"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Tipps zum Debuggen von Threads in systemeigenem Code
Im Folgenden finden Sie einige Tipps, die beim Debuggen von Threads in systemeigenem Code hilfreich sein können:

-   Sie können den Inhalt des Threadinformationsblocks anzeigen, indem Sie `@TIB` im **Überwachungsfenster** oder im Dialogfeld **Schnellüberwachung** eingeben.

-   Sie können den letzten Fehlercode für den aktuellen Thread anzeigen, indem Sie `@Err` im **Überwachungsfenster** oder im Dialogfeld **Schnellüberwachung** eingeben.

-   Funktionen der C-Laufzeitbibliotheken (CRT) können hilfreich beim Debuggen von Multithreadanwendungen sein. Weitere Informationen finden Sie unter [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).

## <a name="see-also"></a>Siehe auch
- [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)