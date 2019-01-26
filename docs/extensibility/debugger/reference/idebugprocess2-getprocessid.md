---
title: IDebugProcess2::GetProcessId | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::GetProcessId
helpviewer_keywords:
- IDebugProcess2::GetProcessId
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3f3e5632f7b59b355c4cd76f76479d21e232780
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954643"
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
Ruft die GUID für diesen Prozess ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetProcessId(  
   GUID* pguidProcessId  
);  
```  
  
```csharp  
int GetProcessId(  
   out Guid pguidProcessId  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pguidProcessId`  
 [out] Gibt die GUID für diesen Prozess zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die GUID (GLOBALLY Unique IDentifier) identifiziert, diesen Prozess für alle anderen Prozesse im System ausgeführt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)