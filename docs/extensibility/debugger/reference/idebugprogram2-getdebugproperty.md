---
title: "IDebugProgram2::GetDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetDebugProperty"
helpviewer_keywords: 
  - "IDebugProgram2::GetDebugProperty"
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Eigenschaften des Programms ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```c#  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### Parameter  
 `ppProperty`  
 \[out\]  Gibt ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)\-Objekt zurück, das die Eigenschaften des Programms darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die Eigenschaften, die von dieser Methode zurückgegeben werden, sind für das Programm bestimmt.  Wenn das Programm mehr als eine Eigenschaft zurückgeben muss, ist das [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) von dieser Methode zurückgegebene Objekt ein Container für zusätzliche Eigenschaften und [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) Aufruf gibt eine Liste aller Eigenschaften zurück.  
  
 Ein Programm kann beliebig viele macht zusätzliche Typ und Eigenschaften, die von der `IDebugProperty2`\-Schnittstelle beschrieben werden können.  Ein IDE werden möglicherweise zusätzliche Eigenschaften Programm durch eine generische Benutzeroberfläche Eigenschaftenbrowser angezeigt.  
  
## Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)