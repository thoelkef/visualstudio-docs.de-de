---
title: "IDebugProcessEx2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcessEx2::Attach"
helpviewer_keywords: 
  - "IDebugProcessEx2::Attach-Methode"
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugProcessEx2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode informiert den Prozess, dass eine Sitzung jetzt den Prozess gedebuggt wird.  
  
## Syntax  
  
```cpp#  
HRESULT Attach(   
   IDebugSession2* pSession  
);  
```  
  
```c#  
int Attach(  
   IDebugSession2 pSession  
);  
```  
  
#### Parameter  
 `pSession`  
 \[in\]  Ein Wert, der die Sitzung eindeutig identifiziert wird, die an diesen Prozess anfügt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die Schnittstelle, die in `pSession` übergeben wird, soll nur als Cookie behandelt werden, ein Wert, der den Debug\- Manager der Sitzung eindeutig identifiziert, der an diesen Prozess anfügt. Keine Methoden für die angegebene Schnittstelle sind aktiviert.  
  
## Siehe auch  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)