---
title: IDebugStackFrame3::GetUnwindCodeContext | Microsoft-Dokumentation
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
- IDebugStackFrame3::GetUnwindCodeContext
helpviewer_keywords:
- IDebugStackFrame3::GetUnwindCodeContext method
ms.assetid: b25f7e7d-2b24-48e4-93b3-829e61d73ebf
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7f450454b7eba05e0267a9fb5a4ed10c8940e153
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511891"
---
# <a name="idebugstackframe3getunwindcodecontext"></a>IDebugStackFrame3::GetUnwindCodeContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugStackFrame3::GetUnwindCodeContext](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext).  
  
Gibt zurück, der Codekontext, eine Position darstellt, wenn ein Stapel zu, Vorgang Entladen aufgetreten ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetUnwindCodeContext(  
   IDebugCodeContext2 **ppCodeContext  
);  
```  
  
```csharp  
int GetUnwindCodeContext(  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppCodeContext`  
 [out] Gibt eine [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Objekt, das Kontext codespeicherort darstellt, wenn eine stapelentladung aufgetreten ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Auch wenn diese Methode einen Codekontext für den Speicherort nach einer stapelentladung zurückgeben kann, bedeutet dies nicht unbedingt, dass der stapelentladung tatsächlich in den aktuellen Stapelrahmen auftreten kann.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)

