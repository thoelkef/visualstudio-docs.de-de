---
title: IDebugPointerField::GetDereferencedField | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 77af1428dbdd0ea9f84000bda34ea8608b17cc24
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Diese Methode gibt den Typ des Objekts, auf den dieser Zeiger-Objekt verweist.  
  
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
 [out] Gibt eine [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) beschreiben den Typ des Zielobjekts.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn z. B. die [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) -Objekt verweist auf eine ganze Zahl, die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) von dieser Methode zurückgegebene Typ beschreibt diese Integer-Datentyp.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)