---
title: "IDebugMemoryContext2::Add | Microsoft Docs"
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
  - "IDebugMemoryContext2::Add"
helpviewer_keywords: 
  - "IDebugMemoryContext2::Add-Methode"
  - "Add-Methode"
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMemoryContext2::Add
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Fügt den angegebenen Wert dem aktuellen Kontext hinzu und gibt einen neuen Kontext zurück.  
  
## Syntax  
  
```cpp#  
HRESULT Add(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int Add(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### Parameter  
 `dwCount`  
 \[in\]  Der dem aktuellen Kontext zu addierende Wert.  
  
 `ppMemCxt`  
 \[out\]  Gibt ein neues [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)\-Objekt zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ein Kontext ist eine Adresse des Arbeitsspeichers, daher einen Wert in eine Adresse hinzugefügt werden, erzeugt eine neue Adresse, die eine neue Oberfläche Kontext erfordert.  
  
 Diese Methode muss einen neuen Kontext immer erzeugen, auch wenn die resultierende Adresse außerhalb des Speichers entspricht, der mit diesem Kontext verknüpft ist.  Die einzige Ausnahme liegt vor, wenn kein Arbeitsspeicher für den neuen Kontext zugeordnet werden kann, oder wenn `ppMemCxt` ist ein NULL\-Wert \(der ein Fehler aufgetreten ist\).  
  
## Siehe auch  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)