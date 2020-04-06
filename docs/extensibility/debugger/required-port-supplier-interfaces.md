---
title: Erforderliche Port Supplier Schnittstellen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2aeb1f26f81d773e171aa3fed6b0f2ef976c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713151"
---
# <a name="required-port-supplier-interfaces"></a>Erforderliche Port-Lieferanten-Schnittstellen
Ein Portlieferant muss die [IDebugPortSupplier2-Schnittstelle](../../extensibility/debugger/reference/idebugportsupplier2.md) implementieren. [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Ein Hafenlieferant liefert Häfen und implementiert sie. Daher müssen die folgenden Schnittstellen ausgeführt werden:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Beschreibt den Port und zählt alle Prozesse auf, die auf dem Port ausgeführt werden.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Bietet das Starten und Beenden von Prozessen auf dem Port.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Stellt einen Mechanismus für Programme bereit, die im Kontext dieses Ports ausgeführt werden, um ihn über die Erstellung und Zerstörung von Programmknoten zu informieren. Weitere Informationen finden Sie unter [Programmknoten](../../extensibility/debugger/program-nodes.md).

- `IConnectionPointContainer`

  Stellt einen Verbindungspunkt für [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)bereit.

## <a name="port-supplier-operation"></a>Hafenlieferantenbetrieb
 Die [IDebugPortEvents2-Senke](../../extensibility/debugger/reference/idebugportevents2.md) empfängt Benachrichtigungen, wenn Prozesse und Programme an einem Port erstellt und zerstört werden. Ein Port ist erforderlich, um [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) zu senden, wenn ein Prozess erstellt wird, und [IDebugProcessDestroyEvent2,](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) wenn ein Prozess am Port zerstört wird. Ein Port ist auch erforderlich, um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zu senden, wenn ein Programm erstellt wird, und [IDebugProgramDestroyEvent2,](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) wenn ein Programm in einem Prozess zerstört wird, der auf dem Port ausgeführt wird.

 Ein Port sendet in der Regel Programmerstellungs- und -zerstörungsereignisse als Reaktion auf die [AddProgramNode-](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) bzw. [RemoveProgramNode-Methoden.](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)

 Da ein Port sowohl physische Prozesse als auch logische Programme starten und beenden kann, müssen die folgenden Schnittstellen auch vom Debugmodul implementiert werden:

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  Beschreibt den physischen Prozess. Mindestens die folgenden Methoden müssen implementiert werden:

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  Bietet dem SDM die Möglichkeit, sich an einen Prozess anzuhängen und von ihm zu lösen.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Beschreibt das logische Programm. Mindestens die folgenden Methoden müssen implementiert werden:

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [Getprocess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  Bietet eine Möglichkeit für das SDM, an dieses Programm anzuhängen.

## <a name="see-also"></a>Weitere Informationen
- [Implementieren eines Hafenlieferanten](../../extensibility/debugger/implementing-a-port-supplier.md)
