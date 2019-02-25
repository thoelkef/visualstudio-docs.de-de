---
title: IDebugProgramEx2::Attach | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5ebf525b2c823963aa7ba099d4f3b1801d84d1e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683583"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Fügen Sie eine Sitzung mit einem Programm.

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

#### <a name="parameters"></a>Parameter
 `pCallback`

 [in] Ein [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Objekt, das die Callback-Funktion darstellt, die die angefügten Debug-Engine Ereignisse sendet.

 `dwReason`

 [in] Ein Wert aus der [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) -Enumeration, die den Grund für den Anfügevorgang beschreibt.

 `pSession`

 [in] Ein Wert, der die Sitzung eindeutig identifiziert wird, die an das Programm angefügt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls einen Fehlercode zurück. Diese Methode sollte zurückgeben `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` , wenn das Programm bereits angefügt ist.

## <a name="remarks"></a>Hinweise
 Der Port, der das Programm enthält, können den Wert in `pSession` um zu bestimmen, welche Sitzung versucht, die an die Anwendung anfügen. Wenn ein Port zum Anfügen an einen Prozess zu einem Zeitpunkt nur eine Debugsitzung zulässt, kann z. B. der Port ermitteln, ob die gleiche Sitzung bereits für andere Programme im Prozess angefügt ist.

> [!NOTE]
>  Die Schnittstelle übergebenen `pSession` nur als ein Cookie, das einen Wert behandelt werden soll, die eindeutig den Anfügen an diesem Programm; sitzungsbasierter Debug-Manager keine der Methoden für die angegebene Schnittstelle funktionsfähig sind.

## <a name="see-also"></a>Siehe auch
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)