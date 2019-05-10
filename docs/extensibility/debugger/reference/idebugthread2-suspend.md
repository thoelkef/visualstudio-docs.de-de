---
title: IDebugThread2::Suspend | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd1987be34cf0f07ce5f37f074cd298a8135a4fa
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226397"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Hält einen Thread.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Suspend ( 
   DWORD *pdwSuspendCount
);
```

```csharp
HRESULT Suspend ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Parameter
 `pdwSuspendCount`\

 [out] Gibt den Unterbrechungszähler nach dem Vorgang "Anhalten" zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Jeder Aufruf dieser Methode inkrementiert den Unterbrechungszähler über 0. Diese Unterbrechungszähler wird angezeigt, der **Threads** Debug-Fenster.

 Bei jedem Aufruf dieser Methode, muss ein späterer Aufruf von der [fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md) Methode.

## <a name="see-also"></a>Siehe auch
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)