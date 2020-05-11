---
title: IDebugProcess3::GetENCAvailableState | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77345cfc3aa1dd95482052893e7c09591ad7cd4e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723640"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
Diese Methode ruft den aktuellen Bearbeitungs- und Fortsetzungsstatus des Prozesses ab. Ein benutzerdefinierter Portlieferant sollte immer zurückgeben. `E_NOTIMPL`

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
[out] Ein Wert aus der [EncUnavailableReason-Enumeration.](../../../extensibility/debugger/reference/encunavailablereason.md)

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird Fehlercode zurückgegeben.

> [!NOTE]
> Ein benutzerdefinierter Portlieferant sollte immer zurückgeben. `E_NOTIMPL`

## <a name="remarks"></a>Bemerkungen
 Dieser Zustand kann von [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)beeinflusst werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
