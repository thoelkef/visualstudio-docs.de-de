---
title: Erstellen eines Haltepunkts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d252f1310c3e251c44525cd94c4d9a2943d8171d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739056"
---
# <a name="create-a-breakpoint"></a>Erstellen eines Haltepunkts
Im Folgenden wird der Prozess des Erstellens eines Haltepunkts beschrieben.

## <a name="methods-in-breakpoint-creation"></a>Methoden bei der Breakpoint-Erstellung
 Wenn das Modul geladen wird, das zum Binden eines Haltepunkts erforderlich ist, ruft der Sitzungsdebug-Manager (SDM) die folgenden Methoden auf:

1. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)

2. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)

3. [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)

    > [!NOTE]
    > **CanBind** wird nur aufgerufen, wenn ein Benutzer einen Haltepunkt aus dem **Breakpoints-Fenster** erstellt.

4. [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

5. [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
