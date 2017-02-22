---
title: "IDebugProgramPublisher2::SetDebuggerPresent | Microsoft Docs"
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
  - "IDebugProgramPublisher2::SetDebuggerPresent"
helpviewer_keywords: 
  - "IDebugProgramPublisher2::SetDebuggerPresent"
ms.assetid: c88c3ff4-3632-4199-b5de-83c6d21bcf75
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramPublisher2::SetDebuggerPresent
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Teilt dem Herausgeber des Programms an, dass ein Debugger vorhanden und Ausführung ist.  
  
## Syntax  
  
```cpp  
HRESULT SetDebuggerPresent(  
   BOOL fDebuggerPresent  
);  
```  
  
```c#  
int SetDebuggerPresent(  
   int fDebuggerPresent  
);  
```  
  
#### Parameter  
 `fDebuggerPresent`  
 \[in\]  Ein Wert ungleich 0 \(`TRUE`\), wenn ein Debugger vorhanden ist,`FALSE`\(null\), wenn dies nicht der Fall ist.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die Anwesenheit oder Abwesenheit eines Debuggers wird in den Daten wiedergegeben, die [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) von der Methode zurückgegeben wird: Der Wert, der zurückgegeben wird, wird es durch einen früheren Aufruf der `SetDebuggerPresent`\-Methode festgelegt oder gelöscht.  
  
## Siehe auch  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)