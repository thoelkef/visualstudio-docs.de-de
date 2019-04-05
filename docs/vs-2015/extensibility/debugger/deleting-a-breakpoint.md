---
title: Löschen eines Haltepunkts | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9a70cfe5b728cc9af019752bd0c9c9d2f5105043
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957691"
---
# <a name="deleting-a-breakpoint"></a>Löschen eines Haltepunkts
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im folgenden beschreibt den Prozess, wenn einen ausstehenden Haltepunkt zu löschen:  
  
## <a name="deletion-process"></a>Vorgang zum Löschen  
 Ruft die Sitzungs-Debug-Manager (SDM) die [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) Methode, um den ausstehenden Haltepunkt, und alle gebundener Haltepunkte entfernen daraus gebunden.  
  
> [!NOTE]
>  Ein einzelnen gebundener Haltepunkt auch gelöscht werden, durch einen Aufruf von [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
