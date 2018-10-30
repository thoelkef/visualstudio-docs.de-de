---
title: MACHINE_INFO | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e548552b5acda6a3334b6d7df90b2aeab80c2e77
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847226"
---
# <a name="machineinfo"></a>MACHINE_INFO
Beschreibt einen bestimmten Computer an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct tagMACHINE_INFO {   
   MACHINE_INFO_FIELDS Fields;  
   BSTR                bstrName;  
   MACHINE_INFO_FLAGS  Flags;  
} MACHINE_INFO;  
```  
  
```csharp  
public struct MACHINE_INFO {   
   public uint   Fields;  
   public string bstrName;  
   public uint   Flags;  
};  
```  
  
## <a name="members"></a>Member  
 `Fields`  
 Eine Kombination von Flags aus der [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) -Enumeration, die angeben, welche Felder der Struktur initialisiert werden.  
  
 `bstrName`  
 Der Name des Computers. Entspricht dem Aufruf von [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md).  
  
 `Flags`  
 Eine Kombination von Flags aus der [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) Enumeration, die die Computerattribute beschreibt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zurückgegeben, durch einen Aufruf der [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)