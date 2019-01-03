---
title: IDebugPortEx2::CanTerminateProcess | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2::CanTerminateProcess
helpviewer_keywords:
- IDebugPortEx2::CanTerminateProcess
ms.assetid: 111f65d8-5a1a-42b3-9de3-dd9bb03a33fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ce0e2941c964a578a26328a028d880658e45ea5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900424"
---
# <a name="idebugportex2canterminateprocess"></a>IDebugPortEx2::CanTerminateProcess
Bestimmt, ob ein Prozess beendet werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CanTerminateProcess(   
   IDebugProcess2* pPortProcess  
);  
```  
  
```csharp  
HRESULT CanTerminateProcess(   
   IDebugProcess2 pPortProcess  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pPortProcess`  
 [in] Ein [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) Objekt, durch die der Prozess beendet wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` , wenn der Prozess beendet werden kann; andernfalls `S_FALSE`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)