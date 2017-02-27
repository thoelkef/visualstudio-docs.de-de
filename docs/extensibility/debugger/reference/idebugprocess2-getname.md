---
title: "IDebugProcess2::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetName"
helpviewer_keywords: 
  - "IDebugProcess2::GetName"
ms.assetid: a2f66ab5-53e5-4cdc-a1b5-3b8afa8ee646
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProcess2::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Titel des Anzeigenamens, oder der Dateiname des Prozesses ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetName(   
   GETNAME_TYPE  gnType,  
   BSTR*         pbstrName  
);  
```  
  
```c#  
int GetName(   
   enum_GETNAME_TYPE  gnType,  
   out string         pbstrName  
);  
```  
  
#### Parameter  
 `gnType`  
 \[in\]  Ein Wert aus der [GETNAME\_TYPE](../../../extensibility/debugger/reference/getname-type.md)\-Enumeration, die angibt, welcher Typ des Namens, das zurückgegeben werden soll.  
  
 `pbstrName`  
 \[out\]  Gibt den Namen des Prozesses zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [GETNAME\_TYPE](../../../extensibility/debugger/reference/getname-type.md)