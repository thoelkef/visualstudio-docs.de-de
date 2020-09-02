---
title: 'IDebugEngine2:: causeelbreak | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62be3ce13ecbc3180cf2bbcce26b04f3d79edb1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731153"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Fordert an, dass alle Programme, die von dieser Debug-Engine (de) debuggt werden, die Ausführung bei der nächsten Ausführung eines Threads abbrechen.

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
 Diese Methode ist asynchron: ein [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) -Ereignis wird gesendet, wenn das Programm das nächste Mal versucht, die Ausführung auszuführen, nachdem diese Methode aufgerufen wurde.

## <a name="see-also"></a>Weitere Informationen
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
