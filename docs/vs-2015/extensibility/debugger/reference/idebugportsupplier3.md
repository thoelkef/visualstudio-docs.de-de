---
title: IDebugPortSupplier3 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4ece720cf6880bba528dee99cdbdeb25c10087a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65674132"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Mit dieser Schnittstelle kann ein Aufrufer ermitteln, ob ein Port Lieferant Ports (durch das Schreiben auf einen Datenträger) zwischen den Aufrufen des Debuggers beibehalten und dann eine Liste mit diesen beibehaltenen Ports erhalten soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein benutzerdefinierter Port Lieferant implementiert diese Schnittstelle, um die Beibehaltung oder Speicherung von Port Informationen auf dem Datenträger zu unterstützen Diese Schnittstelle muss auf demselben Objekt wie die [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) -Schnittstelle implementiert werden.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) für die-Schnittstelle auf `IDebugPortSupplier2` , um diese Schnittstelle abzurufen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge  
 Zusätzlich zu den von der [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) -Schnittstelle geerbten Methoden unterstützt diese Schnittstelle Folgendes:  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Gibt zurück, ob der Port Lieferant Ports (durch das Schreiben auf einen Datenträger) zwischen den Aufrufen des Debuggers beibehalten kann.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Gibt ein Objekt zurück, das verwendet werden kann, um alle Ports aufzuzählen, die von diesem Port Lieferanten auf den Datenträger geschrieben wurden.|  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein Port Lieferant Ports über Aufrufe hinweg beibehalten kann, sollte er diese Schnittstelle implementieren. Ports sollten geladen werden, wenn der Port Lieferant instanziiert wird, und auf den Datenträger geschrieben, wenn der Port Lieferant zerstört wird.  
  
 Eine Debug-Engine interagiert in der Regel nicht mit einem Port Lieferanten und wird für diese Schnittstelle nicht verwendet.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
