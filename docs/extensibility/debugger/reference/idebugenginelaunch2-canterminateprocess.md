---
title: IDebugEngineLaunch2::CanTerminateProcess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91c68e0a0e314015c1f2e6df2a96243c6ce854e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730558"
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
Bestimmt, ob ein Prozess beendet werden kann.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanTerminateProcess ( 
   IDebugProcess2* pProcess
);
```

```csharp
int CanTerminateProcess ( 
   IDebugProcess2 pProcess
);
```

## <a name="parameters"></a>Parameter
`pProcess`\
[in] Ein [IDebugProcess2-Objekt,](../../../extensibility/debugger/reference/idebugprocess2.md) das den zu beendenden Prozess darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; andernfalls wird ein Fehlercode zurückgegeben. Gibt `S_FALSE` zurück, wenn das Modul den Prozess nicht beenden kann, z. B. weil der Zugriff verweigert wird.

## <a name="remarks"></a>Bemerkungen
 Wenn diese `S_OK`Methode zurückgibt, kann die [TerminateProcess-Methode](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) aufgerufen werden, um den Prozess tatsächlich zu beenden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)
