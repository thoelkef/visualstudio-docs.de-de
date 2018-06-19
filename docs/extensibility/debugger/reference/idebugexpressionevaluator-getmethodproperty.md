---
title: IDebugExpressionEvaluator::GetMethodProperty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b5d294e401af09ec3c10fa6dabbb878c661b559e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31111806"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Diese Methode ruft ein Objekt, das die lokalen Variablen, Argumente und andere Eigenschaften einer Methode enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetMethodProperty(   
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BOOL                  fIncludeHiddenLocals,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodProperty(  
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   int                  fIncludeHiddenLocals,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pSymbolProvider`  
 [in] Die Symbol-Anbieter verwendet werden, ausgedrückt als eine [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) Objekt.  
  
 `pAddress`  
 [in] Die Adresse im Code, ausgedrückt als eine [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Funktion-Objekt, das auf die nächste mit aufgelöst werden sollen.  
  
 `pBinder`  
 [in] Der Binder verwendet werden, ausgedrückt als eine [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) Objekt.  
  
 `fIncludeHiddenLocals`  
 [in] Ungleich Null (`TRUE`) bedeutet, dass enthalten ausgeblendete "lokal"; 0 (null) (`FALSE`) bedeutet, dass ausgeblendete "lokal" auslassen  
  
 `ppProperty`  
 [out] Gibt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Objekt, das die Methode darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ausgeblendete "lokal" werden in der Regel Variablen, die vom Compiler generiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)