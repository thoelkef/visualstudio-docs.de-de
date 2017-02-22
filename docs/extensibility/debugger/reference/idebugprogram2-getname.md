---
title: "IDebugProgram2::GetName | Microsoft Docs"
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
  - "IDebugProgram2::GetName"
helpviewer_keywords: 
  - "IDebugProgram2::GetName"
ms.assetid: a54cbf13-b3e3-4c9f-8b8d-13573232dfb0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Namen des Programms ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetName(   
   out string pbstrName  
);  
```  
  
#### Parameter  
 `pbstrName`  
 \[out\]  Gibt den Namen des Programms zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Name, der von dieser Methode zurückgegeben wird, ist immer ein benutzerfreundlicher, USER\-anzeigbarer Name, durch den das Programm beschreibt.  
  
## Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)