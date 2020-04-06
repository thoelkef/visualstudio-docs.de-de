---
title: IDebugthread2::GetLogicalThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e148fb0b9b043fc1717effca00d698ee14beb2f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718837"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Debugmodule implementieren diese Methode nicht.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetLogicalThread( 
   IDebugStackFrame2*     pStackFrame,
   IDebugLogicalThread2** ppLogicalThread
);
```

```csharp
int GetLogicalThread( 
   IDebugStackFrame2        pStackFrame,
   out IDebugLogicalThread2 ppLogicalThread
);
```

## <a name="parameters"></a>Parameter
`pStackFrame`\
[in] Ein [IDebugStackFrame2-Objekt,](../../../extensibility/debugger/reference/idebugstackframe2.md) das den Stapelrahmen darstellt.

`ppLogicalThread`\
[out] Gibt `IDebugLogicalThread2` eine Schnittstelle zurück, die den zugeordneten logischen Thread darstellt. Eine Debugmodulimplementierung sollte diesen Wert auf null festlegen.

## <a name="return-value"></a>Rückgabewert
 Debugmodulimplementierungen geben `E_NOTIMPL`immer zurück.

## <a name="see-also"></a>Weitere Informationen
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
