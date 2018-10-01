---
title: IDebugProperty2::GetMemoryContext | Microsoft-Dokumentation
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
- IDebugProperty2::GetMemoryContext
helpviewer_keywords:
- IDebugProperty2::GetMemoryContext
ms.assetid: 91793d25-790f-4881-a5c0-d0458e534514
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 67f29bb34bf1a514fe94db44bf235b5994b647ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522045"
---
# <a name="idebugproperty2getmemorycontext"></a>IDebugProperty2::GetMemoryContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugProperty2::GetMemoryContext](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty2-getmemorycontext).  
  
Ruft den Kontext Arbeitsspeicher den Wert der Eigenschaft ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetMemoryContext (   
   IDebugMemoryContext2** ppMemory  
);  
```  
  
```csharp  
int GetMemoryContext(  
   out IDebugMemoryContext2 ppMemory  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppMemory`  
 [out] Gibt die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Objekt, das diese Eigenschaft zugeordneten Arbeitsspeicher darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls den Fehlercode zurück. Gibt `S_GETMEMORYCONTEXT_NO_MEMORY_CONTEXT` liegt kein Speicherkontext abrufen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

