---
title: IDebugProgram2::Anfügen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d0b182ba7a873816e3a7aa32d39beb2c63cc5ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723138"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
Fügt an das Programm an.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback
);
```

## <a name="parameters"></a>Parameter
`pCallback`\
[in] Ein [IDebugEventCallback2-Objekt,](../../../extensibility/debugger/reference/idebugeventcallback2.md) das für die Debugereignisbenachrichtigung verwendet werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Die folgende Tabelle zeigt einige mögliche Fehlercodes.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Das angegebene Programm ist bereits an den Debugger angefügt.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Während des Anfügevorgangs ist eine Sicherheitsverletzung aufgetreten.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Ein Desktopprogramm kann nicht an den Debugger angefügt werden.|

## <a name="remarks"></a>Bemerkungen
 Ein Debugmodul (DE) ruft diese Methode nie auf, um sie an ein Programm anzuhängen. Wenn die DE im Adressraum des Programms ausgeführt wird, wird die [OnAttach-Methode](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) aufgerufen. Wenn die DE im SDM-Adressraum (SDM) des Sitzungsdebug-Managers ausgeführt wird, wird die [Attach-Methode](../../../extensibility/debugger/reference/idebugengine2-attach.md) aufgerufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
