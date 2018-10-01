---
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie | Microsoft-Dokumentation
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
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 10496d6e371d32fe4ee76ae6c3360e228053b43d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514120"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2-getinterceptcookie).  
  
Wird aufgerufen, wenn die Verarbeitung einer abgefangenen Ausnahme abgeschlossen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetInterceptCookie(  
   UINT64* pqwCookie  
);  
```  
  
```csharp  
int GetInterceptCookie(  
   out ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pqwCookie`  
 [out] Eindeutiger Wert, der der Ausnahme zugeordnet ist, die abgefangen wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls den Fehlercode zurück.  
  
## <a name="remarks"></a>Hinweise  
 Nach der [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) -Methode behandeln einer abgefangenen Ausnahme abgeschlossen wurde, sendet er die [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) Ereignis. Der Handler können die `GetInterceptCookie` Methode, um den eindeutigen Wert, der der Ausnahme zugeordnete abzurufen (den gleichen Wert, der zum Übergeben der `InterceptCurrentException` Methode).  
  
## <a name="see-also"></a>Siehe auch  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)

