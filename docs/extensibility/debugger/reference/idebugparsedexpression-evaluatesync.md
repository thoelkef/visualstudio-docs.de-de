---
title: IDebugParsedExpression::EvaluateSync | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b67294b6bb22ff9607be726415b6aae8a2a9524
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115241"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Diese Methode der analysierten Ausdruck ausgewertet und optional wandelt das Ergebnis in einen anderen Datentyp.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EvaluateSync(   
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BSTR                  bstrResultType,  
   IDebugProperty2**     ppResult  
);  
```  
  
```csharp  
int EvaluateSync(  
   uint                 dwEvalFlags,   
   uint                 dwTimeout,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   string               bstrResultType,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwEvalFlags`  
 [in] Eine Kombination von [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) Konstanten, die steuern, wie der Ausdruck ausgewertet wird.  
  
 `dwTimeout`  
 [in] Gibt die maximale Zeit in Millisekunden, bis vor der Rückgabe dieser Methode. Verwendung `INFINITE` zum unendlichen Warten angibt.  
  
 `pSymbolProvider`  
 [in] Die Symbol-Anbieter, ausgedrückt als eine [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) Schnittstelle.  
  
 `pAddress`  
 [in] Der aktuelle Ausführungsort innerhalb einer Methode, ausgedrückt als eine [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Schnittstelle.  
  
 `pBinder`  
 [in] Der Binder, ausgedrückt als eine [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) Schnittstelle.  
  
 `bstrResultType`  
 [in] Der Typ das Ergebnis sollte in umgewandelt werden. Dieses Argument kann es sich um einen null-Wert sein.  
  
 `ppResult`  
 [out] Gibt die [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle, die die Ergebnisse der Auswertung darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Erhält der Auswertungskontext des Ausdrucks von `pAddress`, wodurch es möglich, auf die enthaltende Methode zu ermitteln, und klicken Sie dann den Wert der Symbole im Ausdruck bestimmen Regeln verwenden Sprache Bereichsauswahl.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)