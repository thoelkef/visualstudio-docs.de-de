---
title: "Gewusst wie: RPC-Debuggen von COM-Clients und -Servern | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.com"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "COM-Clients, Debuggen"
  - "COM-Server, Debuggen"
  - "COM, Debuggen"
  - "Debuggen eines Remoteprozeduraufrufs während eines Vorgangs"
  - "Debuggen eines prozessexternen Remoteprozeduraufrufs"
  - "Remotedebuggen, RPC (Remoteprozeduraufrufe)"
  - "RPC (Remoteprozeduraufrufe)"
  - "RPC (Remoteprozeduraufrufe), Debuggen"
  - "RPC (Remoteprozeduraufrufe), Debuggen von COM-Clients und -Servern"
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Gewusst wie: RPC-Debuggen von COM-Clients und -Servern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können RPC\-Debuggen \(Remote Procedure Call, Remoteprozeduraufruf\) verwenden, um COM\-Client\-\/Server\-Anwendungen zu debuggen.  Vor der Verwendung muss RPC\-Debuggen allerdings aktiviert werden.  Bei aktiviertem RPC\-Debuggen wird der Debugger an den Server angefügt, wenn Sie vom Client in den Serveraufruf springen. Der Code kann nun debuggt werden.  Wenn der Debugger angefügt wurde, können alle Debuggerfeatures sowohl für Client\- als auch für Serverprozesse verwendet werden.  
  
### So aktivieren Sie RPC\-Debuggen  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Klicken Sie im Dialogfeld **Optionen** auf den Ordner **Debuggen**.  
  
3.  Klicken Sie auf die Seite **Systemeigen**.  
  
4.  Aktivieren Sie das Kontrollkästchen **RPC\-Debuggen**.  
  
    > [!NOTE]
    >  Sie müssen Administrator\- oder Hauptbenutzerrechte besitzen, um Remoteprozeduraufrufe debuggen zu können.  
  
    > [!NOTE]
    >  RPC\-Stepping auf einem Remoteserver, auf dem Microsoft Windows Vista ausgeführt wird, funktioniert nur, wenn ein systemeigener Debugger an den Remoteserver angehängt wird.  Andernfalls schlägt der RPC\-Aufruf ohne eine Fehlermeldung fehl.  Sonst wird der RPC\-Aufruf abgeschlossen, aber der Einzelschritt beim RPC\-Aufruf funktioniert nicht.  
  
## Siehe auch  
 [Debuggen von COM\-Servern und \-Containern](../debugger/com-server-and-container-debugging.md)   
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)