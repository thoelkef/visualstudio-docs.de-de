---
title: IDebugProcessEx2::Detach | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2f016c078fcf19ec244fc4c0682d2caee81a2062
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311616"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Diese Methode informiert dem Prozess, dass eine Sitzung nicht mehr Debuggen des Prozesses ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Detach( 
   IDebugSession2* pSession
);
```

```csharp
int Detach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Parameter
`pSession`\
[in] Ein Wert, der die Sitzung, um diesen Prozess für trennen eindeutig identifiziert.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die Schnittstelle übergebenen `pSession` ist nur als Cookie behandelt werden soll, wird ein Wert, der Identifizierung der sitzungsbasierter Debug-Manager, die ursprünglich für diesen Prozess angefügt; keine der Methoden für die angegebene Schnittstelle funktionsfähig sind.

## <a name="see-also"></a>Siehe auch
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)