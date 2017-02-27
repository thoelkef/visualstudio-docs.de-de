---
title: "IDebugMethodField::GetGlobalContainer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::GetGlobalContainer"
helpviewer_keywords: 
  - "IDebugMethodField::GetGlobalContainer-Methode"
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::GetGlobalContainer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den globalen Container der Methode ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetGlobalContainer(  
   IDebugClassField** ppClass  
);  
```  
  
```c#  
int GetGlobalContainer(  
   out IDebugClassField ppClass  
);  
```  
  
#### Parameter  
 `ppClass`  
 \[out\]  Gibt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) zurück, das das Modul darstellt, in dem diese Methode definiert ist.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Das zurückgegebene Objekt stellt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) das gesamte Modul dar und stellt ein Objekt künstliches, d.h., hat das Modul selbst keine tatsächliche Klasse, kann jedoch durch ein `IDebugClassField`\-Objekt dargestellt werden und die verschiedenen Elemente aufgelistet und ermittelt worden Moduls kann.  
  
## Siehe auch  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)