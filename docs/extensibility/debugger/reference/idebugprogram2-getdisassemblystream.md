---
title: IDebugProgram2::GetDisassemblyStream | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71389ef210d50becaab4d25e29194c2a40000497
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66308762"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Ruft den Disassembly-Datenstrom für dieses Programm oder einen Teil dieser Anwendung ab.

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
[in] Gibt einen Wert aus der [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) Enumeration, die im Rahmen der Disassembly-Datenstrom definiert.

`pCodeContext`\
[in] Ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt, das die Position des, wo Sie den Disassembly-Stream darstellt.

`ppDisassemblyStream`\
[out] Gibt eine [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) -Objekt, das den Disassembly-Stream darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Gibt `E_DISASM_NOTSUPPORTED` Wenn Disassembly für diese bestimmte Architektur nicht unterstützt wird.

## <a name="remarks"></a>Hinweise
 Wenn die `dwScopes` Parameter hat den `DSS_HUGE` flag von der [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) -Enumeration festgelegt, und klicken Sie dann die Disassembly wird erwartet, dass eine große Anzahl von Disassembly-Anweisungen, z. B. für eine gesamte Datei zurückgegeben oder das Modul. Wenn die `DSS_HUGE` Flag nicht festgelegt, und klicken Sie dann die Disassembly wird erwartet, dass auf eine kleine Region beschränkt werden in der Regel, die einer einzelnen Funktion.

## <a name="see-also"></a>Siehe auch
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)