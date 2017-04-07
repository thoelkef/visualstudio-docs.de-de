---
title: IDebugEntryPointEvent2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 194db40a0f73d998d5bf944fde42f09cd7f97b7d
ms.lasthandoff: 04/05/2017

---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
Die Debugging-Modul (DE) sendet diese Schnittstelle zu der Sitzung Debug-Manager (SDM), wenn das Programm wird gleich die erste Anweisung des Benutzercodes ausgeführt.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle als Teil seiner normalen Betrieb. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf das gleiche Objekt wie diese Schnittstelle implementiert werden. Verwendet die SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Der Code wird erstellt und sendet diese Ereignisobjekt zu debuggenden Programms geladen wurde und bereit zur Ausführung der ersten Anweisung des Benutzercodes ist. Das Ereignis wird gesendet, mit der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion, die durch die SDM bereitgestellt wird, wenn diese an die derzeit debuggte Programm angefügt.  
  
## <a name="remarks"></a>Hinweise  
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) wird gesendet, wenn das Programm wird gleich die erste Anweisung auszuführen. Beispielsweise `IDebugEntryPoint2` wird gesendet, wenn das Programm zum Ausführen des Benutzers ist `main` Funktion.  
  
 Wenn die DE sendet `IDebugEntryPointEvent2`, die aktuelle Position der Code sollte bei der ersten Anweisung des Benutzercodes, z. B. `main`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
