---
title: IDebugReturnValueEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugReturnValueEvent2
helpviewer_keywords:
- IDebugReturnValueEvent2
ms.assetid: 2daded43-e427-4fbb-a19e-f3834e3723af
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0ad57acd6218158b1dd10b0f18e421bcd397a2d6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugreturnvalueevent2"></a>IDebugReturnValueEvent2
Diese Schnittstelle wird durch die Debugging-Modul (DE) an dem Sitzung Debug-Manager (SDM) gesendet, nach dem Ausführen in Einzelschritten aus oder über eine Funktion.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugReturnValueEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle, um den Rückgabewert einer Funktion zu melden, die von oder im Zeitverlauf Einzelschrittmodus wurde. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf das gleiche Objekt wie diese Schnittstelle implementiert werden. Verwendet die SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die DE erstellt und sendet diese Ereignisobjekt, um den Rückgabewert einer Funktion zu melden. Das Ereignis wird gesendet, mit der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion, die durch die SDM bereitgestellt wird, wenn es an das derzeit debuggte Programm angefügt ist.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methode der `IDebugReturnValueEvent2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)|Ruft den Wert für eine Funktion mit dem verlassen zurückgegeben wird.|  
  
## <a name="remarks"></a>Hinweise  
 Der von einer Funktion zurückgegebenen Wert abgerufen werden kann, durch den Aufruf [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md). Der zurückgegebene Wert wird angezeigt, der **"Auto"** Fenster.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)