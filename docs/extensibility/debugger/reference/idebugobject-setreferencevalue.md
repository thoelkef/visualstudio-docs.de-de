---
title: IDebugObject::SetReferenceValue | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b597d7a62880e00a570a1971a6fec2becaaddca
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908625"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Legt den Verweiswert, der dieses Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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