---
title: IEnumDebugObjects::Reset | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Reset
helpviewer_keywords:
- IEnumDebugObjects::Reset method
ms.assetid: 4a245e47-cc39-4177-b83d-083ea0e3190f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 786adff86b35ed4d33b07a4144544adffe53ea75
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226459"
---
# <a name="ienumdebugobjectsreset"></a>IEnumDebugObjects::Reset
Diese Methode setzt die Enumeration auf das erste Element zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="parameters"></a>Parameter
 Keiner

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Nachdem diese Methode aufgerufen wird, wird beim nächsten Aufruf von [Weiter](../../../extensibility/debugger/reference/ienumdebugobjects-next.md) gibt das erste Element der Enumeration.

## <a name="see-also"></a>Siehe auch
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
- [Nächste](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)