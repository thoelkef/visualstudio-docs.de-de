---
title: IEnumDebugProcesses2::Reset | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugProcesses2::Reset
helpviewer_keywords:
- IEnumDebugProcesses2::Reset
ms.assetid: 31cbde4f-0bba-497a-9969-d2c342ef4a7b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f8b15c2de8d5c6ae1fc985633c72a1b12cacb0bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31123662"
---
# <a name="ienumdebugprocesses2reset"></a>IEnumDebugProcesses2::Reset
Setzt die Enumeration auf das erste Element zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Nachdem diese Methode wird aufgerufen, den beim nächsten Aufruf der [Weiter](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md) Methode gibt das erste Element der Enumeration.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)