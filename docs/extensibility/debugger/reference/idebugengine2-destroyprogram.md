---
title: IDebugEngine2::DestroyProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce139dd22361d9914693cbe8ad723656ab7d4f26
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731109"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Informiert ein Debugmodul (DE), dass das angegebene Programm atypisch beendet wurde und dass die DE alle Verweise auf das Programm bereinigen und ein Programm-Zerstörungsereignis senden soll.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DestroyProgram( 
   IDebugProgram2* pProgram
);
```

```cpp
int DestroyProgram( 
   IDebugProgram2 pProgram
);
```

## <a name="parameters"></a>Parameter
`pProgram`\
[in] Ein [IDebugProgram2-Objekt,](../../../extensibility/debugger/reference/idebugprogram2.md) das das Programm darstellt, das atypischerweise beendet wurde.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Nachdem diese Methode aufgerufen wurde, sendet die DE anschließend ein [IDebugProgramDestroyEvent2-Ereignis](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) zurück an den Sitzungsdebug-Manager (SDM).

 Diese Methode ist nicht `E_NOTIMPL`implementiert (gibt ) zurück, wenn die DE im gleichen Prozess wie das zu debuggende Programm ausgeführt wird. Diese Methode wird nur implementiert, wenn die DE im gleichen Prozess wie das SDM ausgeführt wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
