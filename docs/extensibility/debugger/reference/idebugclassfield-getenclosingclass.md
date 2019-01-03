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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4cf74c5fd53d3ad75c9fc95e8217c849e3ce550c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53851481"
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