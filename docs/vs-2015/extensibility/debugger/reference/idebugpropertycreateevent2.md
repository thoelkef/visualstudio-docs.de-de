---
title: IDebugPropertyCreateEvent2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1558aa8ca9cad93b00cf90f02f3af6d346b036b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698662"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle wird von der Debug-Engine (de) an den Sitzungs-Debug-Manager (SDM) gesendet, wenn eine Eigenschaft erstellt wird, die einem bestimmten Dokument zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die de implementiert diese Schnittstelle, um zu melden, dass eine Eigenschaft erstellt wurde. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf demselben Objekt wie diese Schnittstelle implementiert werden. Der SDM verwendet [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) für den Zugriff auf die- `IDebugEvent2` Schnittstelle. Diese Schnittstelle wird implementiert, wenn von de eine Eigenschaft erstellt wurde, die einem Skript zugeordnet ist, das geladen oder erstellt wurde, und wenn dieses Skript in der IDE angezeigt werden muss.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Das de erstellt und sendet dieses Ereignis Objekt, um zu melden, dass eine Eigenschaft erstellt wurde. Das Ereignis wird mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Rückruffunktion gesendet, die von der SDM bereitgestellt wird, wenn Sie an das Programm angefügt wird, das gedeppt wird.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle wird die-Methode der- `IDebugPropertyCreateEvent2` Schnittstelle gezeigt.  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Ruft die neue-Eigenschaft ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn einer Eigenschaft ein bestimmtes Dokument oder ein bestimmtes Skript zugeordnet ist, kann de dieses Ereignis an SDM senden, um das Fenster **Skript Dokumente** mit dem Namen des Dokuments zu aktualisieren. Der SDM ruft [getextendedinfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) mit dem-Argument `guidDocument` auf, um eine mit `VARIANT` einem [IUnknown](https://msdn.microsoft.com/library/e6b85472-e54b-4b8c-b19f-4454d6c05a8f) -Zeiger abzurufen. Der SDM ruft [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) auf diesem Zeiger auf, um die [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) -Schnittstelle abzurufen, die zum Aktualisieren des **Skript Dokument** Fensters verwendet wird.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
