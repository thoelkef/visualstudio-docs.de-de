---
title: IDebugthread2::CansetNextStatement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::CanSetNextStatement
helpviewer_keywords:
- IDebugThread2::CanSetNextStatement
ms.assetid: 7014af80-ff4f-4790-a34b-0528918d1fa3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4232c25bfe9acd7f17c88c28aa4211a9c62175f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718861"
---
# <a name="idebugthread2cansetnextstatement"></a>IDebugThread2::CanSetNextStatement
Legt fest, ob der aktuelle Anweisungszeiger auf den angegebenen Stapelrahmen festgelegt werden kann.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanSetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int CanSetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>Parameter
`pStackFrame`\
Reserviert für die zukünftige Verwendung; auf einen NULL-Wert festgelegt. Wenn es sich um einen NULL-Wert handelt, verwenden Sie den aktuellen Stapelrahmen.

`pCodeContext`\
[in] Ein [IDebugCodeContext2-Objekt,](../../../extensibility/debugger/reference/idebugcodecontext2.md) das den auszuführenden Codespeicherort und seinen Kontext beschreibt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn diese `S_OK`Methode zurückkehrt, ruft die [SetNextStatement-Methode](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md) auf, um die nächste Anweisung tatsächlich festzulegen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
