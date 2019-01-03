---
title: IDebugPropertyField::GetPropertySetter | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPropertyField::GetPropertySetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertySetter method
ms.assetid: 744d76fd-2bcc-4917-a040-ce4cc714ef61
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7bf68cd07a2952d421010a75255b1e6261a2220e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53907747"
---
# <a name="idebugpropertyfieldgetpropertysetter"></a>IDebugPropertyField::GetPropertySetter
Ruft die Methode ab, die die Eigenschaft festlegt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetPropertySetter(   
   IDebugMethodField** ppField  
);  
```  
  
```csharp  
int GetPropertySetter(  
   out IDebugMethodField ppField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppField`  
 [out] Gibt eine [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) Objekt, das die Methode, die die Eigenschaft festlegt darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Rufen Sie zum Abrufen der Methode, die die Eigenschaft ruft die [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)