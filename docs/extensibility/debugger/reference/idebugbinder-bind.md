---
title: IDebugBinder::Bind | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c49e4254df9ec06813499237054ec916bb4b6c1b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
Diese Methode ruft die Arbeitsspeicher-Kontext oder ein Objekt, das den aktuellen Symbolwert enthält.  
  
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
 [in] Die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , die das Symbol darstellt.  
  
 `ppObject`  
 [out] Gibt die `IDebugObject` , die die Instanz des Symbols darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)