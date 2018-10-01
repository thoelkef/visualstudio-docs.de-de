---
title: PROCESS_INFO_FLAGS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5f8bd5fdf7e377e7b43325a49aaa9dc505022cef
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512990"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [PROCESS_INFO_FLAGS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/process-info-flags).  
  
Beschreibt, oder gibt die Eigenschaften eines Prozesses an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```csharp  
enum enum_PROCESS_INFO_FLAGS {   
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

