---
title: IDebugExceptionEvent2::GetException | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b4c62a12c54a716a02146190b91f1f95365333b9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917127"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Ruft eine ausführliche Beschreibung der Ausnahme, die dieses Ereignis ausgelöst wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetException(   
   EXCEPTION_INFO* pExceptionInfo  
);  
```  
  
```csharp  
int GetException(   
   EXCEPTION_INFO[] pExceptionInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pExceptionInfo`  
 [in, out] Ein [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) -Struktur, die mit der Beschreibung der Ausnahme gefüllt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 [Nur für C++] Der Aufrufer ist verantwortlich für das Freigeben von Zeichenfolgen in die [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur sowie die Freigabe der [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Objekt in der Struktur.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)