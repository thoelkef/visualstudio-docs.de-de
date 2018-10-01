---
title: IDebugDisassemblyStream2::Read | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 117a90cbcfd96db808252b9653ee4c0015e92b0d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520832"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugDisassemblyStream2::Read](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdisassemblystream2-read).  
  
Liest die Anleitung beginnend mit der aktuellen Position im Stream Disassembly.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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

