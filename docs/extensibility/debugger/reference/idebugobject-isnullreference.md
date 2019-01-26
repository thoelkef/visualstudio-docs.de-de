---
title: IDebugObject::IsNullReference | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 021d7d8b7c1203aab68a93efe8581f66dec698f9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975269"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Testet, ob dieses Objekt ein null-Verweis ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```csharp  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pfIsNull`  
 [out] Ungleich NULL zurück (`TRUE`) Wenn dieses Objekt ein null-Verweis; andernfalls wird NULL (`FALSE`).  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein null-Verweis bedeutet, dass ein leeres Objekt oder ein Objekt, das nicht zugewiesen wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)