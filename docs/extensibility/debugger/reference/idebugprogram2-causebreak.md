---
title: IDebugProgram2::UrsacheBreak | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e96db32d7ba5a01f89530623c949500a265cdb60
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723096"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
Fordert an, dass das Programm die Ausführung beendet, wenn einer seiner Threads das nächste Mal ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein [IDebugBreakEvent2-Ereignis](../../../extensibility/debugger/reference/idebugbreakevent2.md) wird gesendet, wenn das Programm das nächste Programm versucht, Code auszuführen, nachdem diese Methode aufgerufen wurde.

 Diese Methode ist insofern asynchron, als die Methode sofort zurückkehrt, ohne notwendigerweise darauf zu warten, dass das Programm beendet wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
