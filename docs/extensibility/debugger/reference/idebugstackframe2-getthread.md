---
title: IDebugStackFrame2::GetThread | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetThread
helpviewer_keywords:
- IDebugStackFrame2::GetThread
ms.assetid: cbeef85b-3dd7-4f97-adc2-c4d197d979fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad712371049151b18daf3b70abd5063e6421efba
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458565"
---
# <a name="idebugstackframe2getthread"></a>IDebugStackFrame2::GetThread
Ruft den Thread, der einen Stapelrahmen zugeordnet.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetThread ( 
   IDebugThread2** ppThread
);
```

```csharp
int GetThread ( 
   out IDebugThread2 ppThread
);
```

## <a name="parameters"></a>Parameter
 `ppThread`\

 [out] Gibt eine [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)