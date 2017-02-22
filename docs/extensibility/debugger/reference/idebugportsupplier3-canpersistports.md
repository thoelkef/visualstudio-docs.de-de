---
title: "IDebugPortSupplier3::CanPersistPorts | Microsoft Docs"
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
  - "IDebugPortSupplier3::CanPersistPorts"
helpviewer_keywords: 
  - "IDebugPortSupplier3::CanPersistPorts"
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode bestimmt, ob der Port lieferant Ports \(indem sie auf einen Datenträger geschrieben\) zwischen den Aufrufen des Debuggers beibehalten kann.  
  
## Syntax  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```c#  
int CanPersistPorts();  
```  
  
#### Parameter  
 Keine.  
  
## Rückgabewert  
 `S_OK` beibehalten werden können, wenn Ports oder `S_FALSE` anzugeben, dass Ports nicht beibehalten werden können.  
  
## Hinweise  
 Wenn der Anschluss lieferant Ports beibehalten kann, muss er so vorgehen, wenn er erneut zu laden und sie anschließend zerstört wird, wenn er noch einmal instanziiert wird.  
  
## Siehe auch  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)