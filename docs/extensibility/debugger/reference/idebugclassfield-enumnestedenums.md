---
title: "IDebugClassField::EnumNestedEnums | Microsoft Docs"
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
  - "IDebugClassField::EnumNestedEnums"
helpviewer_keywords: 
  - "IDebugClassField::EnumNestedEnums-Methode"
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField::EnumNestedEnums
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt einen Enumerator für die geschachtelten Enumeratoren dieser Klasse.  
  
## Syntax  
  
```cpp#  
HRESULT EnumNestedEnums(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumNestedEnums(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parameter  
 `ppEnum`  
 \[out\]  Gibt ein [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)\-Objekt zurück, das die Liste der geschachtelten Enumerationen darstellt.  Gibt einen NULL\-Wert zurück, wenn keine geschachtelten Enumerationen wird.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück oder gibt S\_FALSE zurück, wenn keine geschachtelten Enumeratoren vorhanden ist.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Jedes Element der Enumeration ist ein [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)\-Objekt, das eine geschachtelte Enumeration beschreibt.  
  
 Eine Enumeration, die innerhalb einer Klasse deklariert wird, gilt als eine geschachtelte Enumeration.  Der Code könnte wie folgt lauten:  
  
```  
class RootClass {  
   enum NestedEnum { EnumValue = 0 }  
};  
```  
  
 Die `EnumNestedEnums`\-Methode gibt ein [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)\-Objekt zurückgeben, das ein [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)\-Objekt, das die `NestedEnum`\-Enumeration darstellt.  
  
## Siehe auch  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)