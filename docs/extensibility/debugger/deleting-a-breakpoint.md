---
title: Löschen eines Haltepunkts | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b63fa7622b7dea4a6ad5c516547518911110a8ef
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958039"
---
# <a name="deleting-a-breakpoint"></a>Löschen eines Haltepunkts
Im folgenden beschreibt den Prozess, wenn einen ausstehenden Haltepunkt zu löschen:  
  
## <a name="deletion-process"></a>Vorgang zum Löschen  
 Ruft die Sitzungs-Debug-Manager (SDM) die [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) Methode, um den ausstehenden Haltepunkt, und alle gebundener Haltepunkte entfernen daraus gebunden.  
  
> [!NOTE]
>  Ein einzelnen gebundener Haltepunkt auch gelöscht werden, durch einen Aufruf von [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)