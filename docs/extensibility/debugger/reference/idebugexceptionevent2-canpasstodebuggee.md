---
title: IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab57f599214cfbd7a1f5fcca15fa104b072d1d48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729870"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Legt fest, ob das Debugmodul (DE) die Option unterstützt, diese Ausnahme an das zu debuggende Programm zu übergeben, wenn die Ausführung fortgesetzt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Rückgabewert
 Gibt `S_OK` entweder (die Ausnahme kann an `S_FALSE` das Programm übergeben werden) oder (die Ausnahme kann nicht übergeben werden).

## <a name="remarks"></a>Bemerkungen
 Die DE muss über eine Standardaktion für die Übergabe an das Debuggee verfügen. Die IDE kann das [IDebugExceptionEvent2-Ereignis](../../../extensibility/debugger/reference/idebugexceptionevent2.md) empfangen und `CanPassToDebuggee` die [Continue-Methode](../../../extensibility/debugger/reference/idebugprocess3-continue.md) aufrufen, ohne die Methode aufzurufen. Daher sollte die DE eine Standard-Groß-/Kleinschreibung für die Weitergabe der Ausnahme haben oder nicht.

## <a name="see-also"></a>Weitere Informationen
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
