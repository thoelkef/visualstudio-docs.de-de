---
title: IDebugExceptionEvent2::PassToDebuggee | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce8e6b53a07f191d967bbd676e6fcfc96b53dc14
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113304"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Gibt an, ob die Ausnahme übergeben werden soll, das Programm, das gerade gedebuggt wird, wenn die Ausführung fortsetzt, oder wenn die Ausnahme verworfen werden sollen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `fPass`  
 [in] Ungleich Null (`TRUE`), wenn die Ausnahme übergeben werden soll, das Programm, das gerade gedebuggt wird, wenn die Ausführung fortsetzt, oder 0 (null) (`FALSE`), wenn die Ausnahme verworfen werden sollen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Beim Aufrufen dieser Methode bewirkt nicht tatsächlich von Code im zu debuggenden Programms ausgeführt werden. Der Aufruf ist lediglich zum Festlegen des Status für die nächste Ausführung des Codes. Z. B. Aufrufe von der [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) Methode gelegten `S_OK` mit der [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` -Feld festgelegt, sodass `EXCEPTION_STOP_SECOND_CHANCE`.  
  
 Die IDE möglicherweise die [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) Ereignis, und rufen die [Fortfahren](../../../extensibility/debugger/reference/idebugprogram2-continue.md) Methode. Debugging-Modul (DE), müsste ein Standardverhalten zum Behandeln der Fall, wenn die `PassToDebuggee` Methode wird nicht aufgerufen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)