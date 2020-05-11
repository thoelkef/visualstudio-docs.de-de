---
title: IDebugDisassemblyStream2::Lesen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a4f5c0250405c2e2a0314b52c4cbc64d749fc0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732095"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Liest Anweisungen, die von der aktuellen Position im Demontagestrom aus beginnen.

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

## <a name="parameters"></a>Parameter
`dwInstructions`\
[in] Die Anzahl der zu zerlegenden Anweisungen. Dieser Wert ist auch die `prgDisassembly` maximale Länge des Arrays.

`dwFields`\
[in] Eine Kombination von Flags aus der DISASSEMBLY_STREAM_FIELDS-Enumeration, die angeben, welche [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) `prgDisassembly` Felder ausgefüllt werden sollen.

`pdwInstructionsRead`\
[out] Gibt die Anzahl der tatsächlich demontierten Anweisungen zurück.

`prgDisassembly`\
[out] Ein Array von [DisassemblyData-Strukturen,](../../../extensibility/debugger/reference/disassemblydata.md) das mit dem zerlegten Code gefüllt wird, eine Struktur pro zerlegter Anweisung. Die Länge dieses Arrays wird `dwInstructions` durch den Parameter bestimmt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die maximale Anzahl von Anweisungen, die im aktuellen Bereich verfügbar sind, kann durch Aufrufen der [GetSize-Methode](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) abgerufen werden.

 Die aktuelle Position, aus der die nächste Anweisung gelesen wird, kann durch Aufrufen der [Seek-Methode](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) geändert werden.

 Das `DSF_OPERANDS_SYMBOLS` Flag kann dem `DSF_OPERANDS` Flag `dwFields` im Parameter hinzugefügt werden, um anzugeben, dass Symbolnamen beim Demontage anweisungen verwendet werden sollen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
