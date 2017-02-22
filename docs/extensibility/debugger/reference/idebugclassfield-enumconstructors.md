---
title: "IDebugClassField::EnumConstructors | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumConstructors"
helpviewer_keywords: 
  - "IDebugClassField::EnumConstructors-Methode"
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField::EnumConstructors
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt einen Enumerator für die Konstruktoren für diese Klasse.  
  
## Syntax  
  
```cpp#  
HRESULT EnumConstructors(   
   CONSTRUCTOR_ENUM   cMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumConstructors(  
   CONSTRUCTOR_ENUM     cMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parameter  
 `cMatch`  
 \[in\]  Ein Wert aus der [CONSTRUCTOR\_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)\-Enumeration, der den Typ von Konstruktoren für die Enumeration angibt.  
  
 `ppEnum`  
 \[out\]  Gibt ein [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)\-Objekt zurück, das die Liste von Konstruktoren darstellt.  Gibt einen NULL\-Wert zurück, wenn keine Konstruktoren vorhanden ist.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück oder gibt S\_FALSE zurück, wenn keine Konstruktoren vorhanden ist.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Jedes Element der Enumeration ist ein [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)\-Objekt, das eine Konstruktormethode beschreibt.  
  
 Die Liste von Konstruktoren in der Regel umfasst nicht die Standardkonstruktoren, die von einem Compiler angegeben werden.  
  
## Siehe auch  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [CONSTRUCTOR\_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)