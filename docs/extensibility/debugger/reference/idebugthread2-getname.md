---
title: "IDebugThread2::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::GetName"
helpviewer_keywords: 
  - "IDebugThread2::GetName"
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Namen eines Threads ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetName (   
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetName (   
   out string pbstrName  
);  
```  
  
#### Parameter  
 `pbstrName`  
 \[out\]  Gibt den Namen des Threads zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der abgerufene Name lautet immer ein Name, der angezeigt werden kann und der Titel beschreibt den Thread.  Der Name der Thread möglicherweise von einer Architektur der Laufzeit abgeleitet, die benannte Threads unterstützt, oder es könnte ein Name, der im Debug\- Modul abgeleitet ist.  Alternativ kann der Name des Threads durch einen Aufruf der [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)\-Methode festgelegt werden.  
  
## Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)