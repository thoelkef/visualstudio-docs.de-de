---
title: IDebugProgram2::GetDisassemblyStream | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcc5032fe2fa080034cda3f63a0fb013e12c42e3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870392"
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

#### <a name="parameters"></a>Parameter
 `dwScope`

 [in] Gibt einen Wert aus der [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) Enumeration, die im Rahmen der Disassembly-Datenstrom definiert.

 `pCodeContext`

 [in] Ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt, das die Position des, wo Sie den Disassembly-Stream darstellt.

 `ppDisassemblyStream`

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