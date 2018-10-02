---
title: IDebugBreakpointRequest2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 78625ecd7c044f8add777a705259cff8ef5f15be
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522915"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugBreakpointRequest2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbreakpointrequest2).  
  
Diese Schnittstelle stellt die erforderlichen Informationen zum Erstellen und binden jeden Typ von Breakpoint.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBreakpointRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von der Sitzungs-Manager (SDM) in der Regel implementiert.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die Debug-Engine (DE) empfängt, diese Schnittstelle durch einen Aufruf von [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) um ein ausstehender Haltepunkt zu erstellen. Ein Aufruf von [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) können dieser Schnittstelle aus dem DE abrufen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugBreakpointRequest2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Ruft die Haltepunktpositionstyp dieser Haltepunkt-Anforderung ab.|  
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Ruft ab, der diese Anforderung Breakpoint beschreibt Informationen zu den Haltepunkt.|  
  
## <a name="remarks"></a>Hinweise  
 Nachdem das Programm im Debugmodus befindlichen geladen wurde, einen Aufruf von [binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) einen ausstehenden Haltepunkt an der angeforderte Speicherort im Programm gebunden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)   
 [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

