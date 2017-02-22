---
title: "IDebugThread2::GetThreadId | Microsoft Docs"
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
  - "IDebugThread2::GetThreadId"
helpviewer_keywords: 
  - "IDebugThread2::GetThreadId"
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugThread2::GetThreadId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Bezeichner für den Thread des Systems ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetThreadId (   
   DWORD* pdwThreadId  
);  
```  
  
```c#  
int GetThreadId (   
   out uint pdwThreadId  
);  
```  
  
#### Parameter  
 `pdwThreadId`  
 \[out\]  Gibt den Thread des Systems Bezeichner zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Eine Thread\-IDs wird verwendet, um einen Thread mit allen anderen Threads in einem Prozess zu identifizieren.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein einfaches `CProgram`\-Objekt implementiert, das die [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)\-Schnittstelle implementiert.  
  
```cpp#  
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {     
   *pdwThreadId = GetCurrentThreadId();    
   return NOERROR;    
}    
```  
  
## Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)