---
title: 'IDebugProcess3:: getencavailablestate | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723640"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
Diese Methode ruft den aktuellen Zustand "Bearbeiten und Fortfahren" des Prozesses ab. Ein benutzerdefinierter Port Lieferant sollte immer zurückgeben `E_NOTIMPL` .

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
vorgenommen Ein Wert [aus der](../../../extensibility/debugger/reference/encunavailablereason.md) Enumeration "Enumeration" in "Enumeration".

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.

> [!NOTE]
> Ein benutzerdefinierter Port Lieferant sollte immer zurückgeben `E_NOTIMPL` .

## <a name="remarks"></a>Bemerkungen
 Dieser Status kann von [disableumc](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)beeinflusst werden.

## <a name="see-also"></a>Siehe auch
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
