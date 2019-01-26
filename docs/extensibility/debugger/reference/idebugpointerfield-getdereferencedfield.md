---
title: IDebugPointerField::GetDereferencedField | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74c3853389f52253b4aa62547c8a0b89a36d03e6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962718"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Diese Methode gibt den Typ des Objekts, die auf den dieser Zeiger-Objekt verweist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetDereferencedField(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetDereferencedField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppField`  
 [out] Gibt eine [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) beschreibt den Typ des Zielobjekts.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn z. B. die [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) -Objekt verweist auf eine ganze Zahl, die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) von dieser Methode zurückgegebene Typ beschreibt, Integer-Datentyp.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)