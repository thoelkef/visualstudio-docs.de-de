---
title: JIT-Optimierung und-Debuggen | Microsoft Docs
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
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2c3dcd57568bdfaac3ba0f7aff33cefca8a0ee32
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="jit-optimization-and-debugging"></a>JIT-Optimierung und -Debuggen
Beim Debuggen einer verwalteten Anwendung [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Optimierung des Just-in-Time (JIT)-Codes standardmäßig unterdrückt. Die Unterdrückung der JIT-Optimierung hat daher zur Folge, dass Sie nicht optimierten Code debuggen. Der Code wird etwas langsamer ausgeführt, da er nicht optimiert ist. Das Debuggen ist dafür jedoch weitaus gründlicher. Das Debuggen von optimiertem Code ist schwieriger und wird nur für den Fall empfohlen, dass Sie im optimierten Code auf einen Fehler stoßen, der sich in der nicht optimierten Version nicht reproduzieren lässt.  
  
 JIT-Optimierung wird gesteuert, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] durch die **unterdrücken JIT-Optimierung beim Laden von Modulen** Option. Finden Sie diese Option auf der **allgemeine** Seite unter das **Debuggen** Knoten in der **Optionen** (Dialogfeld).  
  
 Wenn Sie das Kontrollkästchen der **unterdrücken JIT-Optimierung beim Laden von Modulen** auswählen, können Sie optimierten JIT-Code Debuggen, jedoch die Fähigkeit zum Debuggen ist möglicherweise beschränkt, da der optimierte Code nicht mit den Quellcode übereinstimmt. Folglich Debuggerfenster wie z. B. die **"lokal"** und **"Auto"** Fenster möglicherweise nicht so viele Informationen, als wären Sie nicht optimierten Code Debuggen wurden angezeigt.  
  
 Ein weiterer wichtiger Unterschied betrifft das Debuggen mit Nur mein Code. Wenn Sie mit der Option Nur mein Code debuggen, wird optimierter Code vom Debugger als Nichtbenutzercode angesehen, der beim Debuggen nicht angezeigt wird. Daher sollten Sie beim Debuggen von optimiertem JIT-Code in Betracht ziehen, die Option Nur mein Code zu deaktivieren. Weitere Informationen finden Sie unter [schrittweises Durchlaufen für nur mein Code beschränken](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).  
  
 Beachten Sie, dass die **unterdrücken JIT-Optimierung beim Laden von Modulen** Option Optimierung von Code unterdrückt, wenn Module geladen sind. Wenn Sie den Debugger an einen Prozess anhängen, der bereits ausgeführt wird, kann dieser Prozess Code enthalten, der bereits geladen, JIT-kompiliert und optimiert ist. Die **unterdrücken JIT-Optimierung beim Laden von Modulen** Option hat keine Auswirkung auf solchen Code, auch wenn es Module auswirkt, die nach dem Anhängen geladen werden. Darüber hinaus die **unterdrücken JIT-Optimierung beim Laden von Modulen** Option wirkt sich nicht auf die Module, wie z. B. WinForms.dll, die mit NGEN erstellt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md)   
 [Fügen an laufende Prozesse an](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Der verwaltete Ausführungsprozess](/dotnet/standard/managed-execution-process)