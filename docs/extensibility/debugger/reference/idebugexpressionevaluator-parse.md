---
title: IDebugExpressionEvaluator::Parse | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e64d7419973f0505a2413d7ea56be12a31d01a1c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Diese Methode konvertiert eine Ausdruckszeichenfolge in ein analysierten Ausdrucks.  
  
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
 [in] Die Ausdruckszeichenfolge analysiert werden soll.  
  
 `dwFlags`  
 [in] Eine Auflistung von [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) Konstanten, die bestimmen, wie der Ausdruck analysiert werden.  
  
 `nRadix`  
 [in] Basis für alle numerischen Informationen interpretieren zu verwendende.  
  
 `pbstrError`  
 [out] Gibt den Fehler als einem von Menschen lesbaren Text zurück.  
  
 `pichError`  
 [out] Gibt die Zeichenposition des Beginns des Fehlers in der Zeichenfolge des Ausdrucks zurück.  
  
 `ppParsedExpression`  
 [out] Gibt die analysierten Ausdrucks in einer [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode erzeugt eine analysierten Ausdrucks, nicht auf einen tatsächlichen Wert. Ein analysierter Ausdruck kann ausgewertet werden, d. h. in einen Wert konvertiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)