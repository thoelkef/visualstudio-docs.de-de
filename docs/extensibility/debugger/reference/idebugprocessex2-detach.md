---
title: IDebugProcessEx2::Detach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7379436ae0da57d7f8c47ce8484c810a53a0a453
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723362"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Diese Methode informiert den Prozess, dass eine Sitzung den Prozess nicht mehr debuggen.

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
[in] Ein Wert, der die Sitzung eindeutig identifiziert, von der dieser Prozess getrennt werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die übergebene `pSession` Schnittstelle ist nur als Cookie zu behandeln, ein Wert, der den Sitzungsdebug-Manager, der ursprünglich an diesen Prozess angefügt wurde, eindeutig identifiziert. keine der Methoden auf der mitgelieferten Schnittstelle funktionsfähig sind.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
