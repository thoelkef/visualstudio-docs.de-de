---
title: IDebugProcess3::DisableENC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b39bb448501bacd5ab458b7e61bb1a5044bc8a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723734"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Diese Methode deaktiviert explizit Bearbeiten und Fortfahren für diesen Prozess (und alle darin enthaltenen Programme). Ein benutzerdefinierter Portlieferant sollte immer zurückgeben. `E_NOTIMPL`

## <a name="syntax"></a>Syntax

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>Parameter
`reason`\
[in] Ein Wert aus der [EncUnavailableReason-Enumeration.](../../../extensibility/debugger/reference/encunavailablereason.md)

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird Fehlercode zurückgegeben.

> [!NOTE]
> Ein benutzerdefinierter Portlieferant sollte immer zurückgeben. `E_NOTIMPL`

## <a name="remarks"></a>Bemerkungen
 Sobald Bearbeiten und Fortfahren für einen Prozess deaktiviert ist, kann er nur durch einen Neustart des Prozesses wieder aktiviert werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
