---
title: IDebugProgram2::EnumCodePaths | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b99651811cedbdb8ec0eca5b766e6d75651dd5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723031"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Ruft eine Liste der Codepfade für eine bestimmte Position in einer Quelldatei ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumCodePaths( 
   LPCOLESTR            pszHint,
   IDebugCodeContext2*  pStart,
   IDebugStackFrame2*   pFrame,
   BOOL                 fSource,
   IEnumCodePaths2**    ppEnum,
   IDebugCodeContext2** ppSafety
);
```

```csharp
int EnumCodePaths( 
   string                 pszHint,
   IDebugCodeContext2     pStart,
   IDebugStackFrame2      pFrame,
   Int                    fSource,
   out IEnumCodePaths2    ppEnum,
   out IDebugCodeContext2 ppSafety
);
```

## <a name="parameters"></a>Parameter
`pszHint`\
[in] Das Wort unter dem Cursor in der **Quell-** oder **Demontageansicht** in der IDE.

`pStart`\
[in] Ein [IDebugCodeContext2-Objekt,](../../../extensibility/debugger/reference/idebugcodecontext2.md) das den aktuellen Codekontext darstellt.

`pFrame`\
[in] Ein [IDebugStackFrame2-Objekt,](../../../extensibility/debugger/reference/idebugstackframe2.md) das den Stapelrahmen darstellt, der dem aktuellen Haltepunkt zugeordnet ist.

`fSource`\
[in] Ein Wert`TRUE`ungleich Null ( ),`FALSE`wenn in der **Quellansicht** oder Null ( ) wenn in der **Disassemblierungsansicht.**

`ppEnum`\
[out] Gibt ein [IEnumCodePaths2-Objekt](../../../extensibility/debugger/reference/ienumcodepaths2.md) zurück, das eine Liste der Codepfade enthält.

`ppSafety`\
[out] Gibt ein [IDebugCodeContext2-Objekt](../../../extensibility/debugger/reference/idebugcodecontext2.md) zurück, das einen zusätzlichen Codekontext darstellt, der als Haltepunkt festgelegt werden soll, falls der gewählte Codepfad übersprungen wird. Dies kann z. B. bei einem kurzgeschlossenen booleschen Ausdruck passieren.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein Codepfad beschreibt den Namen einer Methode oder Funktion, die aufgerufen wurde, um zum aktuellen Punkt in der Ausführung des Programms zu gelangen. Eine Liste der Codepfade stellt die Aufrufliste dar.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
