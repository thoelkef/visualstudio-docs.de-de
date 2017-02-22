---
title: "IEnumDebugCodeContexts2::Reset | Microsoft Docs"
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
  - "IEnumDebugCodeContexts2::Reset"
helpviewer_keywords: 
  - "IEnumDebugCodeContexts2::Reset"
ms.assetid: df6cf1e3-2ef8-4d38-81a0-8e9adf151884
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugCodeContexts2::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Setzt die Enumeration auf das erste Element zurück.  
  
## Syntax  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```c#  
int Reset();  
```  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Nachdem diese Methode aufgerufen wurde, gibt der nächste Aufruf der [Weiter](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)\-Methode das erste Element der Enumeration zurück.  
  
## Siehe auch  
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)