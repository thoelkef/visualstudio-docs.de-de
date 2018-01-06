---
title: IDebugDisassemblyStream2::Read | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDisassemblyStream2::Read
helpviewer_keywords: IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: edc41da40c4f0c292523ed338419fbc4a7253dcf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Liest die Anweisungen, die von der aktuellen Position im Disassemblyfenster Datenstrom ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```csharp  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwInstructions`  
 [in] Die Anzahl der Anweisungen, die disassembliert werden soll. Dieser Wert ist auch die maximale Länge von der `prgDisassembly` Array.  
  
 `dwFields`  
 [in] Eine Kombination aus Flags aus der [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) Enumeration, die angeben, welche Felder der `prgDisassembly` sind ausgefüllt werden.  
  
 `pdwInstructionsRead`  
 [out] Gibt die Anzahl der Anweisungen tatsächlich disassembliert.  
  
 `prgDisassembly`  
 [out] Ein Array von [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Strukturen, die mit den disassemblierten Code, einer Struktur pro disassemblierten Anweisung ausgefüllt ist. Die Länge dieses Arrays wird vorgegeben, durch die `dwInstructions` Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die maximale Anzahl von Anweisungen, die im aktuellen Bereich verfügbar sind, erhalten Sie durch Aufrufen der [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) Methode.  
  
 Die aktuelle Position, in dem die nächste Anweisung wird aus der gelesen, kann geändert werden, durch Aufrufen der [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) Methode.  
  
 Die `DSF_OPERANDS_SYMBOLS` Flag hinzugefügt werden können die `DSF_OPERANDS` -flag in der `dwFields` Parameter, um anzugeben, dass Anweisungen Disassemblierung Symbolnamen verwendet werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)