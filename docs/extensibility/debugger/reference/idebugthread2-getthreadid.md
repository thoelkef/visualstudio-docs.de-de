---
title: IDebugThread2::GetThreadId | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c77e2d5de5105b964beea0ad880358b59e10fab7
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450113"
---
# <a name="idebugthread2getthreadid"></a>IDebugThread2::GetThreadId
Ruft den Systembezeichner für den Thread ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetThreadId (
    DWORD* pdwThreadId
);
```

```csharp
int GetThreadId (
    out uint pdwThreadId
);
```

#### <a name="parameters"></a>Parameter
`pdwThreadId` [out] Gibt den Systembezeichner für den Thread zurück.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
Eine Thread-ID wird verwendet, um einen Thread auf allen anderen Threads in einem Prozess zu identifizieren.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine einfache `CProgram` Objekt, das implementiert die [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) Schnittstelle.

```cpp
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {
    *pdwThreadId = GetCurrentThreadId();
    return NOERROR;
}
```

## <a name="see-also"></a>Siehe auch
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
