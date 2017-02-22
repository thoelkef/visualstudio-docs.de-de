---
title: "IDebugProcessEx2::Detach | Microsoft Docs"
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
  - "IDebugProcessEx2::Detach"
helpviewer_keywords: 
  - "IDebugProcessEx2::Detach-Methode"
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessEx2::Detach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode informiert den Prozess, dass eine Sitzung nicht mehr den Prozess gedebuggt wird.  
  
## Syntax  
  
```cpp#  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```c#  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### Parameter  
 `pSession`  
 \[in\]  Ein Wert, mit dem die Sitzung eindeutig identifiziert, um diesen Prozess zu trennen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die Schnittstelle, die in `pSession` übergeben wird, soll nur als Cookie behandelt werden, ein Wert, der den Debug\- Manager der Sitzung eindeutig identifiziert, der ursprünglich an diesen Prozess angefügt haben. Keine Methoden für die angegebene Schnittstelle sind aktiviert.  
  
## Siehe auch  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)