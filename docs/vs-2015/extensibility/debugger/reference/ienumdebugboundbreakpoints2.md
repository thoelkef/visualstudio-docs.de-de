---
title: IEnumDebugBoundBreakpoints2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5ae2329b434178cfc38d544a79254f4b089811a6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775289"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle Listet die gebundene Haltepunkte ein ausstehender Haltepunkt zugeordnet oder Haltepunkt gebunden Ereignis.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugBoundBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (DE) implementiert diese Schnittstelle als Teil der Unterstützung für Haltepunkte an. Diese Schnittstelle muss implementiert werden, wenn Haltepunkte unterstützt werden.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Visual Studio aufgerufen werden:  
  
-   [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) , rufen Sie diese Schnittstelle stellt eine Liste aller Haltepunkte, die ausgelöst wurden.  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) , rufen Sie diese Schnittstelle, die eine Liste aller Haltepunkte, die gebunden waren darstellt.  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) beim Abrufen der diese Schnittstelle, die eine Liste aller Haltepunkte, die an diesem ausstehenden Haltepunkt gebunden darstellt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IEnumDebugBoundBreakpoints2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Ruft eine angegebene Anzahl gebundener Haltepunkte in einer Enumerationsfolge ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Überspringt eine angegebene Anzahl gebundener Haltepunkte in einer Enumerationsfolge.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Ruft die Anzahl gebundener Haltepunkte in einen Enumerator ab.|  
  
## <a name="remarks"></a>Hinweise  
 Visual Studio verwendet die gebundene Haltepunkte, die von dieser Schnittstelle dargestellt, zum Aktualisieren der Anzeige von Haltepunkten in der IDE.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)

