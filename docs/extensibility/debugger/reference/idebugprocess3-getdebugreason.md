---
title: IDebugProcess3::GetDebugReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetDebugReason
helpviewer_keywords:
- IDebugProcess3::GetDebugReason
ms.assetid: f23fbabc-8b18-4278-bebf-4cdc7091513c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2fa12b74b44761761a08e232a9f3efa845fa73a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723669"
---
# <a name="idebugprocess3getdebugreason"></a>IDebugProcess3::GetDebugReason
Diese Methode gibt den Grund zurück, warum der Prozess zum Debuggen gestartet wurde.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDebugReason(
   DEBUG_REASON* pReason
);
```

```csharp
int GetDebugReason(
   out enum_DEBUG_REASON pReason
);
```

## <a name="parameters"></a>Parameter
`pReason`\
[out] Gibt einen Wert [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md) aus der DEBUG_REASON-Enumeration zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md)
