---
title: IDebugObject::IsProxy | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugObject::IsProxy
- IsProxy
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b32fcff6a365f37c926194560674da354f0f08ee
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54918718"
---
# <a name="idebugobjectisproxy"></a>IDebugObject::IsProxy
Bestimmt, ob das Objekt über einen transparenten Proxy ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT IsProxy (  
   BOOL* pfIsProxy  
);  
```  
  
```csharp  
int IsProxy (  
   out bool pfIsProxy  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pfIsProxy`  
 [out] `TRUE` ist das Objekt einen transparenten Proxy ist; andernfalls `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird von der standardmäßigen C++-Debug-Engine implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)