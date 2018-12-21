---
title: Mithilfe der Debuggerfenster beim Debuggen einer Vordergrund-app | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6497a2a21c85e7889b3b6538dace0f8c22f24944
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063767"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Wie werden Debuggerfenster beim Debuggen eines im Vordergrund ausgeführten Programms verwendet?
## <a name="problem-description"></a>Problembeschreibung  
 Es liegt ein Problem beim Zeichnen auf dem Bildschirm vor. Um das Problem beobachten zu können, muss das Programm im Vordergrund bleiben; das bedeutet jedoch, dass kein Zugriff auf die Debuggerfenster möglich wäre. Welche Möglichkeiten gibt es?  
  
## <a name="solution"></a>Lösung  
 Wenn Sie über einen zweiten Computer verfügen, können Sie das Remotedebuggen verwenden. So können Sie das Zeichnen auf dem Bildschirm auf dem Remotecomputer beobachten und gleichzeitig den Debugger auf dem Host ausführen. Weitere Informationen zum Remotedebuggen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debugging Native Code FAQs (Häufig gestellte Fragen zum Debuggen von nativem Code)](../debugger/debugging-native-code-faqs.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)