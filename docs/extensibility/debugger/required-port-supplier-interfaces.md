---
title: Erforderliche Ports Lieferanten Schnittstellen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e34627effce5e2f0d1401da683536548a32d3f6e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="required-port-supplier-interfaces"></a>Erforderliche Port Lieferanten Schnittstellen
Ein Port Lieferant muss implementieren die [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) Schnittstelle.[ IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Da ein Port Lieferant Ports bereitstellt, muss er auch diese implementieren. Aus diesem Grund müssen sie die folgenden Schnittstellen implementieren:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Beschreibt den Port und können alle auf den Port ausgeführten Prozesse auflisten.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Stellt für das Starten und Beenden von Prozessen auf dem Port.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Bietet einen Mechanismus für Programme, die diesen Port Kontext eine Benachrichtigung der Knoten die Erstellung und Zerstörung ausgeführt. Weitere Informationen finden Sie unter [Programm Knoten](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     Stellt einen Verbindungspunkt für [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Lieferanten Portvorgang  
 Die [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) Senke empfängt Benachrichtigungen beim Verarbeiten und Programme erstellt und an einem Port zerstört werden. Ein Port ist erforderlich, um das Senden [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) bei der Erstellung eines Prozesses und [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) Wenn auf dem Port ein Prozesses zerstört wird. Ein Port ist auch erforderlich, um senden [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) Wenn ein Programm erstellt wird und [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) Wenn ein Programm in einem Prozess ausgeführt wird, an dem Port zerstört wird.  
  
 Ein Port in der Regel sendet Programm erstellen und zerstören Ereignisse als Antwort auf die [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) und [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) Methoden bzw.  
  
 Da ein Port starten und beenden Prozesse physischen und logischen Programme kann, müssen diese Schnittstellen auch durch das Debugmodul implementiert werden:  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     Beschreibt den Prozess physischen. Mindestens die folgenden Methoden implementiert werden müssen:  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [getName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     Bietet eine Möglichkeit für die SDM Anfügen und trennen selbst aus einem Prozess.  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     Beschreibt die logische Anwendung an. Mindestens die folgenden Methoden implementiert werden müssen:  
  
    -   [getName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Bietet eine Möglichkeit für die SDM an diesem Programm angefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren eines Portanbieters](../../extensibility/debugger/implementing-a-port-supplier.md)