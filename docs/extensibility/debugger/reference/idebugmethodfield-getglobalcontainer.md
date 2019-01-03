---
title: IDebugMethodField::GetGlobalContainer | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c95e6d6f23a0a7be418d3f9fa0710e45d23f3e12
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905980"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
Ruft den globalen Container die Methode ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetGlobalContainer(  
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetGlobalContainer(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppClass`  
 [out] Gibt eine [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) für das Modul, in dem diese Methode definiert ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Das zurückgegebene [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Objekt, das gesamte Modul darstellt, und ist ein künstliches Objekt, das heißt, das Modul selbst verfügt nicht über eine tatsächliche Klasse jedoch kann es durch dargestellt werden ein `IDebugClassField` -Objekt, sodass die verschiedenen die Elemente des Moduls aufgelistet und ermittelt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)