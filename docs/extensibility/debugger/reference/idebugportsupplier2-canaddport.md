---
title: "IDebugPortSupplier2::CanAddPort | Microsoft Docs"
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
  - "IDebugPortSupplier2::CanAddPort"
helpviewer_keywords: 
  - "IDebugPortSupplier2::CanAddPort"
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplier2::CanAddPort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Überprüft, ob ein Anschluss lieferant neue Ports hinzufügen kann.  
  
## Syntax  
  
```cpp#  
HRESULT CanAddPort(   
   void   
);  
```  
  
```c#  
int CanAddPort();  
```  
  
## Rückgabewert  
 Wenn der Anschluss hinzugefügt werden kann, gibt `S_OK`zurück. Andernfalls gibt `S_FALSE` zurück, um anzugeben kann keine Ports für diesen Anschlusslieferanten hinzugefügt werden.  
  
## Hinweise  
 Rufen Sie diese Methode auf, bevor Sie die [Port hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)\-Methode aufrufen, da die letzte Methode den Port hinzufügen und ihn erstellen, der ein zeitaufwändiger Vorgang sein kann.  
  
## Siehe auch  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [Port hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)