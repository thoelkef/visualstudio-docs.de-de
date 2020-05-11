---
title: Löschen eines Haltepunkts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a77be200a11eb7b3985a4c1a47e4cddaa543f900
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738948"
---
# <a name="deleting-a-breakpoint"></a>Löschen eines Haltepunkts
Im Folgenden wird der Prozess beim Löschen eines ausstehenden Haltepunkts beschrieben:

## <a name="deletion-process"></a>Löschvorgang
 Der Sitzungsdebug-Manager (SDM) ruft die [IDebugPendingBreakpoint2::Delete-Methode](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) auf, um den ausstehenden Haltepunkt und alle gebundenen Haltepunkte, die davon gebunden sind, zu entfernen.

> [!NOTE]
> Ein einzelner gebundener Haltepunkt kann auch durch einen Aufruf von [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)gelöscht werden.

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
