---
title: IDebugProgramEx2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fcb52a96074b783043af1e908cf454466df74c30
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722389"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Fügen Sie eine Sitzung an ein Programm an.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason,
   IDebugSession2*       pSession
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   uint                 dwReason,
   IDebugSession2       pSession
);
```

## <a name="parameters"></a>Parameter
`pCallback`\
[in] Ein [IDebugEventCallback2-Objekt,](../../../extensibility/debugger/reference/idebugeventcallback2.md) das die Rückruffunktion darstellt, an die das angefügte Debugmodul Ereignisse sendet.

`dwReason`\
[in] Ein Wert [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) aus der ATTACH_REASON-Enumeration, der den Grund für den Anfügevorgang beschreibt.

`pSession`\
[in] Ein Wert, der die Sitzung, die an das Programm angefügt wird, eindeutig identifiziert.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; andernfalls wird ein Fehlercode zurückgegeben. Diese Methode `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` sollte zurückgegeben werden, wenn das Programm bereits angefügt ist.

## <a name="remarks"></a>Bemerkungen
 Der Port, der das Programm `pSession` enthält, kann den Wert in verwenden, um zu bestimmen, welche Sitzung versucht, an das Programm anzuhängen. Wenn ein Port z. B. zulässt, dass jeweils nur eine Debugsitzung an einen Prozess angefügt wird, kann der Port bestimmen, ob dieselbe Sitzung bereits an andere Programme im Prozess angefügt ist.

> [!NOTE]
> Die übergebene `pSession` Schnittstelle ist nur als Cookie zu behandeln, ein Wert, der den Sitzungsdebug-Manager eindeutig identifiziert, der an dieses Programm anhängt. keine der Methoden auf der mitgelieferten Schnittstelle funktionsfähig sind.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
