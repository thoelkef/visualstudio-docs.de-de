---
title: Wenn ein Breakpoint gebunden wird oder ungebunden wird | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1425edc2c8fc3fe8c38c133388f90b18b516b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162167"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>Binden bzw. Aufheben der Bindung eines Haltepunkts
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn ein Haltepunkt nicht gebunden werden kann, wenn ein Aufruf an die [IDebugPendingBreakpoint2:: canbind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) -Methode erfolgt, unterscheiden sich die Bindungs Zeit und die Erstellungszeit des Breakpoints.  
  
## <a name="methods-called"></a>Aufgerufene Methoden  
 Der Sitzungs-Debug-Manager (SDM) Ruft die folgenden Methoden auf:  
  
1. [IDebugEngine2:: kreateperdingbreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). DE gibt ein [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)-Wert zurück.  
  
2. [IDebugPendingBreakpoint2:: enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).  
  
3. [IDebugPendingBreakpoint2:: Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).  
  
4. Die [IDebugPendingBreakpoint2:: Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) -Methode und gibt S_OK zurück. Der de sendet eine [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) oder [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).  
  
5. [IDebugBreakpointBoundEvent2:: getpdingbreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) -und [IDebugBreakpointBoundEvent2:: enumboundbreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) -Methoden, um zu überprüfen und die gebundenen Haltepunkte zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
