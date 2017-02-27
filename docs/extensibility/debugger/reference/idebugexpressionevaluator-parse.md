---
title: "IDebugExpressionEvaluator::Parse | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::Parse"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator::Parse-Methode"
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugExpressionEvaluator::Parse
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode konvertiert eine Ausdruckszeichenfolge auf einen analysierten Ausdruck.  
  
## Syntax  
  
```cpp#  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```c#  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### Parameter  
 `upstrExpression`  
 \[in\]  Die zu analysierende Ausdruckszeichenfolge.  
  
 `dwFlags`  
 \[in\]  Eine Auflistung [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) Konstanten, die bestimmen, wie der Ausdruck analysiert werden soll.  
  
 `nRadix`  
 \[in\]  Informationen zum Interpretieren eines numerischen Basis verwendet werden soll.  
  
 `pbstrError`  
 \[out\]  Gibt den Fehler als Nur\-Text zurück.  
  
 `pichError`  
 \[out\]  Gibt die Zeichenposition des Anfangs des Fehlers in der Ausdruckszeichenfolge zurück.  
  
 `ppParsedExpression`  
 \[out\]  Gibt den analysierten Ausdruck in einem [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)\-Objekt zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode erzeugt einen analysierten Ausdruck keinen Wert.  Ein analysierter Ausdruck kann jetzt ausgewertet werden, d. h. in einen Wert konvertiert.  
  
## Siehe auch  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)