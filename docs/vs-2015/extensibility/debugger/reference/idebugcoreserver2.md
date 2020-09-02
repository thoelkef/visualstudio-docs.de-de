---
title: IDebugCoreServer2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c0bca6ccd3738518df339084b0f6463be181e52d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192913"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle dient zur Darstellung und zum Abrufen von Informationen von einem Server auf einem Computer im Netzwerk.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von Visual Studio implementiert, um einen Server darzustellen. Jede Instanz von Visual Studio erstellt eine Instanz dieser Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein benutzerdefinierter Port Lieferant empfängt diese Schnittstelle in einem [Ereignis Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Eine Debug-Engine kann diese Schnittstelle indirekt durch einen get-Befehl von [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) abrufen (der [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)zurückgibt, eine Schnittstelle, die von abgeleitet ist `IDebugCoreServer2` ).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugCoreServer2` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Ruft den Namen und die Attribute eines Computers ab.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Ruft den Namen eines Computers ab.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Ruft einen Port Lieferanten ab, der auf einem Computer vorhanden ist.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Ruft einen Port ab, der bereits auf einem Computer vorhanden ist.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Erstellt einen Enumerator für alle Ports auf einem Computer.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Erstellt einen Enumerator für alle Port Lieferanten auf einem Computer.|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Ruft die Computer Dienstprogramme für einen Computer ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Schnittstelle wird auch von Visual Studio verwendet, um Prozesse zu durchsuchen, die auf Computern im Netzwerk ausgeführt werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Veranstalter](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
