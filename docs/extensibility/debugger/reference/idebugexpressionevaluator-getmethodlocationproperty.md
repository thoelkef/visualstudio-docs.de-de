---
title: "IDebugExpressionEvaluator::GetMethodLocationProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::GetMethodLocationProperty"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator::GetMethodLocationProperty-Methode"
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluator::GetMethodLocationProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode konvertiert einen Speicherort für Methoden und der Offset in eine Speicheradresse.  
  
## Syntax  
  
```cpp#  
HRESULT GetMethodLocationProperty(   
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```c#  
int GetMethodLocationProperty(  
   string               upstrFullyQualifiedMethodPlusOffset,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### Parameter  
 `upstrFullyQualifiedMethodPlusOffset`  
 \[in\]  Der Speicherort der Methoden und der Offset als Zeichenfolge.  
  
 `pSymbolProvider`  
 \[in\]  Der Anbieter Symbol als [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)\-Objekt.  
  
 `pAddress`  
 \[in\]  Eine Adresse innerhalb der Methode als [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Objekt.  
  
 `pBinder`  
 \[in\]  Der Binder ausgedrückt als [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)\-Objekt.  
  
 `ppProperty`  
 \[out\]  Gibt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)\-Schnittstelle zurück, die die Speicheradresse darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die zurückgegebene Adresse kann verwendet werden, um einen Haltepunkt festzulegen, z.  
  
 Trotz des Namens`upstrFullyQualifiedMethodPlusOffset`, kann diesen Parameter übergebenen ein teilweise qualifizierter Methodenname.  In diesem Fall ist die ausgewählte Methode, die die`pAddress`einschließt.  Wie dieser Parameter interpretiert wird, ist von der Implementierung des Ausdrucksauswerters und der Sprache, die sie unterstützen.  
  
## Siehe auch  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)