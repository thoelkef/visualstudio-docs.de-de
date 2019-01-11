---
title: IDebugExpressionEvaluator::Parse | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ebd8518a6fd2048de0d5204dcede8943f4da62e1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922180"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Diese Methode konvertiert eine Ausdruckszeichenfolge in einen analysierten Ausdruck.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```csharp  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `upstrExpression`  
 [in] Die Ausdruckszeichenfolge analysiert werden.  
  
 `dwFlags`  
 [in] Eine Auflistung von [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) Konstanten, die bestimmen, wie der Ausdruck ist, die analysiert werden.  
  
 `nRadix`  
 [in] Die Basis, die verwendet werden, um alle numerischen Informationen interpretieren.  
  
 `pbstrError`  
 [out] Gibt den Fehler als Klartext zurück.  
  
 `pichError`  
 [out] Gibt die Zeichenposition des Starts des Fehlers in der Ausdruckszeichenfolge zurück.  
  
 `ppParsedExpression`  
 [out] Gibt den analysierten Ausdruck in einem [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode erzeugt einen analysierten Ausdruck, der nicht auf einen tatsächlichen Wert. Ein analysierten Ausdruck kann ausgewertet werden, d. h. in einen Wert konvertiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)