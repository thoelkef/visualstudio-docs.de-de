---
title: JIT-Optimierung und -Debuggen | Microsoft-Dokumentation
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
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 56b010a01ccd7e40e696653e13dd7c972c97a9cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690537"
---
# <a name="jit-optimization-and-debugging"></a>JIT-Optimierung und -Debuggen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie eine verwaltete Anwendung debuggen, wird die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Optimierung des Just-in-time (JIT)-Codes standardmäßig unterdrückt. Die Unterdrückung der JIT-Optimierung hat daher zur Folge, dass Sie nicht optimierten Code debuggen. Der Code wird etwas langsamer ausgeführt, da er nicht optimiert ist. Das Debuggen ist dafür jedoch weitaus gründlicher. Das Debuggen von optimiertem Code ist schwieriger und wird nur für den Fall empfohlen, dass Sie im optimierten Code auf einen Fehler stoßen, der sich in der nicht optimierten Version nicht reproduzieren lässt.  
  
 Die JIT-Optimierung wird in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] durch die Option **JIT-Optimierung beim Laden von Modulen unterdrücken** gesteuert. Sie finden diese Option auf der Seite **Allgemein** im Dialogfeld **Optionen** unter dem Knoten **Debuggen** .  
  
 Wenn Sie die Option **JIT-Optimierung beim Laden von Modulen unterdrücken** deaktivieren, können Sie optimierten JIT-Code Debuggen, die Möglichkeit zum Debuggen kann jedoch eingeschränkt sein, da der optimierte Code nicht mit dem Quellcode identisch ist. Folglich werden Debuggerfenster **wie das Fenster** "lokal" **und "** Auto" möglicherweise nicht so viele Informationen angezeigt wie beim Debuggen von nicht optimiertem Code.  
  
 Ein weiterer wichtiger Unterschied betrifft das Debuggen mit Nur mein Code. Wenn Sie mit der Option Nur mein Code debuggen, wird optimierter Code vom Debugger als Nichtbenutzercode angesehen, der beim Debuggen nicht angezeigt wird. Daher sollten Sie beim Debuggen von optimiertem JIT-Code in Betracht ziehen, die Option Nur mein Code zu deaktivieren. Weitere Informationen finden Sie unterschritt-für-  [Schritt-nur eigenen Code einschränken](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code).  
  
 Beachten Sie, dass die Option **JIT-Optimierung beim Laden von** Modulen unterdrücken die Optimierung des Codes unterdrückt, wenn Module geladen werden. Wenn Sie den Debugger an einen Prozess anhängen, der bereits ausgeführt wird, kann dieser Prozess Code enthalten, der bereits geladen, JIT-kompiliert und optimiert ist. Die Option **JIT-Optimierung beim Laden von Modulen unterdrücken** hat keine Auswirkungen auf diesen Code, obwohl Sie sich auf Module auswirkt, die nach dem Anfügen von geladen werden. Außerdem wirkt sich die Option **JIT-Optimierung beim Laden von Modulen unterdrücken nicht auf** Module wie WinForms.dll aus, die mit ngen erstellt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugging von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Navigieren durch Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md)   
 [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Der verwaltete Ausführungsprozess](https://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)
