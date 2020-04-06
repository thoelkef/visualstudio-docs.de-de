---
title: Beenden eines Programms | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 985b20fe75f8ceee3d434ac681b437c51baf85e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712520"
---
# <a name="terminating-a-program"></a>Beenden eines Programms
Im folgenden Abschnitt wird das Beenden eines einzelnen Programms mit einem Thread beschrieben.

## <a name="termination-process"></a>Kündigungsprozess

1. Die DE sendet ein [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) mit einem gültigen [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).

2. Die DE sendet ein [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) mit einem gültigen [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).

   Die IDE wechselt in den Entwurfsmodus. Das Debugmodul oder die Laufzeitumgebung ruft [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) auf, um das Programm aus dem Port zu entfernen.

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
