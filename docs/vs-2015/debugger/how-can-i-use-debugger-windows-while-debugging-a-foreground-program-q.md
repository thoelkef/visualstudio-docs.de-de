---
title: Wie werden Debuggerfenster beim Debuggen eines im Vordergrund ausgeführten Programms verwendet? | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.background
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- foreground program debugging
- remote debugging, debugging foreground programs
- debugging [Visual Studio], while observing foreground programs
- focus, debugging while observing foreground programs
- debugging [Visual Studio], foreground programs
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 296cb0da8615e07c4f7cb22e76b81d6819a8f816
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286506"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Wie werden Debuggerfenster beim Debuggen eines im Vordergrund ausgeführten Programms verwendet?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Problembeschreibung  
 Es liegt ein Problem beim Zeichnen auf dem Bildschirm vor. Um das Problem beobachten zu können, muss das Programm im Vordergrund bleiben; das bedeutet jedoch, dass kein Zugriff auf die Debuggerfenster möglich wäre. Welche Möglichkeiten gibt es?  
  
## <a name="solution"></a>Lösung  
 Wenn Sie über einen zweiten Computer verfügen, können Sie das Remotedebuggen verwenden. So können Sie das Zeichnen auf dem Bildschirm auf dem Remotecomputer beobachten und gleichzeitig den Debugger auf dem Host ausführen. Weitere Informationen zum Remotedebuggen finden Sie unter [Einrichten des Remotedebuggens](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von nativem Code häufig gestellte Fragen](../debugger/debugging-native-code-faqs.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)



