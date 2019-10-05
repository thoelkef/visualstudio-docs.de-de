---
title: PROCESS_INFO_FLAGS | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88ff2a1da1f937fd4011932979bd95057eb40dfd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205054"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Beschreibt, oder gibt die Eigenschaften eines Prozesses an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```csharp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## <a name="members"></a>Member  
 PIFLAG_SYSTEM_PROCESS  
 Gibt an, dass der Prozess ein Systemprozess ist.  
  
 PIFLAG_DEBUGGER_ATTACHED  
 Gibt an, dass der Prozess von einem Debugger debuggt wird. Es ist möglicherweise eine [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Debugger, oder es möglicherweise einige andere Debugger, z. B. WinDbg.  
  
 PIFLAG_PROCESS_STOPPED  
 Gibt an, dass der Prozess beendet wird. Nur gültig, wenn `PIFLAG_DEBUGGER_ATTACHED` ist ebenfalls angegeben. Verfügbar in [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] und höher.  
  
 PIFLAG_PROCESS_RUNNING  
 Gibt an, dass der Prozess ausgeführt wird. Nur gültig, wenn `PIFLAG_DEBUGGER_ATTACHED` ist ebenfalls angegeben. Verfügbar in [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] und höher.  
  
## <a name="remarks"></a>Hinweise  
 Verwendet für die `Flags` Mitglied der [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Struktur.  
  
 Diese Flags können kombiniert werden, mit einer bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
