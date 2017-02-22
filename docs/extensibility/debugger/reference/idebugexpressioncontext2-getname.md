---
title: "IDebugExpressionContext2::GetName | Microsoft Docs"
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
  - "IDebugExpressionContext2::GetName"
helpviewer_keywords: 
  - "IDebugExpressionContext2::GetName"
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionContext2::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Namen des Auswertungskontexts ab.  
  
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
 \[out\]  Gibt den Namen des Auswertungskontexts zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Name ist die Beschreibung dieses Auswertungs.  Sie ist in der Regel etwas, die von einer Ausdrucksauswertung analysiert werden kann, der den genauen Auswertungs Elementkontext verweist.  In C\+\+ ist der Name folgendermaßen:  
  
```  
"{ function-name, source-file-name, module-file-name }"  
```  
  
## Siehe auch  
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)