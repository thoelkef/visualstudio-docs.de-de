---
title: IDebugThread2::Suspend | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 3926456c8b625102dfc5df4d8818f3cacc3a2ce3
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Unterbricht einen Thread.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Suspend (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
HRESULT Suspend (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwSuspendCount`  
 [out] Gibt den Unterbrechungszähler nach dem Vorgang "Anhalten" zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Jeder Aufruf dieser Methode wird den Unterbrechungszähler über 0 erhöht. Diese Unterbrechungszähler wird angezeigt, der **Threads** Debug-Fenster.  
  
 Für jeden Aufruf dieser Methode muss ein späteren Aufruf der [fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)
