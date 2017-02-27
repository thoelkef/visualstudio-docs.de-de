---
title: "IDebugClassField::GetEnclosingClass | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::GetEnclosingClass"
helpviewer_keywords: 
  - "IDebugClassField::GetEnclosingClass-Methode"
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Klasse ab, die diese Klasse enthalten ist.  
  
## Syntax  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```c#  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### Parameter  
 `ppClassField`  
 \[out\]  Gibt ein [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)\-Objekt zurück, das die einschließende Klasse darstellt.  Gibt einen NULL\-Wert zurück, wenn kein einschließende Klasse gibt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Wenn die Klasse, die durch dieses Objekt dargestellt wird, [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) einer geschachtelten Klasse ist, gibt der `ppClassField`\-Parameter ein `IDebugClassField`\-Objekt zurück, das die einschließende Klasse darstellt.  Beispielsweise diese Klassendefinition:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Die `GetEnclosingClass`\-Methode für das Aufrufen `IDebugClassField`\-Objekt, das die Klasse darstellt, `NestedClass``IDebugClassField` gibt ein Objekt zurück, das die Klasse `RootClass`darstellt.  
  
## Siehe auch  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)