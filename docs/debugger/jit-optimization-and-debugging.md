---
title: "JIT-Optimierung und -Debuggen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen [Visual Studio], Optimierter Code"
  - "Optimierter Code, Debuggen"
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# JIT-Optimierung und -Debuggen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim Debuggen einer verwalteten Anwendung wird die Optimierung des Just\-In\-Time \(JIT\)\-Codes von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] standardmäßig unterdrückt.  Die Unterdrückung der JIT\-Optimierung hat daher zur Folge, dass Sie nicht optimierten Code debuggen.  Der Code wird etwas langsamer ausgeführt, da er nicht optimiert ist. Das Debuggen ist dafür jedoch weitaus gründlicher.  Das Debuggen von optimiertem Code ist schwieriger und wird nur für den Fall empfohlen, dass Sie im optimierten Code auf einen Fehler stoßen, der sich in der nicht optimierten Version nicht reproduzieren lässt.  
  
 Die JIT\-Optimierung wird in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] durch die Option **JIT\-Optimierung beim Laden von Modulen unterdrücken** gesteuert.  Diese Option finden Sie im Dialogfeld **Optionen** auf der Seite **Allgemein** unter dem Knoten **Debuggen**.  
  
 Wenn Sie die Option **JIT\-Optimierung beim Laden von Modulen unterdrücken** deaktivieren, können Sie optimierten JIT\-Code debuggen. Ihre Möglichkeiten beim Debuggen sind jedoch unter Umständen eingeschränkt, da der optimierte Code nicht mit dem Quellcode übereinstimmt.  Daraus ergibt sich, dass Debuggerfenster, z. B. **Lokal** und **Auto**, möglicherweise nicht so viele Informationen anzeigen, wie sie im Vergleich dazu beim Debuggen von nicht optimiertem Code anzeigen würden.  
  
 Ein weiterer wichtiger Unterschied betrifft das Debuggen mit Nur mein Code.  Wenn Sie mit der Option Nur mein Code debuggen, wird optimierter Code vom Debugger als Nichtbenutzercode angesehen, der beim Debuggen nicht angezeigt wird.  Daher sollten Sie beim Debuggen von optimiertem JIT\-Code in Betracht ziehen, die Option Nur mein Code zu deaktivieren.  Weitere Informationen finden Sie unter [Schrittweises Durchlaufen für "Nur mein Code" beschränken](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).  
  
 Beachten Sie, dass durch die Option **JIT\-Optimierung beim Laden von Modulen unterdrücken** die Optimierung von Code unterdrückt wird, wenn Module geladen sind.  Wenn Sie den Debugger an einen Prozess anhängen, der bereits ausgeführt wird, kann dieser Prozess Code enthalten, der bereits geladen, JIT\-kompiliert und optimiert ist.  Die Option **JIT\-Optimierung beim Laden von Modulen unterdrücken** hat auf solchen Code keine Auswirkung, wirkt sich aber auf Module aus, die nach dem Anhängen geladen werden.  Darüber hinaus bleiben mit NGEN erstellte Module \(z. B. WinForms.dll\) von der Option **JIT\-Optimierung beim Laden von Modulen unterdrücken** unberührt.  
  
## Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md)   
 [Anhängen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Der verwaltete Ausführungsprozess](../Topic/Managed%20Execution%20Process.md)