---
title: JIT-Optimierung und-Debuggen | Microsoft-Dokumentation
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
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e798d44371f04b955db9019c741100ce9e5e5ef6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201979"
---
# <a name="jit-optimization-and-debugging"></a>JIT-Optimierung und -Debuggen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Debuggen einer verwalteten Anwendung [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Optimierung von just-in-Time (JIT)-Code standardmäßig unterdrückt. Die Unterdrückung der JIT-Optimierung hat daher zur Folge, dass Sie nicht optimierten Code debuggen. Der Code wird etwas langsamer ausgeführt, da er nicht optimiert ist. Das Debuggen ist dafür jedoch weitaus gründlicher. Das Debuggen von optimiertem Code ist schwieriger und wird nur für den Fall empfohlen, dass Sie im optimierten Code auf einen Fehler stoßen, der sich in der nicht optimierten Version nicht reproduzieren lässt.  
  
 JIT-Optimierung wird gesteuert, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] durch die **unterdrücken JIT-Optimierung beim Laden von Modulen** Option. Finden Sie diese Option auf der **allgemeine** Seite die **Debuggen** Knoten in der **Optionen** Dialogfeld.  
  
 Wenn Sie das Kontrollkästchen der **unterdrücken JIT-Optimierung beim Laden von Modulen** auswählen, können Sie optimierten JIT-Code Debuggen, aber die Möglichkeiten zum Debuggen möglicherweise beschränkt, da der optimierte Code nicht den Quellcode übereinstimmt. Daher Debuggerfenster wie z. B. die **"lokal"** und **"Auto"** Fenster möglicherweise nicht so viele Informationen, als wären Sie nicht optimierten Code Debuggen wurden angezeigt.  
  
 Ein weiterer wichtiger Unterschied betrifft das Debuggen mit Nur mein Code. Wenn Sie mit der Option Nur mein Code debuggen, wird optimierter Code vom Debugger als Nichtbenutzercode angesehen, der beim Debuggen nicht angezeigt wird. Daher sollten Sie beim Debuggen von optimiertem JIT-Code in Betracht ziehen, die Option Nur mein Code zu deaktivieren. Weitere Informationen finden Sie unter [schrittweises Durchlaufen, um nur eigenen Code beschränken](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code).  
  
 Beachten Sie, dass die **unterdrücken JIT-Optimierung beim Laden von Modulen** Option Optimierung von Code unterdrückt, wenn Module geladen sind. Wenn Sie den Debugger an einen Prozess anhängen, der bereits ausgeführt wird, kann dieser Prozess Code enthalten, der bereits geladen, JIT-kompiliert und optimiert ist. Die **unterdrücken JIT-Optimierung beim Laden von Modulen** Option wirkt sich nicht auf diese Art von Code, auch wenn es Module gelten, die nach dem Anhängen geladen werden. Darüber hinaus die **unterdrücken JIT-Optimierung beim Laden von Modulen** Option wirkt sich nicht auf die Module, wie z. B. WinForms.dll, die mit NGEN erstellt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md)   
 [Fügen an laufende Prozesse an](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Der verwaltete Ausführungsprozess](http://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)



