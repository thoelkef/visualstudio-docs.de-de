---
title: IDebugObject::SetReferenceValue | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b1da0e152d536e9bed47dfb3964df60634c017bc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180505"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Legt den Verweiswert, der dieses Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT SetReferenceValue(   
   IDebugObject* pObject  
);  
```  
  
```csharp  
int SetReferenceValue(  
   [In] IDebugObject pObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pObject`  
 [in] Ein [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekt, das den neuen Verweiswert darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Auf diese Weise wird dies [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) einen Verweis auf den Wert des Objekts im angegebenen Objekt der `pObject` wegwirft alle vorherigen Verweis-Parameter. Beachten Sie, das von diesem `IDebugObject` Objekt muss bereits ein Verweistyp sein.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
