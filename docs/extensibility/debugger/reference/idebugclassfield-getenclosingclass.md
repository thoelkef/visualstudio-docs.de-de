---
title: IDebugClassField::GetEnclosingClass | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37dcb0eb23cf216b604d927309cd395252d59792
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040865"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Ruft die Klasse, die diese Klasse umschließt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppClassField`  
 [out] Gibt eine [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Objekt darstellt, der einschließenden Klasse. Gibt einen null-Wert zurück, wenn keine einschließenden Klasse vorhanden ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die Klasse von diesem dargestellt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Objekt ist eine geschachtelte Klasse, die `ppClassField` gibt Parameter ein `IDebugClassField` Objekt darstellt, der einschließenden Klasse. Angenommen, dieser Klassendefinition:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Aufrufen der `GetEnclosingClass` Methode für die `IDebugClassField` Objekt darstellt der `NestedClass` -Klasse zurückgegeben wird ein `IDebugClassField` Objekt, das die Klasse darstellt `RootClass`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)