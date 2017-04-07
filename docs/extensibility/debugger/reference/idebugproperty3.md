---
title: IDebugProperty3 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: 12
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
ms.openlocfilehash: 295baf524d3b1261826090164ccdf657b9672122
ms.lasthandoff: 04/05/2017

---
# <a name="idebugproperty3"></a>IDebugProperty3
Diese Schnittstelle bietet Unterstützung für:  
  
-   Abrufen von einer beliebig lange Zeichenfolge, die der Eigenschaft zugeordnet.  
  
-   Verknüpfen eine eindeutige ID, mit der Eigenschaft.  
  
-   Eine Liste der benutzerdefinierten Viewer für die Eigenschaft abgerufen.  
  
-   Festlegen des Werts einer Eigenschaft die Möglichkeit, alle resultierenden Fehler zu melden.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle für das gleiche Objekt, das implementiert [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) um Unterstützung für lange Zeichenfolgen, die Eigenschaft-IDs und benutzerdefinierten Viewer bereitzustellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf eine `IDebugProperty2` Schnittstelle, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den von geerbten Methoden `IDebugProperty2`, `IDebugProperty3` Schnittstelle macht die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Gibt die Länge der Zeichenfolge, die der Eigenschaft zugeordnet.|  
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Gibt die Zeichenfolge in einem vom Benutzer bereitgestellte Puffer zurück.|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Erstellt eine eindeutige ID für diese Eigenschaft an.|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Zerstört die eindeutige ID für diese Eigenschaft an.|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Gibt die Anzahl der benutzerdefinierten Viewer, denen diese Eigenschaft angezeigt werden kann.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Gibt die Liste der benutzerdefinierten Viewer, denen diese Eigenschaft angezeigt werden kann.|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Legt den Wert dieser Eigenschaft, die eine Fehlermeldung zurückgegeben wird, wenn nichts ein aufgetretenes Problem.|  
  
## <a name="remarks"></a>Hinweise  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) ist die bevorzugte Methode für die Sitzung Debug-Manager (SDM) Wert einer Eigenschaft festgelegt.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
