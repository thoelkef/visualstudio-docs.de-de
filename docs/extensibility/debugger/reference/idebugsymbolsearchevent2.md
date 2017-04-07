---
title: IDebugSymbolSearchEvent2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
caps.latest.revision: 10
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
ms.openlocfilehash: 92385ae5922ecd16658f089c28cfd3746b6ff093
ms.lasthandoff: 04/05/2017

---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
Diese Schnittstelle wird durch die Debugging-Modul (DE) gesendet, um anzugeben, dass die Debugsymbole für ein Modul, das gerade gedebuggt wird geladen wurden.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugSymbolSearchEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle, um zu melden, dass ein Modul Symbole geladen wurden. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf das gleiche Objekt wie diese Schnittstelle implementiert werden. Verwendet die SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die DE erstellt und sendet diese Ereignisobjekt Berichten, dass ein Modul Symbole geladen wurden. Das Ereignis wird gesendet, mit der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion, die durch die SDM bereitgestellt wird, wenn diese an die derzeit debuggte Programm angefügt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die `IDebugSymbolSearchEvent2` Schnittstelle verfügbar macht, die folgende Methode.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Ruft Informationen zu den Ergebnissen einer Suche Symbol ab.|  
  
## <a name="remarks"></a>Hinweise  
 Dieses Ereignis wird gesendet werden, auch wenn die Symbole konnte nicht geladen werden. Aufrufen von `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` ermöglicht dem Handler für dieses Ereignis, um festzustellen, ob das Modul tatsächlich Symbole hat.  
  
 Visual Studio verwendet dieses Ereignis in der Regel zum Aktualisieren des Status der geladenen Symbole in der **Module** Fenster.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
