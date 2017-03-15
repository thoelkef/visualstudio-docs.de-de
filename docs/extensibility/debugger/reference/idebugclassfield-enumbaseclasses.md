---
title: "IDebugClassField::EnumBaseClasses | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumBaseClasses"
helpviewer_keywords: 
  - "IDebugClassField::EnumBaseClasses-Methode"
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::EnumBaseClasses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt einen Enumerator für die Basisklasse dieser Klasse.  
  
## Syntax  
  
```cpp#  
HRESULT EnumBaseClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumBaseClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parameter  
 `ppEnum`  
 \[out\]  Gibt ein [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)\-Objekt zurück, das die Liste der Basisklassen darstellt.  Gibt einen NULL\-Wert zurück, wenn keine Basisklassen vorhanden ist.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurückgibt, S\_SH\_NO\_BASE\_CLASSES zurück, wenn keine Basisklassen vorhanden ist \(und den `ppEnum`\-Parameter wird auf einen NULL\-Wert festgelegt\). andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die Basisklassen im Enumeratorobjekt werden in der Reihenfolge der unmittelbarsten \(oder die meisten abgeleitete\) Basisklasse in die Remotsten Basisklasse angegeben.  Beispielsweise die C\+\+\-Klassen:  
  
```  
class Root { }  
class Level1 : Root { }  
class Level2 : Level1 { }  
class MyClass : Level2 { }  
```  
  
 Die Enumeration ist die Basisklasse in der Reihenfolge `Level2`, `Level1`, `Root`zurückgeben.  
  
## Siehe auch  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)