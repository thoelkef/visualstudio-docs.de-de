---
title: "IDebugDisassemblyStream2::Read | Microsoft Docs"
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
  - "IDebugDisassemblyStream2::Read"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::Read"
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDisassemblyStream2::Read
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Liest die Anweisungen, die von der aktuellen Position im Disassemblys datenstrom.  
  
## Syntax  
  
```cpp#  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```c#  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### Parameter  
 `dwInstructions`  
 \[in\]  Die Anzahl der Anweisungen zu disassemblieren.  Dieser Wert ist auch die maximale Länge des Arrays. `prgDisassembly`  
  
 `dwFields`  
 \[in\]  Eine Kombination von Flags aus der [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)\-Enumeration, die angeben, welche Felder aus `prgDisassembly` ergänzt werden sollen.  
  
 `pdwInstructionsRead`  
 \[out\]  Gibt die Anzahl der tatsächlich disassemblierten Anweisungen zurück.  
  
 `prgDisassembly`  
 \[out\]  Ein Array [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Strukturen, das dem disassemblierten Code gefüllt wird, eine Struktur pro disassemblierte Anweisung.  Die Länge dieses Arrays wird durch den Parameter `dwInstructions` vorgeschrieben.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die maximale Anzahl von Anweisungen, die im aktuellen Bereich verfügbar sind, kann abgerufen werden, indem die [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)\-Methode aufruft.  
  
 Die aktuelle Position, an der die nächste Anweisung gelesen wird, kann geändert werden, indem die [Suchen](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)\-Methode aufruft.  
  
 Das `DSF_OPERANDS_SYMBOLS`\-Flag kann dem Flag im `dwFields``DSF_OPERANDS`\-Parameter hinzugefügt werden, um anzugeben, dass Symboltitel verwendet werden sollten, sofern ein solcher Anweisungen disassembliert.  
  
## Siehe auch  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [Suchen](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)