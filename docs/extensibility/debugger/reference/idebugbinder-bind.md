---
title: IDebugBinder::Bind | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 82455db074e23b5ea08010747c80888e4629cf18
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979958"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
Diese Methode ruft den Arbeitsspeicher-Kontext oder das Objekt, das das Symbol für den aktuellen Wert enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Bind(   
   IDebugObject*  pContainer,  
   IDebugField*   pField,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Bind(  
   IDebugObject     pContainer,  
   IDebugField      pField,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pContainer`  
 [in] Die [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , enthält das untergeordnete Element verweist `pField`.  
  
 `pField`  
 [in] Die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , das das Symbol darstellt.  
  
 `ppObject`  
 [out] Gibt die `IDebugObject` , die die Instanz des Symbols darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)