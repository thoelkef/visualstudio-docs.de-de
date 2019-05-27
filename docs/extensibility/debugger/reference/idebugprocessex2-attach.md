---
title: IDebugProcessEx2::Attach | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: edb130496f2896fc0678e850163cbc96ce321048
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199039"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Diese Methode informiert dem Prozess, dass eine Sitzung jetzt Debuggen des Prozesses ist.

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
[in] Ein Wert, der die Sitzung, Anfügen an diesen Prozess eindeutig identifiziert.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die Schnittstelle übergebenen `pSession` nur als ein Cookie, das einen Wert behandelt werden soll, die eindeutig den Anfügen an diesen Prozess; sitzungsbasierter Debug-Manager keine der Methoden für die angegebene Schnittstelle funktionsfähig sind.

## <a name="see-also"></a>Siehe auch
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)