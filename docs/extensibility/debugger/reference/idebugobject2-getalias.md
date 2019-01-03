---
title: IDebugObject2::GetAlias | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 756f1249fc2adad9cdfa217c3f8fdd05eaa945d1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889750"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Ruft den Alias, der dieses Objekt zugeordnete ab, sofern vorhanden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetAlias(  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int GetAlias(  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppAlias`  
 [out] Gibt eine [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) Objekt, das den Alias für dieses Objekt darstellt, andernfalls einen null-Wert.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Erstellt ein Alias für ein Objekt durch einen Aufruf der [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)