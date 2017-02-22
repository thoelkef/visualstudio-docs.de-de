---
title: "IDebugMemoryContext2::Subtract | Microsoft Docs"
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
  - "IDebugMemoryContext2::Subtract"
helpviewer_keywords: 
  - "Subtrahieren-Methode"
  - "IDebugMemoryContext2::Subtract-Methode"
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMemoryContext2::Subtract
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Subtrahiert den angegebenen Wert aus dem aktuellen Kontext und gibt einen neuen Kontext zurück.  
  
## Syntax  
  
```cpp#  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### Parameter  
 `dwCount`  
 \[in\]  Die Anzahl von Bytes des Arbeitsspeichers dekrementiert werden soll.  
  
 `ppMemCxt`  
 \[out\]  Gibt ein neues [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)\-Objekt zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ein Kontext ist eine Adresse des Arbeitsspeichers, daher einen Wert aus einer Adresse, Dienstes wird eine neue Adresse, die eine neue Oberfläche Kontext erfordert.  
  
 Diese Methode muss einen neuen Kontext immer erzeugen, auch wenn die resultierende Adresse außerhalb des Speichers entspricht, der mit diesem Kontext verknüpft ist.  Die einzige Ausnahme liegt vor, wenn kein Arbeitsspeicher für den neuen Kontext zugeordnet werden kann, oder wenn `ppMemCxt` ist ein NULL\-Wert \(der ein Fehler aufgetreten ist\).  
  
## Siehe auch  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)