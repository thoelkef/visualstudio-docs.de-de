---
title: "IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetPhysicalStackRange"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetPhysicalStackRange"
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetPhysicalStackRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine Darstellung des abhängigen MACHINE des Bereichs der physikalischen Adressen ab, die einem Stapelrahmen zugeordnet sind.  
  
## Syntax  
  
```cpp#  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```c#  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### Parameter  
 `paddrMin`  
 \[out\]  Gibt die niedrigste physische Adresse zurück, die diesem Stapelrahmen zugeordnet ist.  
  
 `paddrMax`  
 \[out\]  Gibt die höchste physische Adresse zurück, die diesem Stapelrahmen zugeordnet ist.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die Informationen, die von dieser Methode zurückgegeben werden, werden vom Manager der Sitzung \(SDM Debuggen\) im Stapelrahmen zu sortieren.  
  
 Es wird davon ausgegangen, dass die Aufrufliste unten wächst das heißt dass neue Stapelrahmen an den in zunehmendem Maße unteren Speicherorte hinzugefügt werden.  Eine Architektur der Laufzeit muss physischen Stapel Bereiche bereitstellen, die diese Annahme übereinstimmen.  
  
## Siehe auch  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)