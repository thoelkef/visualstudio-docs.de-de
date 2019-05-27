---
title: IDebugThread2::CanSetNextStatement | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::CanSetNextStatement
helpviewer_keywords:
- IDebugThread2::CanSetNextStatement
ms.assetid: 7014af80-ff4f-4790-a34b-0528918d1fa3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa649270ae9f837f84314776bbfb6b35e77b7d36
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199750"
---
# <a name="idebugthread2cansetnextstatement"></a>IDebugThread2::CanSetNextStatement
Bestimmt, ob es sich bei der aktuellen Anweisungszeiger auf den angegebenen Stapelrahmen festgelegt werden kann.

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
Für die zukünftige Verwendung reserviert. Legen Sie auf einen null-Wert. Ist dies ein null-Wert, verwenden Sie den aktuellen Stapelrahmen aus.

`pCodeContext`\
[in] Ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt, das beschreibt, der Code-Ort ausgeführt werden und der Kontext.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Wenn diese Methode zurückgibt `S_OK`, rufen Sie dann die [nächste Anweisung festlegen](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md) Methode die nächste Anweisung festlegen.

## <a name="see-also"></a>Siehe auch
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)