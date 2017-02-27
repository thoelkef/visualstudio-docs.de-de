---
title: "IDebugExpressionEvaluator::GetMethodProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::GetMethodProperty"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator::GetMethodProperty-Methode"
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluator::GetMethodProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft ein Eigenschaftenobjekt ab, das die lokalen Variablen, Argumente und andere Eigenschaften einer Methode enthält.  
  
## Syntax  
  
```cpp#  
HRESULT GetMethodProperty(   
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BOOL                  fIncludeHiddenLocals,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```c#  
int GetMethodProperty(  
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   int                  fIncludeHiddenLocals,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### Parameter  
 `pSymbolProvider`  
 \[in\]  Der zu verwendende Symbol für, ausgedrückt als wurde [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)\-Objekt.  
  
 `pAddress`  
 \[in\]  Die Adresse in Code ausgedrückt als [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Objekt, das zur nächsten enthaltenden Funktion aufgelöst werden soll.  
  
 `pBinder`  
 \[in\]  Der zu verwendende Binder, ausgedrückt als wurde [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)\-Objekt.  
  
 `fIncludeHiddenLocals`  
 \[in\]  Ein Wert ungleich 0 \(`TRUE`\) bedeutet, ausgeblendete lokale Variablen einschließen.`FALSE`\(null\) bedeutet, ausgeblendete Lokal zu  
  
 `ppProperty`  
 \[out\]  Gibt ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)\-Objekt zurück, das die Methode darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ausgeblendete lokale Variablen sind in der Regel Variablen, die vom Compiler generiert werden.  
  
## Siehe auch  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)