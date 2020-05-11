---
title: IDebugProgram2::GetDisassemblyStream | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2160f963ad1f3f37291519ced30b8096e33a6116
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722867"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Ruft den Demontagestream für dieses Programm oder einen Teil dieses Programms ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDisassemblyStream( 
   DISASSEMBLY_STREAM_SCOPE   dwScope,
   IDebugCodeContext2*        pCodeContext,
   IDebugDisassemblyStream2** ppDisassemblyStream
);
```

```csharp
int GetDisassemblyStream( 
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,
   IDebugCodeContext2             pCodeContext,
   out IDebugDisassemblyStream2   ppDisassemblyStream
);
```

## <a name="parameters"></a>Parameter
`dwScope`\
[in] Gibt einen Wert [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) aus der DISASSEMBLY_STREAM_SCOPE-Enumeration an, die den Bereich des Demontagestreams definiert.

`pCodeContext`\
[in] Ein [IDebugCodeContext2-Objekt,](../../../extensibility/debugger/reference/idebugcodecontext2.md) das die Position des Starts des Demontagestreams darstellt.

`ppDisassemblyStream`\
[out] Gibt ein [IDebugDisassemblyStream2-Objekt](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) zurück, das den Demontagestream darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt `E_DISASM_NOTSUPPORTED` zurück, wenn die Demontage für diese bestimmte Architektur nicht unterstützt wird.

## <a name="remarks"></a>Bemerkungen
 Wenn `dwScopes` der Parameter `DSS_HUGE` das Flag der DISASSEMBLY_STREAM_SCOPE-Enumeration gesetzt hat, wird erwartet, dass die Demontage eine große Anzahl von Demontageanweisungen zurückgibt, z. B. für eine ganze Datei oder ein Modul. [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) Wenn `DSS_HUGE` das Flag nicht gesetzt ist, wird erwartet, dass die Demontage auf einen kleinen Bereich beschränkt ist, in der Regel auf den einer einzelnen Funktion.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
