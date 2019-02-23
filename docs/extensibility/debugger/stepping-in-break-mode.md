---
title: Schrittausführung im Unterbrechungsmodus | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 66e7e227daa0dd58bf24ae946cce667992e09f90
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685026"
---
# <a name="stepping-in-break-mode"></a>Schrittausführung im Unterbrechungsmodus
Der folgende Abschnitt beschreibt den Prozess, der tritt auf, wenn der Debugger im Unterbrechungsmodus ist und Code durchlaufen schrittweise muss:

## <a name="stepping-process"></a>Zum schrittweisen Prozess

1.  Rufen Sie [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) mit [STEPKIND](../../extensibility/debugger/reference/stepkind.md) und [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) Argumente für einen Schritt ausführen.

2.  Wenn der Schritt abgeschlossen ist, Senden einer [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) als Beenden-Ereignis.

## <a name="see-also"></a>Siehe auch
- [Aufrufen von debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)