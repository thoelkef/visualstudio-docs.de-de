---
title: IDebugPortSupplier3 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 8
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
ms.openlocfilehash: 0eb7cf542fa61d53220cd10f54e3fbd7c6165bf4
ms.lasthandoff: 04/05/2017

---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Diese Schnittstelle kann einen Aufrufer bestimmen, ob ein Port Lieferant Ports (indem sie auf den Datenträger geschrieben wird) zwischen den Aufrufen des Debuggers beibehalten und Sie anschließend eine Liste mit diesen beibehaltenen Ports rufen kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle zum beibehalten oder Speichern der Portinformationen auf den Datenträger zu unterstützen. Diese Schnittstelle muss implementiert werden, auf das gleiche Objekt wie die [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf die `IDebugPortSupplier2` Schnittstelle, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den von geerbten Methoden der [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) diese Schnittstelle unterstützt die folgenden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Gibt zurück, ob der Port Lieferant Ports beibehalten werden kann (indem sie auf den Datenträger geschrieben wird) zwischen den Aufrufen des Debuggers.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Gibt ein Objekt, das verwendet werden kann zum Aufzählen über alle Ports, die auf den Datenträger geschrieben wurden, diesen Port Lieferant zurück.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Lieferant Port Ports für Aufrufe beibehalten kann, sollte er diese Schnittstelle implementieren. Ports sollten geladen werden, wenn der Lieferant Port instanziiert, und wenn der Lieferant Port zerstört wird auf den Datenträger geschrieben.  
  
 Debugging-Modul ist in der Regel interagiert nicht mit einem Port Lieferanten und verfügt über keine Verwendung für diese Schnittstelle.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
