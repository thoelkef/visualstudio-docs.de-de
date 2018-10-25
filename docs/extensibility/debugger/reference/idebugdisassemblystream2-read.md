---
title: IDebugDisassemblyStream2::Read | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5e59ea6c5ab01485b3c022f0504aeae55c3882a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902631"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Liest die Anleitung beginnend mit der aktuellen Position im Stream Disassembly.  
  
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
 [in] Die Anzahl der Anweisungen zum disassemblieren. Dieser Wert ist auch die maximale Länge von der `prgDisassembly` Array.  
  
 `dwFields`  
 [in] Eine Kombination von Flags aus der [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) Enumeration, die angeben, welche Felder der `prgDisassembly` ausgefüllt werden müssen.  
  
 `pdwInstructionsRead`  
 [out] Gibt die Anzahl von Anweisungen, die tatsächlich disassembliert.  
  
 `prgDisassembly`  
 [out] Ein Array von [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Strukturen, die mit der disassemblierte Code, eine Struktur pro disassemblierten Anweisung gefüllt wird. Die Länge dieses Arrays hängt von der `dwInstructions` Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die maximale Anzahl von Anweisungen, die im aktuellen Bereich verfügbar sind, erhalten Sie durch Aufrufen der [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) Methode.  
  
 Die aktuelle Position, in dem die nächste Anweisung wird aus der gelesen, kann geändert werden, durch den Aufruf der [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) Methode.  
  
 Die `DSF_OPERANDS_SYMBOLS` Flag hinzugefügt werden kann die `DSF_OPERANDS` -flag in der `dwFields` Parameter, um anzugeben, dass Symbolnamen dürfen bei der Disassemblierung Anweisungen verwendet werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)