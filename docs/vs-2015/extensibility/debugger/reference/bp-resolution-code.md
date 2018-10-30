---
title: BP_RESOLUTION_CODE | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_RESOLUTION_CODE
helpviewer_keywords:
- BP_RESOLUTION_CODE structure
ms.assetid: ac103ec5-771c-4667-92de-b5abb53bbb52
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 25c551a9805c1a482dbbb58bb30dfb9400a8aaa6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924680"
---
# <a name="bpresolutioncode"></a>BP_RESOLUTION_CODE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Beschreibt den Speicherort eines Haltepunkts Code.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _BP_RESOLUTION_CODE {   
   IDebugCodeContext2* pCodeContext;  
} BP_RESOLUTION_CODE;  
```  
  
```csharp  
public struct BP_RESOLUTION_CODE {   
   public IDebugCodeContext2 pCodeContext;  
};  
```  
  
## <a name="members"></a>Member  
 `pCodeContext`  
 Die [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Objekt, das die Position des Breakpoints im Code identifiziert.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur ist ein Mitglied der [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) -Struktur, die in ein Mitglied zu aktivieren ist die [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) vom zurückgegebene Struktur der [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)

