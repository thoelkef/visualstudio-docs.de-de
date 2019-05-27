---
title: IDebugProcess3::GetENCAvailableState | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc51b89061dca3c0d3026b391b8d6b0106421542
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202349"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
Diese Methode ruft den aktuellen Status des Prozesses bearbeiten und fortfahren. Ein benutzerdefinierten Port Lieferanten sollte immer zurückgeben `E_NOTIMPL`.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetENCAvailableState(
   EncUnavailableReason* pReason
);
```

```csharp
int GetENCAvailableState(
   EncUnavailableReason[] pReason
);
```

## <a name="parameters"></a>Parameter
`pReason`\
[out] Ein Wert aus der [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) Enumeration.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt den Fehlercode zurück.

> [!NOTE]
> Ein benutzerdefinierten Port Lieferanten sollte immer zurückgeben `E_NOTIMPL`.

## <a name="remarks"></a>Hinweise
 Dieser Zustand kann durch beeinflusst werden [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md).

## <a name="see-also"></a>Siehe auch
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)