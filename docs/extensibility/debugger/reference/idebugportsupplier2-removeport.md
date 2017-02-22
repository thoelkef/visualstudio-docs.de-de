---
title: "IDebugPortSupplier2::RemovePort | Microsoft Docs"
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
  - "IDebugPortSupplier2::RemovePort"
helpviewer_keywords: 
  - "IDebugPortSupplier2::RemovePort"
ms.assetid: f5c1fbf2-9084-46f2-a682-7db963928df2
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplier2::RemovePort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Entfernt einen Anschluss.  
  
## Syntax  
  
```cpp#  
HRESULT RemovePort(   
   IDebugPort2* pPort  
);  
```  
  
```c#  
int RemovePort(   
   IDebugPort2 pPort  
);  
```  
  
#### Parameter  
 `pPort`  
 \[in\]  Ein [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)\-Objekt, das den Anschluss darstellt, das entfernt werden soll.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode entfernt den Port von der internen Liste des Anschlusslieferanten aktiver Ports.  
  
## Siehe auch  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)