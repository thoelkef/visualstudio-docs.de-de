---
title: IDebugExceptionEvent2::GetException | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
caps.latest.revision: 10
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
ms.openlocfilehash: 5ae6c92b103ce5d37a24425ec080e651a70dece4
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Ruft eine ausführliche Beschreibung der Ausnahme, die dieses Ereignis ausgelöst hat.  
  
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
 [in, out] Ein [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) -Struktur, die mit der Beschreibung der Ausnahme ausgefüllt ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 [Nur C++] Der Aufrufer ist verantwortlich für die Freigabe von Zeichenfolgen in die [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur sowie die Freigabe der [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Objekt in der Struktur.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
