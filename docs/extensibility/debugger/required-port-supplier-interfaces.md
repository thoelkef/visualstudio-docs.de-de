---
title: "Erforderliche Ports Zulieferer Schnittstellen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Port-Lieferanten, erforderlichen Schnittstellen"
  - "Debuggen [Debugging-SDK], port Lieferanten"
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Erforderliche Ports Zulieferer Schnittstellen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Port lieferant muss die [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)\-Schnittstelle implementieren.       [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Da Zubehör anschlüsse eines Anschlusslieferanten, sie ebenfalls implementieren müssen.  Daher muss er die folgenden Schnittstellen implementieren:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Beschreibt den angegebenen Anschluss und kann alle Prozesse aufgelistet, die auf dem Port ausgeführt werden.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Stellt für das Starten und Beenden von Prozessen auf dem Port bereit.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Stellt einen Mechanismus für Programme, die innerhalb des Kontexts dieses Ports, um es der Knoten Programm und \- zerstörung zu benachrichtigen.  Weitere Informationen finden Sie unter [Programm\-Knoten](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     Stellt einen Verbindungspunkt für [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)bereit.  
  
## Anschluss\-Lieferanten\-Vorgang  
 Die [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) Senke Benachrichtigungen empfängt, wenn Prozess und Programme auf einem Port erstellt und zerstört werden.  Ein Port ist erforderlich, [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) zu senden, wenn ein Prozess und [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) erstellt wird, wenn ein Prozess im Anschluss zerstört wird.  Ein Port ist auch erforderlich, [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) gesendet werden sollen, wenn in einem Programm, und [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) erstellt wird, wenn ein Programm in einem Prozess, der auf dem Port zerstört wird.  
  
 Ein Port wird in der Regel Programm erstellen und zerstören [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) die als Reaktion auf Ereignisse und Methoden [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) .  
  
 Da ein Port starten und physikalische Programme und logische Prozesse beenden kann, müssen diese Schnittstellen durch das Debugmodul ebenfalls implementiert werden:  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     Beschreibt den physischen Prozess.  Mindestens müssen die folgenden Methoden implementiert werden:  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     Stellt eine Methode bereit, mit denen das SDM von einem Prozess anfügt, und trennt.  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     Beschreibt das logische Programm.  Mindestens müssen die folgenden Methoden implementiert werden:  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Stellt eine Methode zum SDM in die Anfügen an diesem Programm bereit.  
  
## Siehe auch  
 [Implementieren einen Port Lieferanten](../../extensibility/debugger/implementing-a-port-supplier.md)