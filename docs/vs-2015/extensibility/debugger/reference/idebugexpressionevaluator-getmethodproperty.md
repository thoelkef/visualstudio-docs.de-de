---
title: 'Idebugexpressionevaluator:: getmethodproperty | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b84ac959241a8f68f4d9516879660b6414708731
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155362"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode ruft ein Property-Objekt ab, das die lokalen, Argumente und anderen Eigenschaften einer Methode enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 in Der zu verwendende Symbol Anbieter, ausgedrückt als [idebugsymbolprovider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) -Objekt.  
  
 `pAddress`  
 in Die Adresse im Code, ausgedrückt als [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Objekt, das in die nächstgelegene enthaltende Funktion aufgelöst werden soll.  
  
 `pBinder`  
 in Der zu verwendende Binder, ausgedrückt als [idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) -Objekt.  
  
 `fIncludeHiddenLocals`  
 in Ungleich NULL ( `TRUE` ) bedeutet, verborgene lokale Variablen einzuschließen; NULL ( `FALSE` ) bedeutet, dass ausgeblendete lokale Variablen ausgeblendet werden.  
  
 `ppProperty`  
 vorgenommen Gibt ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt zurück, das die Methode darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Verborgene lokale Variablen sind in der Regel Variablen, die vom Compiler generiert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugexpressionevaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [Idebugsymbolprovider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [Idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
