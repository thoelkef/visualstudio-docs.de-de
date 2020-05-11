---
title: IDebugProgram2::Beenden | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 913c90e34e308ce5bb4ceecface739afc8d03f3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722749"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Beendet das Programm.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn möglich, wird das Programm beendet und aus dem Prozess entladen; Andernfalls führt das Debugmodul (DE) die erforderlichen Bereinigungen durch.

 Diese Methode oder die [Terminate-Methode](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) wird von der IDE aufgerufen, in der Regel als Reaktion auf das Anhalten des gesamten Debuggens durch den Benutzer. Die Implementierung dieser Methode sollte idealerweise das Programm innerhalb des Prozesses beenden. Ist dies nicht möglich, sollte die DE verhindern, dass das Programm in diesem Prozess mehr ausgeführt wird (und die erforderlichen Bereinigungen durchführen). Wenn `IDebugProcess2::Terminate` die Methode von der IDE aufgerufen wurde, wird der `IDebugProgram2::Terminate` gesamte Prozess irgendwann nach dem Aufruf der Methode beendet.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
