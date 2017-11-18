---
title: IDebugPropertyCreateEvent2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPropertyCreateEvent2
helpviewer_keywords: IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: afe91b8dfa6321d046b7bdeb301e426d1083263f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Diese Schnittstelle wird durch die Debugging-Modul (DE) an dem Sitzungs-Manager (SDM) gesendet, wenn es sich um eine Eigenschaft erstellt, die einem bestimmten Dokument zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle, um zu melden, dass eine Eigenschaft erstellt wurde. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf das gleiche Objekt wie diese Schnittstelle implementiert werden. Verwendet die SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle. Diese Schnittstelle wird implementiert, wenn die DE erstellt hat eine Eigenschaft verknüpft sind mit einem Skript, das geladen oder erstellt wurde und dieses Skript in der IDE angezeigt muss.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 DE erstellt und sendet diese Ereignisobjekt zum Bericht, der eine Eigenschaft erstellt wurde. Das Ereignis wird gesendet, mit der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion, die durch die SDM bereitgestellt wird, wenn es an das derzeit debuggte Programm angefügt ist.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methode die `IDebugPropertyCreateEvent2` Schnittstelle.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Ruft die neue Eigenschaft ab.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Eigenschaft einer bestimmten Dokument oder einem Skript zugeordnet wurde, DE kann dieses Ereignis senden, um die SDM zum Aktualisieren von der **Skriptdokumente** Fenster mit dem Namen des Dokuments. Ruft die SDM [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) mit dem Argument `guidDocument` zum Abrufen einer `VARIANT` , enthält eine [IUnknown](/cpp/atl/iunknown) Zeiger. Ruft die SDM [QueryInterface](/cpp/atl/queryinterface) für diesen Zeiger zum Abrufen der [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) Schnittstelle, die verwendet wird, zum Aktualisieren der **Skriptdokumente** Fenster.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)