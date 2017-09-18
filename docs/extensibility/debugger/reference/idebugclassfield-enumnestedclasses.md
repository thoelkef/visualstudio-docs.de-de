---
title: "IDebugClassField::EnumNestedClasses | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumNestedClasses"
helpviewer_keywords: 
  - "IDebugClassField::EnumNestedClasses-Methode"
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::EnumNestedClasses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt einen Enumerator für Klassen, die in dieser Klasse geschachtelt werden.  
  
## Syntax  
  
```cpp#  
HRESULT EnumNestedClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumNestedClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parameter  
 `ppEnum`  
 \[out\]  Gibt ein [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)\-Objekt zurück, das die Liste der geschachtelten Klasse darstellt.  Gibt einen NULL\-Wert zurück, wenn keine geschachtelten Klassen gibt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück oder gibt S\_FALSE zurück, wenn keine geschachtelten Klassen gibt.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Jedes Element der Enumeration ist ein [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)\-Objekt, das eine geschachtelte Klasse beschreibt.  
  
 Eine geschachtelte Klasse ist eine Klasse, die innerhalb einer anderen Klasse definiert ist.  Beispiele:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Die [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)\-Enumeration ist ein Objekt, das die `NestedClass`\-Klasse darstellt.  
  
## Siehe auch  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)