---
title: Treten im Pausenmodus | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3161fc1c1ec8b44d96b3793198ac630ba2e32d67
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712860"
---
# <a name="stepping-in-break-mode"></a>Treten im Pausenmodus
Im folgenden Abschnitt wird der Prozess beschrieben, der auftritt, wenn sich der Debugger im Unterbrechungsmodus befindet und Code durchlaufen muss:

## <a name="stepping-process"></a>Stepping-Prozess

1. Rufen Sie [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) mit [STEPKIND-](../../extensibility/debugger/reference/stepkind.md) und [STEPUNIT-Argumenten](../../extensibility/debugger/reference/stepunit.md) auf, um einen Schritt auszuführen.

2. Wenn der Schritt abgeschlossen ist, senden Sie ein [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) als Stoppereignis.

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
