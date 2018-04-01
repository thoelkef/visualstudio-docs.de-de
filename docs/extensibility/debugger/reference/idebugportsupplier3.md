---
title: IDebugPortSupplier3 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f0e1c5c252e0674ee3de8371080e298f42de2112
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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