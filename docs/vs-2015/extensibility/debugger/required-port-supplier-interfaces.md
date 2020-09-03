---
title: Erforderliche Port Lieferanten Schnittstellen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a065389a6b9b67b8bce82394569ce65afb0f8d55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821438"
---
# <a name="required-port-supplier-interfaces"></a>Schnittstellen für erforderliche Portanbieter
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Port Lieferant muss die [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) -Schnittstelle implementieren. [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Da ein Port Lieferant Ports bereitstellt, muss dieser auch implementiert werden. Daher müssen die folgenden Schnittstellen implementiert werden:  
  
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Beschreibt den Port und kann alle Prozesse auflisten, die auf dem Port ausgeführt werden.  
  
- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Ermöglicht das Starten und Beenden von Prozessen auf dem Port.  
  
- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Bietet einen Mechanismus für Programme, die innerhalb des Kontexts dieses Ports ausgeführt werden, um Sie über die Erstellung und Zerstörung von Programmknoten zu benachrichtigen. Weitere Informationen finden Sie unter [Programmknoten](../../extensibility/debugger/program-nodes.md).  
  
- `IConnectionPointContainer`  
  
     Stellt einen Verbindungspunkt für [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)bereit.  
  
## <a name="port-supplier-operation"></a>Port Lieferanten Vorgang  
 Die [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) -Senke empfängt Benachrichtigungen, wenn Prozess und Programme auf einem Port erstellt und zerstört werden. Ein Port ist erforderlich, um [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) zu senden, wenn ein Prozess erstellt wird, und [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) , wenn ein Prozess auf dem Port zerstört wird. Ein Port ist auch erforderlich, um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zu senden, wenn ein Programm erstellt wird, und [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) , wenn ein Programm in einem Prozess zerstört wird, der auf dem Port ausgeführt wird.  
  
 Ein Port sendet in der Regel Programm Erstellungs-und Lösch Ereignisse als Reaktion auf die Methoden " [addprogramnode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) " und " [removeprogramnode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) ".  
  
 Da ein Port sowohl physische als auch logische Programme starten und beenden kann, müssen diese Schnittstellen auch von der Debug-Engine implementiert werden:  
  
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
  Beschreibt den physischen Prozess. Mindestens die folgenden Methoden müssen implementiert werden:  

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  

  - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
    Bietet eine Möglichkeit für das Anfügen und trennen von SDM von einem Prozess.  
  
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
  Beschreibt das logische Programm. Mindestens die folgenden Methoden müssen implementiert werden:  

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Bietet eine Möglichkeit, das SDM an dieses Programm anzufügen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren eines Portanbieters](../../extensibility/debugger/implementing-a-port-supplier.md)
