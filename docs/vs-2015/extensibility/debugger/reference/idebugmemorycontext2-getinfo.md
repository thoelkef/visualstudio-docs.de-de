---
title: IDebugMemoryContext2::GetInfo | Microsoft-Dokumentation
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
- IDebugMemoryContext2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugMemoryContext2::GetInfo method
ms.assetid: 08c7f091-1816-4d64-8834-f9ecaac5c58d
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 94f6d64bdb11fcd930c04a4d50f8cd3b7037bc58
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522221"
---
# <a name="idebugmemorycontext2getinfo"></a>IDebugMemoryContext2::GetInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugMemoryContext2::GetInfo](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmemorycontext2-getinfo).  
  
Ruft eine [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) -Struktur, die den Kontext beschreibt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetInfo(   
   CONTEXT_INFO_FIELDS dwFields,  
   CONTEXT_INFO*       pInfo  
);  
```  
  
```csharp  
int GetInfo(  
   enum_CONTEXT_INFO_FIELDS dwFields,   
   CONTEXT_INFO[]           pinfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFields`  
 [in] Eine Kombination von Flags aus der [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) Enumeration, die angeben, welche Felder der der [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Struktur werden füllen.  
  
 `pInfo`  
 [in, out] Die `CONTEXT_INFO` -Struktur, die ausgefüllt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)

