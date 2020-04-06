---
title: Threads | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ed5c06e0c42dac1f0539cc2c7c5886d95b23ae1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712478"
---
# <a name="threads"></a>Threads
In der Debuggerarchitektur wird ein *Thread*:

- Ist die grundlegende Recheneinheit. Ein Thread führt seine Anweisungen sequenziell im Kontext einer einzelnen Aufrufliste aus und wechselt von einem Codekontext zum nächsten.

- Kann sich selbst und das Programm identifizieren, in dem es ausgeführt wird. Threads können benannt, angehalten und fortgesetzt werden. Ein Thread kann auch die zugehörigen Stapelrahmen auflisten und unter bestimmten Bedingungen in einen anderen Stapelrahmen verschoben werden. Angesichts des Kontexts eines Stapelrahmens kann ein Thread den zugeordneten logischen Thread zurückgeben, falls vorhanden. Ein Thread verfügt über Eigenschaften, z. B. eine Suspend-Anzahl, die im **Threads-Fenster** der IDE angezeigt werden können.

- Wird durch eine [IDebugThread2-Schnittstelle](../../extensibility/debugger/reference/idebugthread2.md) dargestellt, die in der Regel von einem Debugmodul (DE) oder einer virtuellen Maschine als Folge der Ausführung eines Programms erstellt wird.

## <a name="see-also"></a>Weitere Informationen
- [Programs](../../extensibility/debugger/programs.md)
- [Stapelrahmen](../../extensibility/debugger/stack-frames.md)
- [Debug-Engine](../../extensibility/debugger/debug-engine.md)
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [Sitzungsdebug-Manager](../../extensibility/debugger/session-debug-manager.md)
