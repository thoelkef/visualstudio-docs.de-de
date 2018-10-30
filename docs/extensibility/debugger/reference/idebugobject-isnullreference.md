---
title: IDebugObject::IsNullReference | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d6b5108d9fd830c047c020d4b3adab2526854e6c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939695"
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