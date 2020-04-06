---
title: IDebugProcessEx2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d70da2530a1677367a22968436a17eba809fd24a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723382"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Diese Methode informiert den Prozess, dass eine Sitzung den Prozess jetzt debuggen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Attach( 
   IDebugSession2* pSession
);
```

```csharp
int Attach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Parameter
`pSession`\
[in] Ein Wert, der die Sitzung, die an diesen Prozess angefügt wird, eindeutig identifiziert.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die übergebene `pSession` Schnittstelle ist nur als Cookie zu behandeln, ein Wert, der den Sitzungsdebug-Manager eindeutig identifiziert, der an diesen Prozess angefügt wird. keine der Methoden auf der mitgelieferten Schnittstelle funktionsfähig sind.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
