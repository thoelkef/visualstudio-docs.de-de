---
title: IDebugCoreServer2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce3e4c0c933527a5db754dcd96de97283e6e8260
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107565"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Diese Schnittstelle wird verwendet, um darzustellen, und Abrufen von Informationen von einem Server auf einem Computer im Netzwerk.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Visual Studio implementiert diese Schnittstelle, um einen Server darstellen. Jede Instanz von Visual Studio erstellt eine Instanz dieser Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein benutzerdefinierten Port Lieferanten empfängt diese Schnittstelle in einem Aufruf von [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Ein Debugmodul erhalten diese Schnittstelle indirekt durch einen Aufruf von [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (welche gibt [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), eine Schnittstelle, die abgeleitet ist `IDebugCoreServer2`).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugCoreServer2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Ruft den Namen und die Attribute eines Computers an.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Ruft den Namen eines Computers ab.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Ruft einen Port Lieferanten, der vorhanden ist auf einem Computer ab.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Ruft einen Port, der auf einem Computer bereits vorhanden ist.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Erstellt einen Enumerator für alle Ports auf einem Computer an.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Erstellt einen Enumerator für alle Lieferanten Port auf einem Computer an.|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Ruft die Hilfsprogramme für die Computer für einen Computer an.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle wird auch von Visual Studio verwendet, um Prozesse, die auf Computern im Netzwerk zu durchsuchen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)