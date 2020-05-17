---
title: Verwenden von Debuggerfenstern beim Debuggen einer im Vordergrund ausgeführten App | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.background
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- foreground program debugging
- remote debugging, debugging foreground programs
- debugging [Visual Studio], while observing foreground programs
- focus, debugging while observing foreground programs
- debugging [Visual Studio], foreground programs
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 759d9a6a3beb55bf72a0f41a93cb26c8c15b0c5e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734053"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Wie werden Debuggerfenster beim Debuggen eines im Vordergrund ausgeführten Programms verwendet?
## <a name="problem-description"></a>Problembeschreibung
 Es liegt ein Problem beim Zeichnen auf dem Bildschirm vor. Um das Problem beobachten zu können, muss das Programm im Vordergrund bleiben; das bedeutet jedoch, dass kein Zugriff auf die Debuggerfenster möglich wäre. Welche Möglichkeiten gibt es?

## <a name="solution"></a>Lösung
 Wenn Sie über einen zweiten Computer verfügen, können Sie das Remotedebuggen verwenden. So können Sie das Zeichnen auf dem Bildschirm auf dem Remotecomputer beobachten und gleichzeitig den Debugger auf dem Host ausführen. Weitere Informationen zum Remotedebuggen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

## <a name="see-also"></a>Siehe auch
- [FAQs zum Debuggen von nativem Code](../debugger/debugging-native-code-faqs.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)