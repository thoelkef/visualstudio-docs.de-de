---
title: Erforderliche Port Lieferanten Schnittstellen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcb8bae5d715e59591eb44418de2b36e8ac753a5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60112506"
---
# <a name="required-port-supplier-interfaces"></a>Erforderliche Port Lieferanten-Schnittstellen
Muss ein portanbieters implementieren die [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) Schnittstelle.[ IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Ein portanbieters Ports bereitstellt und implementiert werden. Aus diesem Grund müssen sie die folgenden Schnittstellen ausführen:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

     Beschreibt den Port ein, und listet alle Prozesse, die auf den Port ausgeführt wird.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

     Bietet für starten und Beenden von Prozessen auf dem Port.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

     Stellt einen Mechanismus für Programme, die im Kontext des Ports, eine Benachrichtigung der Programm-Knoten-Erstellung und Zerstörung ausgeführt. Weitere Informationen finden Sie unter [Programmieren Knoten](../../extensibility/debugger/program-nodes.md).

- `IConnectionPointContainer`

     Stellt einen Verbindungspunkt zum [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).

## <a name="port-supplier-operation"></a>Lieferanten portvorgang
 Die [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) Senke empfängt Benachrichtigungen, wenn der Prozess und Programme erstellt und an einem Port zerstört werden. Ein Port ist erforderlich, um das Senden von [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) Wenn ein Prozess erstellt wird und [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) Wenn ein Prozess auf dem Port zerstört wird. Ein Port ist auch erforderlich, zum Senden von [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) Wenn ein Programm erstellt wird und [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) Wenn ein Programm in einem Prozess ausgeführt wird, auf dem Port zerstört wird.

 Ein Port in der Regel sendet Programm erstellen und zerstören Ereignisse als Reaktion auf die [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) und [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) Methoden bzw.

 Da ein Port starten und beenden sowohl die physikalischen Prozesse, die als auch die logische Programme, müssen die folgenden Schnittstellen auch von der Debug-Engine implementiert werden:

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

     Beschreibt den physischen Prozess. Mindestens die folgenden Methoden implementiert werden müssen:

    - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

    - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

    - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

    - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

    - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

    - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

     Bietet eine Möglichkeit, das SDM Anfügen und trennen selbst von einem Prozess an.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

     Beschreibt die logische Anwendung an. Mindestens die folgenden Methoden implementiert werden müssen:

    - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

    - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

    - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

     Bietet eine Möglichkeit, das SDM zum Anfügen an diesem Programm.

## <a name="see-also"></a>Siehe auch
- [Implementieren eines portanbieters](../../extensibility/debugger/implementing-a-port-supplier.md)