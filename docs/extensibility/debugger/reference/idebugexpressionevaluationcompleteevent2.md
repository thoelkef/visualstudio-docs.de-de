---
title: IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 42dfc3ed4a4bff3e0c32d7155a74d74c1c6d0503
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
Diese Schnittstelle wird durch die Debugging-Modul (DE) an dem Sitzung Debug-Manager (SDM) gesendet, wenn asynchrone ausdrucksauswertung abgeschlossen ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugExpressionEvaluationCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle zum Bericht Abschluss eine ausdrucksauswertung, die durch einen Aufruf gestartet [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf das gleiche Objekt wie diese Schnittstelle implementiert werden. Verwendet die SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die DE erstellt und sendet diese Ereignisobjekt, um den Abschluss der Auswertung von Ausdrücken zu melden. Das Ereignis wird gesendet, mit der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion, die durch die SDM bereitgestellt wird, wenn diese an die derzeit debuggte Programm angefügt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugExpressionEvaluationCompleteEvent2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Ruft den ursprünglichen Ausdruck ab.|  
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Ruft das Ergebnis der Auswertung von Ausdrücken ab.|  
  
## <a name="remarks"></a>Hinweise  
 Die DE muss dieses Ereignis zu senden, ob die Auswertung erfolgreich oder nicht war.  
  
 Wenn die Auswertung nicht erfolgreich war, die `DEBUG_PROPINFO_VALUE` und `DEBUG_PROPINFO_ATTRIB` Flags können nicht festgelegt werden, der [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) -Struktur, die von zurückgegeben wird [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (die [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Objekt durch die DE erstellt und zurückgegeben, die der `IDebugExpressionEvaluationCompleteEvent2` Ereignis, wenn die Auswertung fehlschlug).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)