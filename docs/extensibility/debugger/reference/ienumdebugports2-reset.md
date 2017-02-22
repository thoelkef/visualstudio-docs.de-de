---
title: "IEnumDebugPorts2::Reset | Microsoft Docs"
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
  - "IEnumDebugPorts2::Reset"
helpviewer_keywords: 
  - "IEnumDebugPorts2::Reset"
ms.assetid: 67da406c-eadb-421e-ae12-e26e9866f262
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPorts2::Reset
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
 Nachdem diese Methode aufgerufen wurde, gibt der nächste Aufruf der [Weiter](../../../extensibility/debugger/reference/ienumdebugports2-next.md)\-Methode das erste Element der Enumeration zurück.  
  
## Siehe auch  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)